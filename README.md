##Exercise Files
Zip file under C:\Hooman\Unreal

## Unreal keys
1. Create an Architecture project
2. LMB + up/down to go foward and backward
3. LMB + left/right to rotate
4. MMB + drag to pan the scene
5. RMB + drag to rotate

## Maya keys

6. Select the floor and press "f" key to "frame scene"
7. alt + LMB click to rotate the object you framed
8. alt + MMB to pan
9. alt + RMB to truck (zoom in/out) the camera in and out (you can roll middle mouse wheel to zoom in/out)
10. Click RMB and tab on (WASDQE) to move forward/left/backward/right/up/down
11. On the ViewPort tab, click on three lines (menu) and select FPS
12. On the ViewPort tab, click on three lines (menu) and select GameView
13. On the ViewPort tab, click on three lines (menu) and select Immersive mode
14. When you open a new project, you typically get a blank "Main" level
15. Go to assets, go to "Levels", these are the levels hat we are going to use. "Level" in Unreal is same as "Scene" in Unity.
16. Open 02_02 level
17. click on select tool (arrow) or press "q", like Maya and Unity qwerty keys, "q" for select, "w" for move, "e" for rotate, "r" for scale, "t" for translate, y for tansform
18. On the Outliner, select SM_Cabin, toggle the visibilty
19. select some game object and move it under another game object to create hierarchy. Right click and select "detach"
20. Select the Level 02_02 on outliner, right click and create folder to group some static meshes
21. Go to 02_05 level, select the table, click "w" to "Select And Translate" object, click MMB and drag the center of coordinates to the edge of the table leg and now try to rotate. You see the rotation happens around the edge and not the center of the table.
22. If you select another object and go back to the table, you see the center of the axis is back to the center of the table!
23. In order to make the coordinate fixed, move the axis gizmo to the edge, right click on the table, select "pivot" and then "Set as Pivot Offset"
24. Pay attention, we are in the "Selection Mode", go to "Modeling mode", select "XForm", select "Edit Pivot", but if you do accept the edit, it actually changees the new pivot on the mesh for "every level" of the project that references it. so if you are changing the pivot only for the scene, just do the "offset".
25. Duplcate game objects: 1. Right click->Edit->Duplicate 2. select the object Ctrl+D 3. Alt + LMB + Drag

## Import Material

1. Create two subfolders: ScooterFBX_raw and ScooterFBX_skeleton
2. Import Scooter Yellow.fbx from Assets folder in the exercise files. Make sure Skeleton checkbox is not crossed.
3. Select all the meshes under ScooterFBX_raw and drage it to the level. 
4. Create a hierarchy: Make all the meshes under Scooter_Main
5. With this set up, you can move the handle bar, wheels, etc.. separately.
6. Now go over the ScooterFBX_skeleton and import the Scooter Yellow.fbx, but this time, cross check the skeleton and change the "import content type" to "Geometry Only".
7. Drag the "Scooter_Yellow" Skeletal Mesh to the level. This is just one object!

## Import File Into Level
1. Create three folders "Comp", BP (BluePrint), "Actor" under "Import" folder.
File --> Import Into Level. In FBX Scene Import Options, open the RootNode, you have access to the entire static meshes, leave everything checked on, In the hierachy Type, select "Create One Actor with Components"
2. You can do the import using hierachy type "create level actors". As you notice this one maintains the hierachy. So you have access to Scooter handle bar separrately
3. You can do the import using hierachy type "BluePrint".

