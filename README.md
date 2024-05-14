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
Level 04_04
1. Unreal Engine Skeletal Meshes let you work with meshes that have deformations or skeleton applied. Typically, it's used for characters.
2. Let's import Assets/Character.fbx into Assets/character folder.
3. Unreal knows it's a skeletal mesh and it automatically checks its box for you. Make sure that "Import Content Type" is set to "Geometry and Skinning Weights"
4. Double click on Character skeletal mesh. Skeletal Mesh Editor is very similar to Static Mesh Editor, but it has a couple of other tabs. 
5. We have Skeleton tab and below that, we have asset details, which includes materials, levels of detail like a standard mesh. in addition to that, it has details for the skeletal mesh as well as for animation.
6. Click on "Charater_Skeleton" icon on top of the tabs, and then you see each one of these individual bones/joints on the left side. Click on "Spine" and rotate the upper body.
7. Click on "Character_PhysicsAsset" icon on top of the tabs. This is basically just capsules placed aroud the bones to give collision to that character. Because the character constantly deforms, just having a one capsule around the character for collision might not work. That's why have more capsules and that's what this physics asset does.
8. When you work with skeleton-based assets, you'll be using skeletal mesh editor!

### Modeling Tools
Level 04_05
1. In addition to the Static and Skeletal Mesh Editors, you can edit geometry using modeling tools in Unreal Engine. 
2. Go over to selection mode and pull down that menu and select modeling. The hotkey for that is Shift + 5. 
3. And as you can see, we've got a lot of different modeling tools here. Now if we want, we can change our existing geometry or we can create new geometry. 
4. So one of the nice things we have is we have the ability to create geometry here. So let's say I wanted to create stairs. So all I have to do is create them by clicking Stairs under Modeling Mode. And then we have all of these different Stairs types of ways to control those stairs: floating stairs, curved stairs, spiral stair. Let's just create a floating stair here. And then we can change the width. So these are really just parametric objects, the height of the steps, and so on. Now once you have this, you can accept it, and then those stairs show up in my outliner.
5. Now we have a number of different primitives here such as Box, Cylinder, etc..
6.  But we also have the ability to model, so we can deform objects by clicking the "Deform" icon.
7. Keep those stairs selected. Select "Warp" to warp those stairs so I can create kind of a nice curvy effect here. You change the  Bend Degrees as well other "Operation Type" such as a flair, a squish, a twist, and so on. And so every one of those will change the shape of that.  Hit "Cancel". 
8. Lattice: Another really nice one is the lattice deformer. You can change the resolution here on the left side (by default it's set to 5,5,5). But you can left-click and drag all of those vertex points. And if you've ever used these in a 3D modeling application you'd be very familiar with lattice deformations. Go ahead and hit "Cancel" on that. 
10. Go ahead and delete these stairs. And hit on  "Create" to create new shapes and create a sphere. So let's go ahead and create a sphere. Change the radius to 107. And then if we want, we'll give it more subdivisions (change it to 32).  Turn on wireframe mode (Alt+2 or click on "lit") so you can kind of see how it's creating that particular sphere.  Click "Accept". And then let's go back into a lit mode, and go to deform.
11. Keep "Deform" selected and hit on "Vertex Sculpt". So if you go into vertex sculpt, you'll see that you can do some nice sculpting here by hold the left button and dragging, and you can turn symmetry on or off. If we hit the shift key, it becomes a smooth brush, so we can actually smooth that down. And if we hit "Cancel", that goes away. Go ahead and delete the sphere. 
12. Hit on "XForm" tools to do arrays. Select the yellow table, and hit "Pattern", and that will create multiple copies of this object. So if I want 8 or 10 copies of that, change the rotation or the translation, or scale these tables as we create those copies. It's a great way to array things across your level. 

## Chapter 5 Materials
### Applying Materials
1. Materials are a great way to add color, texture, and character to your objects in Unreal Engine. 
2. Select the outdoor table from the level. And then just hit the letter "F" to frame it. Now once you have that selected, you'll see that in the details panel, we should have a materials rollout. And that will have a material in it. Now it can have multiple materials but this particular object just has one. 
3. Now materials actually live in the content browser, in this case, for this scene, they live in under Assets, Cabin_Scene, materials. And you'll see we have a lot of different materials here. Or we can go over "Details" panel" and hit the pulldown in front of Material > Element 0. So you'll see we have patio table material and that's the one that's applied to this object. But if you scroll down, you'll see we have a couple of other materials in there that we can use. So I have Patio Table B and C. So if I were to click on one of those, it will change that color of the patio table. Now these also live in my content browser as well, so I have these in my Cabin_Scene materials folder, and you'll see if we go all the way down here, I have Patio Table B and C. So I can also left-click and drag to apply a material. So if I wanted to put it back to normal, I could just go ahead and click and drag and notice how it changes. 
4. Objects can have more than one material applied. So a good example of that is the house itself. So if I click on this "SM_Cabin" object, you'll see that under materials, we actually have 10 different materials applied. So I can again just change these simply by selecting them here. So I have WoodSiding_Mat in element 10. And that's basically the side of that building. And if I were to click on this, I can basically insert whatever one I want. Now you can scroll through all of these. Or another way to do it is to simply do a search. So I'm going to type the word redwood and you'll see we have a RedwoodSiding_Mat. So I'm going to click on that and notice how that changes. 
5. Now if I want, I can also click and drag. So let's say I wanted to change the roofing maybe. So I have a MetalSiding_Mat. I could left-click and drag that onto that building if I wanted to. It's not really what I want, so I'm going to hit "Undo". But I could also drag that metal siding to the side of the building and it would apply. And what this does is it replaces the entire material that is in that slot. So element 10 here, which was the WoodSiding, also incorporates the side of that building. So if I were to change that back to, say, the WoodSiding_Mat that was originally on it, you'll see that it changes both on this side and this side. So when you click and drag, it's going to understand what material is in this particular element and then swap it out for the entire model. 
6. So applying materials to objects is really very straightforward in Unreal Engine. And you can use either materials that come with your project or you can create your own or you can download materials from the Unreal Store.