---
layout: post
title: "Sand Dunes Simulation (Houdini C++ SOP)"
date: 2026-08-06
---

# Sand Dunes Simulation (Houdini C++ SOP)

This custom Houdini C++ Surface Operator (SOP) node was built for sand dune dynamics simulation on the feature film *Dune (Part One)*.

Instead of relying on heavy Vellum grain solvers for large landscape sand movements, this custom SOP node (`sandDunes`) implements a fast, cellular-automata mass transfer algorithm directly on Houdini point geometry.

### How the Algorithm Works:
1. **Attribute Inspection:** Evaluates point height (`h`) and neighbor point arrays (`__nearpoints__`).
2. **Threshold Check:** Compares local point height delta `(h - nptH)` against a configurable threshold (`threshold`).
3. **Mass Transfer:** When the height threshold is exceeded, sand mass (`mass`) is transferred from the higher point to a randomly selected neighbor over `N` iterations.
4. **Performance:** Executes in C++ as a native Houdini C++ DSO operator, scaling efficiently across dense point fields.

### C++ Source Code

**sandDunes.h**
```cpp
#ifndef __sandDunes__
#define __sandDunes__

#include <SOP/SOP_Node.h>

class sandDunes : public SOP_Node
{
public:
	sandDunes(OP_Network *net, const char *name, OP_Operator *op);
	virtual ~sandDunes();

	static PRM_Template myTemplateList[];
	static OP_Node *myConstructor(OP_Network*, const char *, OP_Operator *);

protected:
	virtual OP_ERROR cookMySop(OP_Context &context);
private:
	int ITERATIONS(fpreal t) { return evalInt("iters", 0, t); }
	float GETMASS(fpreal t) { return evalFloat("mass", 0, t); }
	float GETTHRS(fpreal t) { return evalFloat("threshold", 0, t); }
};

#endif
```

**sandDunes.cpp**
```cpp
#include "sandDunes.h"

#include <GU/GU_Detail.h>
#include <GA/GA_Handle.h>
#include <OP/OP_AutoLockInputs.h>
#include <OP/OP_Director.h>
#include <OP/OP_Operator.h>
#include <OP/OP_OperatorTable.h>
#include <PRM/PRM_Include.h>
#include <UT/UT_DSOVersion.h>
#include <SYS/SYS_Math.h>
#include <GEO/GEO_PointTree.h>
#include <UT/UT_ValArray.h>
#include <vector>

void
newSopOperator(OP_OperatorTable *table)
{
	table->addOperator(new OP_Operator(
		"sandunes",
		"sandDunes ",
		sandDunes::myConstructor,
		sandDunes::myTemplateList,
		1,
		1,
		0));
}

static PRM_Name iterName("iters", "Iterations");
static PRM_Name massName("mass", "Mass");
static PRM_Name thrName("threshold", "Threshold");

static PRM_Default iterDefault(1);
static PRM_Default massDefault(0.05);
static PRM_Default trhDefault(0.09);

PRM_Template
sandDunes::myTemplateList[] = {
	PRM_Template(PRM_INT_J,  1, &iterName, &iterDefault, 0),
	PRM_Template(PRM_FLT_J,  1, &massName, &massDefault, 0),
	PRM_Template(PRM_FLT_J,  1, &thrName, &trhDefault, 0),
	PRM_Template(),
};

OP_Node *
sandDunes::myConstructor(OP_Network *net, const char *name, OP_Operator *op)
{
	return new sandDunes(net, name, op);
}

sandDunes::sandDunes(OP_Network *net, const char *name, OP_Operator *op)
	: SOP_Node(net, name, op)
{
}

sandDunes::~sandDunes()
{
}

OP_ERROR
sandDunes::cookMySop(OP_Context &context)
{
	fpreal now = context.getTime();

	OP_AutoLockInputs inputs(this);
	if (inputs.lock(context) >= UT_ERROR_ABORT)
		return error();

	duplicateSource(0, context);

	int iterations = ITERATIONS(now);
	float mass = GETMASS(now);
	float trhs = GETTHRS(now);

	GA_ROHandleIA _npts(gdp, GA_ATTRIB_POINT, "__nearpoints__");
	GA_RWHandleF _h(gdp, GA_ATTRIB_POINT, "h");
	if (_h.isValid() && _npts.isValid())
	{
		for (int i = 0; i < iterations; i++) 
		{
			for (GA_Iterator it(gdp->getPointRange()); !it.atEnd(); ++it)
			{
				GA_Offset offset = *it;
				float h = _h.get(offset);
				UT_Int32Array npts;
				_npts.get(offset, npts);
				int randIdx = rand() % npts.size();
				GA_Offset nptOffset = gdp->pointOffset(npts[randIdx]);
				float nptH = _h.get(nptOffset);
				if ((h - nptH) >= trhs) 
				{
					h -= mass;
					nptH += mass;
					_h.set(nptOffset, h);
					_h.set(offset, nptH);
				}
			}
		}
	}
	else
		std::cerr << " h or __nearpoints__ attribute is lost !!" << std::endl;
	return error();
}
```
