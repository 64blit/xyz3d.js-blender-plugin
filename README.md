# xyz3d.js Blender Plugin

This plugin adds custom properties to the selected objects which are read by the xyz3d.js library.

https://www.youtube.com/watch?v=3mRjiqz_XWI

![overview](./docs/1-overview.png)

# how to use

## Models

Select an object and while it's the active object choose a corresponding option in the models section.

#### INTERACTABLE MESHES

If the object is "clickable" or "hoverable"

1. set it as "interactable"
2. add a bounding (convex) mesh around it that will work as bounds the user clicks
3. set viewport visibility of this bounding mesh to bounds only (optionally)
4. click the bounding mesh, then it's interactable mesh counterpart, and select "Set Raycast Mesh". (AKA selected=interactable, active=raycast mesh)

#### SCENE ZONES

This is how xyz3d groups models and compartmentalizes interactive/background components. Only buttons in the currently viewing scene zone are interactable. Each scene zone requires a Camera Anchor mesh, this is where the camera will move to when you enter the scene zone. The camera will then be moved back if the vertices of your interactable and background meshes are not in the camera's frustum. Note, a camera anchor order is mandatory - this starts at 0.

0. Enter a scene zone name at the top of the plugin, ie Home or Demo
1. Create a box for the camera anchor (recommended to set viewport visibility to bounds)
2. Move this box to where you would like the camera to be for this zone
3. Click this box and set it as a camera anchor via the apply button, also click the set scene zone button and set it's camera anchor order.
4. Select the meshes corresponding to this zone and also click "Apply" to "Set Zone"
5. Repeat for all scene zones.

#### ANIMATIONS

Looping animations will play continuously, Hover Animations play when the user hovers over the model, as Click animations fire on user clicks, and Camera animations fire on user clicks as well. Note, only interactable meshes are raycasted against, so this means click, hover, and camera animations will only fire on the interactable types.

1. Open the dope sheet, then navigate to the action editor
2. Copy the name of the animation you would like to add to your model
3. Paste this name into the animation text box found via the plugin
4. Apply this animation to any animation types as required via the Apply buttons

## gltf export settings

![gltf export settings](./docs/blender-gltf-settings.png)
