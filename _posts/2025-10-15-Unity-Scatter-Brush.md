---
layout: post
title: "Unity Editor Extension: Custom Scatter Brush Tool"
date: 2025-10-15
---

# Unity Editor Extension: Custom Scatter Brush Tool

Manually dragging prefabs into a Unity scene, positioning them on terrain surfaces, and adjusting rotations is tedious when dressing environments.

To speed up world building, I wrote a custom Unity `EditorWindow` tool called **Scatter Brush**. It allows users to create a palette of gameobject prefabs and paint them directly onto terrain geometry in the Scene View.

![Unity Scatter Brush Tool Demonstration]({{ '/assets/media/scattering_unity.gif' | relative_url }})

### Tool Features and Implementation Details:

* **Scene View Raycasting:** Subscribes to `SceneView.duringSceneGui` to cast rays from the mouse cursor onto scene geometry in real time.
* **Visual Feedback Handles:** Draws a cyan circle gizmo (`Handles.DrawWireDisc`) aligned to the surface normal under the cursor.
* **Prefab Palette Hotkeys:** Pressing number keys (1 to 9) instantly switches the active prefab without needing to focus back on the Inspector.
* **Normal Alignment and Randomization:** Instantiated prefabs align automatically to terrain surface normals while applying a randomized Y-axis rotation for natural variation.
* **Undo History Support:** Registers every instantiated object with `Undo.RegisterCreatedObjectUndo` so Ctrl+Z works as expected.

### C# Source Code

```csharp
using UnityEngine;
using UnityEditor;
using System.Collections.Generic;

namespace SubnauticaClone
{
    public class ScatterBrushWindow : EditorWindow
    {
        public List<GameObject> palette = new List<GameObject>();
        public GameObject terrain;

        private int selectedIndex = 0;

        string toolName = "Scatter Brush";
        float brushRadius = 5f;
        bool isPainting = false;

        private SerializedObject serializedObj;

        [MenuItem("Tools/Scatter Brush")]
        public static void ShowWindow()
        {
            GetWindow<ScatterBrushWindow>("Scatter Brush");
        }

        private void OnEnable()
        {
            SceneView.duringSceneGui += OnSceneGUI;
            serializedObj = new SerializedObject(this);
        }

        private void OnDisable()
        {
            SceneView.duringSceneGui -= OnSceneGUI;
        }

        private void OnGUI()
        {
            GUILayout.Label(toolName, EditorStyles.boldLabel);

            serializedObj.Update();
            SerializedProperty paletteProp = serializedObj.FindProperty("palette");
            SerializedProperty terrainProp = serializedObj.FindProperty("terrain");

            EditorGUILayout.PropertyField(paletteProp, new GUIContent("Brush Palette"), true);
            EditorGUILayout.PropertyField(terrainProp, new GUIContent("Terrain Parent"), true);
            serializedObj.ApplyModifiedProperties();

            GUILayout.Space(10);
            brushRadius = EditorGUILayout.Slider("Brush Radius", brushRadius, 0.5f, 10f);

            if (palette.Count > 0)
            {
                selectedIndex = Mathf.Clamp(selectedIndex, 0, palette.Count - 1);
                string currentName = palette[selectedIndex] != null ? palette[selectedIndex].name : "None";
                GUILayout.Label($"Selected [Key {selectedIndex + 1}]: {currentName}", EditorStyles.helpBox);
            }
            else
            {
                GUILayout.Label("Add items to Palette to start!", EditorStyles.label);
            }

            if (GUILayout.Button(isPainting ? "Stop Painting" : "Start Painting"))
            {
                isPainting = !isPainting;
            }
        }

        private void OnSceneGUI(SceneView sceneView)
        {
            if (!isPainting || palette.Count == 0) return;

            Event e = Event.current;

            if (e.type == EventType.KeyDown)
            {
                int numberPressed = (int)e.keyCode - (int)KeyCode.Alpha1;

                if (numberPressed >= 0 && numberPressed < palette.Count)
                {
                    selectedIndex = numberPressed;
                    e.Use();
                    sceneView.Repaint();
                }
            }

            Ray ray = HandleUtility.GUIPointToWorldRay(e.mousePosition);
            if (Physics.Raycast(ray, out RaycastHit hit))
            {
                Handles.color = Color.cyan;
                Handles.DrawWireDisc(hit.point, hit.normal, brushRadius);

                GameObject currentPrefab = palette[selectedIndex];
                if (currentPrefab != null)
                {
                    Handles.Label(hit.point + Vector3.up, $"Active: {currentPrefab.name}");
                }

                if (e.type == EventType.MouseDown && e.button == 0)
                {
                    PaintObject(hit.point, hit.normal);
                    e.Use();
                }
            }

            sceneView.Repaint();
        }

        private void PaintObject(Vector3 position, Vector3 normal)
        {
            if (selectedIndex >= palette.Count) return;
            GameObject prefabToPaint = palette[selectedIndex];
            if (prefabToPaint == null) return;

            GameObject newObj = (GameObject)PrefabUtility.InstantiatePrefab(prefabToPaint);
            newObj.transform.parent = terrain.transform;
            newObj.transform.position = position;
            newObj.transform.up = normal;
            newObj.transform.Rotate(0, Random.Range(0, 360), 0);

            Undo.RegisterCreatedObjectUndo(newObj, "Paint Object");
        }
    }
}
```