## Datasmith Importer
1. Go to main menu ==> Edit ==> Plugins ==> Datasmith Impoter (make sure it's checked)
2. In addition to that, you will need a datasmith plugin in the application that you are using.
3. Go to https://www.unrealengine.com/en-US/datasmith/plugins
4. Download the one from Sketchup and if you have Sketchup (55 dollars for educators and students), you can export using datasmith.
5. Create a Datasmith folder under Import
6. click on "Quickly Add To your project" icon, DataSmith, File Import, and import the ranch house from Assets ==> Datasmith folder, Keep Geometry and Materials and uncheck the rest!
7. If your third party is supporting Datasmith, try to use Datasmith!

## USD Format
Level 03_04
1. The USD Format, known as Universal Scene Description is a new format that is intended to make data transfere a lot easier between 3D packages.
2. The reason you want to use USD format, it's because it supports more advanced materials. 
3. Now most renderers have gone to PBR (physically based rendering) materials. FBX doesn't support PBR. FBX (FilmBox) is a proprietary file format developed by Kaydara and owned by Autodesk since 2006. It is used to provide interoperability between digital content creation applications.
4. Go to main menu ==> Edit ==> Plugins ==> USD Impoter (make sure it's checked)
5. Create a USD folder under Import
6. Right Click, Import Assets, import Scooter_Blue.usd under Assets/USD folder, leave all the options as it is.
7. Go to Static Meshes folder and drag SM_Scooter_BodyMain to the level. Press "f" key (frame selection) to focus

## Chapter 4 working with Meshes

### Using Static Mesh Editor
Level 04_01
1. We have a number of different types of geometry that we can work with.
2. The most common geometry in Unreal Engine is static mesh.
3. Static mesh is a polygonal object that can be placed in memory and rendered by the graphics card.
4. When you import objects to the Unreal Engine, they come as static mesh and you can edit them using the static mesh editor.
5. Select SM_PatioChair1 from the Outliner, press f, right click, and select Edit SM_PatioChair1 (or hit control+E)
6. You can also select the static mesh in Details panel. Also StaticMeshes folder under Cabin_Scene has all the static meshes as well.
7. You can hit on the "Collision" drop down and select "add capsule collision" that will give you a collision so that if things run into this object, you can move the chair or etc.
8. We can also select UV and change the UVs in the static mesh editor.

### Optimization and LODs
Level 04_02
1. We want differing levels of detail depending upon whether that object is close to or further away from the camera.
2. You get LOD when you import static mesh.
3. FBX supports levels of detail.
4. Go to Asset --> Tree folder , right click and import from Exercise file > Assets > Tree_LOD.fbx
5. Make sure "Import Mesh LODs" checked
6. You can Uncheck the AutoCompute LOD screen Size and type in whatever value you want. for now leave it checked.
7. Drag Tree_LOD Static mesh from Asset>Tree folder in the Coentent browser to the scene.
8. When you drag the tree closer to the camera you get more detail and when you push it away, you get less detail.
9. Double click on Tree_LOD static mesh in the Content Browser.
10. Notice that LOD group is set to "None" by default.
11. Under LOD picker, select the "Custom" check box.
12. Under LOD Settings, check off the "Auto Complete LOD Distances", we can then start ti type in the distances that we want.
13. For LOD 0, we leave the screen size to 1.0.
14. For LOD 1, we change the screen size to 0.4 from 0.75
15. For LOD 2, we change the screen size to 0.1, means we use LOD 2, when it's 10 percent of the current screen size.
16. Save and Zoom out/in to see the change in the scene. Ctrl+LMB (to go left and right). Ctrl+RMB(to forward and backward)
17. Alt+RMB to zoom in an dzoom out. Alt+LMB to rotate the camera to the left and right.

### Using Nanite
Level 04_03
1. If you are working with a scene with a lot of details, you may consider Unreal Engine's Nanite.
2. A nanomachine, also called a nanite, is a mechanical or electromechanical device whose dimensions are measured in nanometers (millionths of a millimeter, or units of 10^-9 meter). Nanomachines are largely in the research-and-development phase, but some primitive devices have been tested.
3. This is internal format that Unreal Engine has to display high resolution geometry very quickly.
4. To set it up: Go to Edit > Project Settings > Type the word Nanite > Make sure that that's checked on.
5. When you import an asset, you tell Enreal Engine, that's a Nanite asset.
6. Let's go to Assets folder, we have a folder call Terrain. Go to that folder, and Right Click and Import Terrain.fbx from Assets folder
7. Make sure under Mesh > Advanced "Import Mesh LODs" are turned off, because Nanite will do all that work.
8. Turn on "Build Nanite" and then hit "Import All". It will recalculate the mesh to work with Nanite.
9. Open the Terrain static mesh and change the material tp Terrain_Material (Green one)
10. Drag the Terrain Static Mesh and add it to the scene. Use Alt+ Left click and drag to move the terrain.

### Skeletal Meshes