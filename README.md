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
Level 05_01
1. Materials are a great way to add color, texture, and character to your objects in Unreal Engine. 
2. Select the outdoor table from the level. And then just hit the letter "F" to frame it. Now once you have that selected, you'll see that in the details panel, we should have a materials rollout. And that will have a material in it. Now it can have multiple materials but this particular object just has one. 
3. Now materials actually live in the content browser, in this case, for this scene, they live in under Assets, Cabin_Scene, materials. And you'll see we have a lot of different materials here. Or we can go over "Details" panel" and hit the pulldown in front of Material > Element 0. So you'll see we have patio table material and that's the one that's applied to this object. But if you scroll down, you'll see we have a couple of other materials in there that we can use. So I have Patio Table B and C. So if I were to click on one of those, it will change that color of the patio table. Now these also live in my content browser as well, so I have these in my Cabin_Scene materials folder, and you'll see if we go all the way down here, I have Patio Table B and C. So I can also left-click and drag to apply a material. So if I wanted to put it back to normal, I could just go ahead and click and drag and notice how it changes. 
4. Objects can have more than one material applied. So a good example of that is the house itself. So if I click on this "SM_Cabin" object, you'll see that under materials, we actually have 10 different materials applied. So I can again just change these simply by selecting them here. So I have WoodSiding_Mat in element 10. And that's basically the side of that building. And if I were to click on this, I can basically insert whatever one I want. Now you can scroll through all of these. Or another way to do it is to simply do a search. So I'm going to type the word redwood and you'll see we have a RedwoodSiding_Mat. So I'm going to click on that and notice how that changes. 
5. Now if I want, I can also click and drag. So let's say I wanted to change the roofing maybe. So I have a MetalSiding_Mat. I could left-click and drag that onto that building if I wanted to. It's not really what I want, so I'm going to hit "Undo". But I could also drag that metal siding to the side of the building and it would apply. And what this does is it replaces the entire material that is in that slot. So element 10 here, which was the WoodSiding, also incorporates the side of that building. So if I were to change that back to, say, the WoodSiding_Mat that was originally on it, you'll see that it changes both on this side and this side. So when you click and drag, it's going to understand what material is in this particular element and then swap it out for the entire model. 
6. So applying materials to objects is really very straightforward in Unreal Engine. And you can use either materials that come with your project or you can create your own or you can download materials from the Unreal Store.

### Editing materials and instances
Level 05_02
1. Now let's take a brief look at some ways to edit materials in Unreal Engine. So in this project, I have a bunch of different materials. But let's go into Assets, Cabin_Scene. And if we double-click on the materials folder, you'll see we have a lot of these. Now if I expand this, you'll see that a couple of these are named material instance and some are named material. Now these are slightly different. A material is basically an original source. So it basically has all the things that you need to really create the material. A material instance points to another material and just adds changes. And that's a really quick way to create different types of materials. So for example, this patio table material that we looked at before is an instance. And if I double-click on this, you'll see this window here. And this allows me to edit that particular instance. So we can change things such as the metallicness of this. If you want to make it a little bit more metal or if you want to make it maybe less rough, you can see how that's actually changing in that viewport. In fact, let's go ahead and frame that here so we can see it. So if I bring down the roughness, it gets shinier, and so on. And if I want to, I can actually add in textures that change this particular instance, or I can change the base color. And this is a really simple way to work. So if I wanted to, you know, change that to a different color, I could certainly do that. Now, once you're done with this, you can either hit "Save" here or do a Save As and give it another name. So if I do a Save As, I can call a patio table. Let's say Metal.Mat and hit "Save". And now it creates that asset here. So if I wanted to, I could left-click and drag one of the other ones over and change it. 

2. Another way to edit materials is to edit the original material. So if you have something that says material and I double-click on it, you're going to get a slightly different interface. So let me expand this. Now what you're going to get is you're going to get a Node Editor, what's called the material graph here. And that basically shows me all the textures in a graph-like format. And then here on the left side, you can change a lot of the attributes about that particular material. So if you want to change things such as shadows, things like translucency to make it more of a glassy material and so on. And so there's a lot of technical things that you can change on this, and this really allows you to author in the material exactly the way that you want. So if you want to edit a material and double-click on it, just beware that you're going to get one of two different interfaces depending upon whether the material is an instance or a basic material.

### Creating materials
Level 05_03
1. let's create a material from scratch. I'm going to create a material that goes on this plane, and we're going to just do a simple tile floor. 
2. So if I go into my assets folder, you'll notice we have a textures folder. And in there, you should find a couple of textures that we will be using for this tile floor. So for example, a base color. So it's going to be kind of this black and white checkered floor. 
3. Now if we go into our materials folder here under assets, you may or may not have some materials in here, but I'm just going to right-click and create a new one. We're going to call that material TileFloor_Mat. And then if I want, I can left-click and drag that to my floor. And obviously not much is going on there because I don't have it configured yet. 
4. So let's go ahead and double-click on this. And because it's a brand new material and not an instance, it will bring you into the material editor with the material graph. 
5. So the first thing you'll notice there is a window there. And this allows you to zoom in and out. I'm rolling my middle mouse button here. Or you can right-click and drag to truck in and out and then left-click orbits.
6. We can also change what we're viewing here. So right now I'm on sphere. At the bottom right of the window, We can change it to a plane. And right now I've got just a single-sided material. So you can see I'm not seeing that plane completely. Or we can do a cube. 
7. On the details tab, we can change basic things about this particular material. So if we wanted to, we could change the blend mode, make it a translucent material which would make it slightly transparent. We're going to keep it at opaque. We can also turn on two-sided (no back face culling). So when I go back to that preview mesh of a plane, you can see how I can see now both sides. 
8. But more importantly, you want to be able to work in this material graph. We can navigate this graph simply by right-clicking and dragging. We can roll our middle mouse button to zoom. And then if we left-click, that will go ahead and connect things. 
9. So I'm going to take some of those textures and we're going to connect those into this graph. Now this TileFloor_Mat node has all of the input slots for the texture we'd normally use for a PBR or Physically-Based Rendering. And so we'll have things such as base color, metallic, specular, and so on. So I'm going to go back to assets, find textures, and then let's start clicking and dragging these in. We're going to start with the base color. So let's go ahead and drag the base color texture inside the material window. And you'll notice that this node has a number of outputs. We can output the RGB value or single red, green, and blue, as well as alpha. And then there's also inputs here for UV mapping if we want to change that. But we just want to use the basics. 
10. So I'm going to click on "RGB", left-click and drag, notice how it drags out that line. And I'm going to hover over base color. Let go. And now I've got my tile floor. Now if I set the preview mesh to cube you can kind of see it a little bit better. I can get that reflections a little bit better. 
11. Now another thing we can add in is a normal map. So I'm going to go black and white tile normal, drag that in. And connect that into the normal map. So RGB out of that into normal map. And watch what happens. I'm getting a normal map, so I'm getting a little bit more relief on that. 
12. And then we could add in, say for example, roughness. Left-click and drag to the roughness channel. So this is all very straightforward. And then I have another one for ambient occlusion. So again I can left-click and drag from RGB to ambient occlusion. And now I have all of these basically plugged in. Now I have another one here for tile height, but I'm not going to be using that in this particular material. So now once we have this material, you can see it's showing up fairly well. And so once I hit "Save", it will save that out to my content browser. 
13. So I can either do a File, Save, or Save As. So let's go ahead and just do a save. And once I do that, you'll see it comes up in my viewport. So that's essentially the basics of how to use the Material Editor in Unreal Engine. And we can go a lot further with this by adding more nodes and even customizing it further.

### Editing material nodes
Level 05_04
1. Now let's go a little bit deeper into nodes in the Material Editor. Now I have my material here and I've saved it out as 05_04_TileFloor. So let's double-click on this. And this was the material we were working with last. And so as you can see, we've got a bunch of texture maps brought into this particular material. 
2. If we want, we can actually add in additional values that aren't based on a texture map. So let's say we wanted to work with, say, metallic and specular, and we wanted to control those. 
3. The easiest way to do that is to bring in what's called a constant and then use that to control these values. So all I have to do is right-click anywhere in "node" window, and it brings up a menu. Now we can either search this menu or we can just go down to this constants. Now there are a number of constants. And it's really just how many vectors we have. So if it's a single value, you'd use a constant, if it's a color, you'd use something like a Constant3Vector. Now let's just use a single value. So if I click on constant, it just brings up this value. And you can see it here in the details panel. When this is highlighted, that's the value. 
4. So let's control metallic. So I'm going to go ahead, left-click and drag and plug the constant "value" into the "metallic" of our material. 
5. Now, if I bring this constant value up to 1, you can see it gets very, very metallic very quickly. And so this is an easy way to control that value. So let's bring it down. And let's maybe just bring it just maybe about 0.1 or 0.2, something in that range. And that way it just gives a nice little sheen. 
6. We can do the same thing for specularity. Now I could right-click and bring in another constant, but we can also copy and paste nodes. So all I have to do is highlight this constant node, Ctrl + C, Ctrl + V, copy-paste. Plug this into specular. And so now I have a new one, and I can give it whatever value I want. So if I bring it up to 1, it's going to be way more shiny. If I bring it down to 0, it's going to be less so. So let's go ahead and bring this maybe to 0.5 or something like that. 
Note: From a visual point of view, a metallic surface colors the reflection with its color: all reflections in a blue metallic surface will be tinted blue. In contrast, a specular surface will have color-neutral reflections regardless of the base color. In other words, reflections on a specular object are added to the base color, while reflections on a metallic object are multiplied by it. This is an oversimplification, but helpful for visualization of the differences.  In the case of a metallic material, the Albedo color controls the color of the specular reflection and most light reflects as specular reflections. Non-metallic materials have specular reflections that are the same color as the incoming light and barely reflect when looking at the surface face-on.
7. Now we can also work with color. So that would be what's called a three-vector constant. So let's go ahead and add in some color to this black and white tile texture. So if I right-click in the node window and I go into constants, in this case, I'm going to do Constant3Vector. And what that does is it basically brings in a color. So if I click here on this little black swatch (the left little black window inside the Constant node), I can make it whatever color I want. So let's make it a nice blue. 
8. But what I have to do is I have to link that into base color. So if I were to just click and drag this to base color, you'll see, well, it just totally replaces the color. I still want some of that tile. So we're going to have to mix this.  
9. We're going to add in what's called a linear interpolation. So I'm going to right-click, type in the word linear, and we're going to find linear interpolate. Now that's also known as a lerp. So if you zoom in here, you'll see this lerp has two inputs and one output, and then an alpha which blends those two inputs. So I'm going to take this output, plug it into base color that disconnects the old ones. And then I'm going to take the texture node, plug it into A, take the color node, plug it into B. And already we're getting an effect. Now this lerp, if I highlight this, you'll see here in the details panel, I have A and B and then the blend between them. So if it's at 0, it's all A which means it's all this black and white texture. If it's 1, it's all B, and that's all that color. So anything in between is going to be what we want. So I'm going to put this at about 0.25. And there we go. So now I can control the color using this lerp. Now this is just the basics of how to use the material graph and how to edit and add in nodes. But as you can see, it can get very powerful very quickly. There's a lot of things you can do with this, and it's a really great way to create and edit materials.

### Transparency effects
Level 05_05
1. Let's go a little bit deeper into materials and show you how to create materials that are translucent or glassy. So let's create a glass material that we're going to place on this sphere. I'm going to be in my Assets Materials folder and go right-click and create a new material. And let's just call this Glassy_Mat. Now I'm going to double-click on this. And as you can see, we've got a number of values here in our base material.  
2. But if you look at the Node window, the opacity is grayed out as well as refraction. So we need to make sure that we turn those on before we create this material. Because this material will be transparent and it will have some refraction. So we can do that in the details panel. So I'm going to scroll down a little bit in details till we see Material Domain, Blend Mode, and Shading Model. So we want to make sure the material domain is a surface. The blend mode is translucent. And the shading model is default lid. 
3. If you notice, as soon as we turned on translucent, The opacity is neabled in the node window, but we still can't do things such as metallic or specular.  So I'm going to scroll down on the details tab and look for lighting mode under translucency. So I want to make sure that that's set to "Surface TranslucencyVolume". Now watch what happens to our material. We get metallic specular roughness and so on. 
4. We still don't have refraction. So we also have to turn that on. So I'm just going to type refract into that search panel under Details tab. And you'll see we have refraction method. Now there is a whole rollout for refraction. But we want to make sure our refraction method is "Index Of Refraction". So that way we just type in the physical refractive index and it should work. 
5. So now that we have the material node set up, we can start to populate it. So the first thing I want to do is let's just add a base color. So what color will our glass be tinted? Well, we can certainly create a Constant3Vector, which is basically a color. And so let's give that kind of a nice maybe a light blue or something like that. And then I'm going to plug that in to base color. 
6. For metallic specular roughness, those are all single values. So I'm going to create a single constant. And then I'm just going to copy and paste it a few times. So let's create four constants on the node window. 
7. And so the first one, we're going to plug into metallic. And so we want that metallic value to be pretty high: 0.8. 
8. Specularity, I think we want this to be fairly specular. So let's make that 0.9. 
9. Roughness, we don't want this roughness at all. It's going to be a smooth glass. So we're going to plug in the value of 0. 
10. And then finally, the last one is opacity. So let's plug in opacity. And notice how all of a sudden we get that opacity. So I'm going to make this about, say, 0.25. And that will allow me to see this. 
11. Now, we're still not getting the reflectiveness. So if I were to save this material without refraction, you'll see that if I take this material and apply it to my sphere, I'll get something that's okay, but if you notice that thing in the center, that's really not how we want to refract. 
12. So let's go back into this. And we need to be a little more sophisticated with how we create refraction. So the first thing I'm going to do is I'm going to create a lerp or a linear interpolate in the node window. So plug that into refraction. 
13. And then I'm going to create what's called a Fresnel on the node window, F-R-E-S-N-E-L And I'm going to plug that into the alpha of our Lerp. What a Fresnel does, is it basically computes the curvature of the surface. So as the surface curves away, it's going to balance that linear interpolation between A and B. 
14. For the A value of Lerp, I want the value for where you're looking directly through the surface. I'm going to add a constant, I'm going to make that constant 1. So that's basically no refraction at all. And then we're going to add in one more constant for our actual refractive index. And for that, I'm going to type in 1.5, which is approximately that of glass. As you can see, we're starting to get that effect. So the Fresnel controls the mix of these two. And when it gets close to the edge, we start to get more refraction. So let's go ahead and click "Save". Close this out. 
15. And there we go. Very nice. So as you can see, it's a little more complicated. To get that translucent effect, you do need to make sure that you turn on translucency, create your opacity the way that you want, and also work with your index of refraction. But as you can see, there's a lot you can do with materials in Unreal Engine. And so this is a great little glass that you can use in all sorts of applications.

### Control parameters and instances
Level 05_06
1. Creating materials with nodes is very powerful, but it can be intimidating to the average user and it also can get messy. So if I were to say take this class material and I wanted to change something, well, I got to find out which node is the one I want to use and change it. And you can make it a lot easier by creating what's called a material instance, and just exposing the parameters that you normally change. It'll make it a lot easier to manipulate those particular values. 
2. So let's double-click on 05_06_Glassy_Mat under Assets > Materials. And what we're going to do is we're going to change some of these nodes into parameters. So all I have to do is right-click on the Constant3Vector that we used for base color, and select convert to parameter. So let's call this, BaseColor. 
3. When I go to Parameter tab, I now have a base color value. 
4. Well, what about metallic? Well, we can convert that to a parameter. Let's call it metallic. So now I've got a metallic parameter here. What about roughness? I can right-click "Convert to Parameter". Roughness. And next, we can change opacity to a parameter. Convert to parameter, opacity. And then finally, what about the index of refraction? Now that's the one being plugged in to B on the lerp. So right now it's at 1.5. But if we convert it to parameter we can change it to whatever we want. So let's call this Index of Refraction. So now my parameters, I have all of these different parameters that I can work with. So now all I have to do is save out this material. 5. I'm going to create what's called an instance of Material. So if I right-click over 05_06_Glassy_Mat, select create material instance. Let's call this Glassy_Instance. Now when I drop this instance on the sphere object, well, nothing's going to change. 
6. But if I double-click on Material Instance, notice how I get a much simpler way to edit these materials. 
7. So I can turn on, for example, base color.  And maybe we want this to be a little bit more red. And you can see I have a very interactive way of manipulating this material. So, opacity, I can turn it up or down, interactively. I don't have to recompile the shader, I don't have to navigate a bunch of nodes. It makes it very easy. Index of refraction, I can dial it back, dial it up. So it's a really, really easy way to make materials that are easy to edit. So a lot of times when you see material instance, they've added in these parameters. Now you can also go into the instance, and as we've seen before, we can go down and manipulate a lot of other values as well. So if you have a material that you want to adjust a lot, it makes sense to expose those parameters that you normally use and turn it into a material instance.

## 6. Enhacing the Scene
### Creating landscapes
Level 06_01
1. If you want to create larger worlds in Unreal Engine, you may want to consider landscape. Landscape allows you to create large amounts of terrain and sculpt that terrain using interactive tools, and it's a great way to create very large worlds. 
2. Go to selection mode and select landscape. Unreal Engine assumes that we're going to create a landscape. And it kind of gives you a little bit of a green proxy that tells you what the landscape will look like. Under "New Landscape", search for landscape material. It's called Landscape_Mat. Basically it's just green grass. And then under "Location", if we want, we can change the location for the terrain. I can also interactively move that proxy to wherever I want. 
3. And then we also have the "Section Size" of the terrain. I'm going to keep this pretty small to 15 by 15 quads. Notice how that terrain got a lot smaller. 
4. And then number of components, let's just do 8 by 8. 
5. And let's go ahead and hit "Create". What that does is it applies that material and creates the terrain, and it puts us into a sculpt mode. 
6. So you notice here we have managed mode and we have sculpt mode. Now in sculpt mode, we have a bunch of different tools that allow us to sculpt our terrain so we can make our brush size bigger or smaller. I'm going to start with a pretty big brush size (change the "Brush Size" to 1100). 
7. How strong is your brush? I'm going to set the "Tool Strength" about 0.36 or so. 
8. And then we can left-click and drag and start painting the terrain that we want. Now I can certainly zoom in, use my navigation tools to paint however I want and create some hills or maybe even some mountains. 
9. Right now we're pulling the terrain up, but we can click on "Erase" tto erase terrain. So if you don't want that, we can also click on "Smooth" and smooth terrain. So if you want a little bit more rolling hills, you can certainly do that. We have flatten. We also have some nice erosion, hydro, which basically is for things like creek beds or riverbeds, gives erosion due to water. We can add noise to give a little bit more bump to it, and so on. So all of this just allows us to sculpt the terrain exactly the way that we want. 
10. Now all of this is stored in what's called a heightmap. Now this is basically just a grayscale bitmap that is the height of that terrain. Now you can import your own heightmaps if you want, and if you have something that you've painted in another application, you might be able to use it here. 
11. Now, once you're done with your terrain, you can just go straight back into selection mode. And so now that terrain is in my outliner. Looks like just any other object in the Outliner. although it is a landscape, so it's a slightly different piece of geometry. 
12. Click on the Lanscape object in the outliner to get the details tab. Now if we want, we can go down and affect the details of this. So if I wanted to, say, change the material, I could certainly do that here. If I didn't want grass, I wanted dirt or something, I could certainly change that. And then we can also turn on things such as Nanite. And so if you have really large terrain, you might want to turn on Nanite just to make sure that your levels are as fast as they can be. So those are some of the absolute basics of creating terrain. And you can certainly spend a lot of time painting and tweaking and fine-tuning your terrain. And I actually find it quite fun to build, so you might want to spend some time just creating some terrain that you might use in your projects.

### Adding foliage
Level 06_02
1. Another way to enhance your scene is to add foliage. Now this could be trees, grass, rocks, really any geometry that you want. You can actually paint it over a surface, typically a landscape. 
2. So let's go into our assets folder. And under foliage, you'll see we have a couple of trees. So I have some pine trees here named tree A, B, and C. And then I have a couple of oak trees. And so we're going to paint these on our surface. 
3. And let's change the selection mode to foliage mode. And you'll notice we've got some brush options for painting. And we have a place to drop our foliage (+ Drop Foliage Here). 
4. So basically all you need to do is drop the geometry that you want. And so I'm going to select tree B and just drop it in there. And when I highlight the Tree_B (where I dropped it), you get some options. So if I were to just paint right now (left click and brush), you'll notice that, well, I'm getting a little bit of a problem here and that these trees are kind of following that landscape (they are not vertical!) and I really don't want them to do that. So I'm going to undo that (Ctrl+Z to remove the trees) and I'm going to scroll down. And then there's this "Placement" rollout here, and under there is aligned to normal. So I'm going to go ahead and turn that off. 
5. And then we have a lot of other things that we can change. Under Painting rollout, you have density, let's make the density say 40%. 
6. We can also change the scaling. Under Painting rollout, Scale X, I can scale the tree up or down to make a little bit more variety in. So let's go maybe from .6 to one. 
7. And now when I start to paint, they're not aligning to normal. So the trees are vertical and I'm able to paint them in my scene. 
8. Now, if I want to paint a different tree, all I have to do is go  to my foliage and grab another tree. I'm going to grab one of these oak trees, drop it under +Floiage on the laft panel. 
9. If you highlight the trees under +Foliage, notice that , both trees are checked. So if I were to just click right now, it's going to paint both pine trees and oak trees, and I don't want that. So I want to make sure that one is checked off and another one's checked on. And I'm going to highlight the oak tree. And let's bring the density down to maybe say about 20%. Let's go ahead and give some scale variation to this, maybe .6 to 1.2 or something like that. And then we also want to make sure a line to normal is turned off. And then I'm can also change the size of my brush and my paint density. 
10. And there we go. There's some nice oak trees. So as you can see, it's fairly straightforward. Our painting meshes. 
11. Change the Foliage mode back into selection mode, Under Outliner there is an InstanceFoliageActor0. And so that's where all of my trees live in the outliner. So as you can see, it's a really easy way to populate your scene with trees, grass, rocks, and so on.

### Quixel assets
Level 06_03
1. Unreal Engine's Quixel assets are a great way to add new elements to your existing projects. Now there's two ways to get into Quixel. You can click on "+" (quickly add to your project icon) and go into Quixel Bridge and that will bring up this window. I'm going to close that and then we can also Add Quixel Content from the content browser. And again, it brings you into that same window. 
2. Now you will need to log in when you first use this. And you can use your Unreal ID to do that. 
3. Quixel  has a lot of different assets and all of these are free to use. And so it has a whole bunch of different things. So if we click on "Old Workshop", you can see we have a lot of tools and benches, and things like that. 
4. We can go to our home here and that will give us the featured things. We can go to 3D Assets and Search by Type. And go into, say, interior. 
5. We also have collections. So from the environment, we have different types of industrial, we have natural environments. So Canyons of Utah, lots of rocks, and materials as well. Now this also includes the materials. So if you just need some materials, you can do that.  
6. So I'm going to go to "home" here, and under 3D Assets, interior, I'm going to click on furniture, and then just pick a piece of furniture that I like. Now my current scene is a pretty modern scene. So I'm going to go ahead and select this wooden table here and then select the quality and hit "Download". And this may take a little while depending on your Internet speed. And once it's downloaded, you can click "Add". Now this will add it to your project. 
7. Now, if I close this window, you'll find it under Megascans 3D Assets. And then we have wooden table. All I have to do is left-click and drag. 
8. Now you can also go into Quixel Content. You can search under collections. There's all sorts of entire buildings. And so if you want to create a city, you can do that. 
9. Another great way is to create natural environments. So if we go into say, under 3D Assets from the home menu, under nature, we can go maybe into rocks. And if we wanted to add in a rock into our scene, we could do that. So let's go ahead and add Mossy Forest Boulder, download that. And add that to our scene. And now I should have mossy forest Boulder. Go ahead and drag that in. And now I have a boulder in my front yard. 

### Features and content packs
Level 06_04
1. In addition to the Quixel assets, you can also add in both features and what are called content backs into your Unreal scenes. Now, features are basically just built-in, so if I were to right-click over my content browser, I can select "add feature or content pack". 
2. Now features are basically things such as blueprint, so I can add in some different types of players if I want. We also have C++-type content, and then we also have what's called content. So by default, you get what's called the Starter Content Pack, which has a lot of materials and geometry that you can drag into your scene to help get you started. 
3. But if you want, you can also go to the Unreal Marketplace https://www.unrealengine.com/marketplace/en-US/store, and that will allow you to download all sorts of content packs. So I'm looking at the free content. We also have online learning content, and if you want, you can also go into different types of industries. So if you want architecture-based content, you can certainly do that. Some of this is paid content, some of it is free. 
4. And you can download. And then if you want to bring it into your current project, it will show up here, and then you can just highlight it and click "Add to Project". 

## 7. Lighting and Rendering
### Environmental lighting
Level 07_01
1. Now let's take a look at lighting in Unreal Engine. Now, there are many different types of lights that you can use, and we're going to cover most of them. But the most simple form of lighting is what's called sun and sky.  So if I go into my outliner, you'll see we actually have this sun and sky icon and we can turn that on or off, and that provides the light. 
2. But we also have a couple of other things that are contributing to the lighting in this scene. And if we turn off the sun and sky, you'll see that, well, we have clouds, so we can turn off these volumetric clouds. I'm just hitting this little eyeball here. And then we also have what's called exponential fog. And that's kind of the haze on the horizon. So we can turn that off. So all of this light is now created using sun and sky. 
3. So let's go ahead and just start from scratch and create a new sun and sky and show you how it works. So I'm going to go ahead and select SunAndSky and hit "Delete". And so now I have no light in the scene. 
4. We can click on + to add to project. Under lights, we want to find sun and sky.  So we've basically just brought back what we deleted. But now you know exactly where it is located. 
5. Now let's look at "details" for SunSky. Now in this plugin, you do have your transform. You have your location, rotation, and scale. But that doesn't really matter too much. But one thing that does matter is this little icon that we get along with sun and sky. And if you look at the icon you can tell that it's telling you which way it thinks north is (you might have to do see it from up). 
6. Notice that right now the camera is facing south and north is behind us. So if we want to, we can change that. In fact, we can change a lot of different values here. 
7. So let's go through to location rollout. So what's our location. Well, we have latitude. So where along the earth are we? As well as longitude. So that's how far away from the equator you are. Time zone. So are we at zero? It's going to be Greenwich Mean Time, and then we can go before and after that. 
8. And then we also have what's called north offset. So in this case I can basically rotate the compass. So if I rotated it, maybe -90, north would be in the direction that we're looking. And so again, you can orient this. And if you have a specific piece of real estate or land that you want to duplicate, you can do that by using your north offset as well as your latitude and longitude. 
9. And then we also have month and day to control that. And if we want, we can also add in things such as daylight savings time. 
10. And then finally, we have solar time. What time is it during the day? And that will cause the sun to move across the sky, depending upon where we are on the planet. So all you have to do is just set these to get them exactly the way that you want. And you're good to go. So this is a very easy way to light a scene. 
11. Now, in addition to this, this scene came with some standard things that you'd normally have in a default Unreal Engine scene that has a light, and one of them is called the VolumetricCloud, and then the other one is called ExponentialHeightFog. 
12. Now VolumetricClouds basically allow you to control the clouds. So if we go into that VolumetricCloud details you see we can add the bottom altitude. So how low are the clouds? How high is the cloud layer? And then things such as ray tracing as well, and we can change the planet radius. Typically, we leave that at the default if we're working with Earth. And then we can also change things such as the material and stuff like that. So that's just another way to simulate reality in your scenes. So hopefully, this will help you to create realistic skies very, very easily.

### HDRI lighting and environments
Level 07_02
1. The sun and sky plugin is great for basic lighting, but if you want more control or you want more rich lighting, you may want to use an image-based lighting. And we can do that in Unreal Engine using the HDRI Backdrop. 
2. Now I've deleted all the lights out of this scene, so let's go ahead and turn it from "Lit to Unlit", and we can see that we have our basic cabin that we were using. 
3. So I'm going to create an HDRI Backdrop. Now before I do this, I want to make sure I have an HDRI Image that I want to use. 
4. Now I have a couple that I loaded up in Photoshop here. So as you can see, they're basically environments with a light source. They're also 32-bit files. So they're HDR files. And that means that they have a really wide dynamic range. Now you can find these files in a lot of different places. There's one called HDRI Poly Haven that has a lot of them that are free to use, and you can certainly find them on the Internet https://polyhaven.com/hdris. 
5. Now, in order to do this in Unreal Engine, all we have to do is to hit on "+", add lights, HDRI Backdrop, and that brings in the backdrop and there we go. And then what we can do is we can move the blue "Z" axis down. So this is basically just an object. We can move this so that it fits our scene. So I'm going to move it down so that the grass is just visible. 
6. But we're still in unlit mode, so let's use this to light the scene. So I'm going to go ahead and click on "Lit". 
7. And we have our first problem. Now the one thing about this particular plugin is that it needs to be a specific size. So if we select HDRIBackdrop, go to the details panel and scroll down. You'll see that it already has a cube map that it brings in by default. And that's what we're seeing. But the one thing we need to look at is size. So it comes in a little small. So by default, it comes in at 150. Now this may change but we need to make sure that this is above 1500. So let's type in 1500. Hit "Enter". And there's our light. 
8. Okay. So now we have the light that we want. And again as you remember, we can move this up or down but we can also rotate it. So I'm going to go ahead and rotate this. And you can see that the light changes as well as the background. So as I rotate this, I have a different backdrop and different lighting. 
9. Now if I want to, I can change this as well. So let's go into assets, I have a cube maps folder. And if we want those two that we saw before, Sunrise_Field, double-click on that. That's one of the ones we're using. And Sunset_Coast. Again, that's another one. So let's go ahead and select Sunset_Coast and drag it over that cube map. And now it changes. 
10. And again, I can rotate this to get the lighting that I want. And you can see that this has a very strong rear light, or I can have it become a front light. 
11. Now, one of the things you're probably seeing is that this is a little bit distorted here. So we can scroll down and there is a checkbox  called Used Camera Projection. Now what this does is it just changes the way it maps this image to the sphere that we're rotating. So if I turn this on, you can see it kind of flattens it out.
12. Now we can see what happens here if I select this ground grass (SM_GROUND_GLASS) and hide it, you'll see that I can actually select that HDRIBackdrop and move it up. So that's actually my grass. But if we use camera projection off, then you'll see we're getting a little bit of a different effect. So it just depends on the image that you're using as to whether or not you want to turn that on or off. Just be aware that it's there. 
13. Now once we have this, we can also change the rotation of this so we can position the light where we want. We can turn up or down the "Intensity". So if we want more intense light, we can certainly do that, bring it down to 0 or bring it up to say 5 so we have much more intense light and this is really going to balance it against the other lights in the scene. Now I have what's called a post-process volume in here, which does kind of an auto-exposure. So you're not going to get too wild of a light here. But typically, the default value for "Intensity" is 1. And you can see how the auto-exposure is kind of making this work. And also notice that with this, it's not really sticking to that ground when I've got that used camera projection. So if I turn that off, you can see it's sticking a little bit better. But again, I'm getting a little bit of a distorted effect here. And some images won't give you that. It just depends on what you have. 
14. So if I have this approaching storm, which was my default, you can see that maybe it's a little bit better. Anyways, and you can always go back and turn on your own ground here. So I'm going to go back into here, into my cabin folder. Find that ground grass, SM_GroundGrass and turn it back on. And then move it back up a little bit. And actually move my HDRIBackdrop down just a bit. There we go. So again, you can create your own ground plane, or you can use the HDRI Backdrop as your ground plane. But this is a really good way to have highly realistic lighting in your scene that's very controllable.

### Additional light types
Level 07_03
1. In addition to environmental lighting, you can also add individual lights into your scenes, such as a spotlight or point light. So let's take a look at how to use those. So in this scene, well, I already have some light in here. I have a sun and sky. So I'm just going to select sun and sky and toggle the visibility off. And that'll darken our scene. 
2. And let's add a single light into this. So I'm going to go into my quickly add menu, go into lights and let's select Point Light. Now, if I move that, in this case, along the red axis and then up along the blue axis, you'll see that this is illuminating the scene. Now the point light is basically just a point light source. So it illuminates in all directions. So it's like the bare light bulb in the room. 
3. So let's take a look at some of the attributes that we can control in the details panel. So under light, we have intensity. I'm going to turn this up or down, make it brighter or dimmer. And we can change the unit. So if you want to make it a very specific light, you can do that. We're using candelas but you can also use things such as lumens or EV or so on. 
__NOTE__ The candela has replaced the standard candle or lamp as a unit of luminous intensity in calculations involving artificial lighting and is sometimes called the new candle. It is the unit of Luminous intensity. The symbol of Candela is Cd. 1 candela is equal to 4π lumen.
4. We can change the color of the light. So if you want tinted lights, you can obviously do that. 
5. And then the attenuation radius. Now, notice how this is kind of falling off after a certain distance. And you can see this little blue sphere kind of indicates that. So if we bring that down (to 400) and you'll see that while we have an attenuation radius, so that's where that light falls off. So if you want to make your lights really specific to an area, you can do that. Or you can make your attenuation radius larger and then that will make the light illuminate more things. 
6. We also have a source radius. Now this basically controls the softness of the shadows. So basically makes the light physically bigger. So you can see this most in the shadows of the scooter. So as I bring that up, you'll see the shadows are starting to fade out. Now if you make it 0, that makes it a true point light and you get the sharpest shadows. 
7. Now, in addition to this, we can change the temperature of the light. That's another way to tint it. 
8. And then if you want to turn the light off, you can just turn off Affects World. That will basically turn it off. 
9. And we can also turn shadows on or off for a specific light. 
10. Now another thing that you can do is you can control what's called indirect lighting. And so that's basically bounced lighting in the scene. So right now it's set to 1, but let's go ahead and zoom in a little bit on this scooter here. And if I turn this all the way up, let's turn it up to maybe six, you'll notice I'm getting this kind of bluish/greenish kind of sheen underneath it. And that's the bounced lighting from the surface of this scooter. So it's basically the same color as the scooter. So as I turn this down, that bounced lighting goes away. And also notice how it kind of illuminates generally the scene as well. So this gives you a lot more bounced lighting from this specific light. 
11. Now, in addition to this, we have a number of other parameters. If you want, you can change the falloff of the light. Right now it's set to the default which is inverse square, which is a real-world light. 
12. Let's take a look at some of the other lights as well. So I'm going to go ahead and turn off my point light by making it invisible. And let's go ahead and add a spotlight. And so let's go ahead and move that. You can see I can move this up or over, and I can rotate it to get a nice effect or I can move it. So the spotlight is very much more, as it sounds, it just illuminates a spot or an area. 
13. Now, in addition to all the attributes that we can use for the point light, you can see we have the same intensity and color and all that. 
14. We also have what's called the cone angle. So the outer cone angle is how wide is that or narrow is that spotlight. And then we have what's called an inner cone angle. And so what that does is that it basically defines how fast that light falls off. So when they're the same, you'll see we get a really sharp edge. And when the inner cone angle is less, you'll see it fades off from here to here. So that's the spotlight. 
15. Let's go ahead and turn that off. And then let's add in one more. We're going to add in lights, Rect Light. So that's a rectangular light. And that's essentially the same as a softbox. And so it's a light that's emitted from an area. So it's basically an area light. And it's really similar to a spotlight, but it has another couple of controls here. So we have our source width. We can make it really wide or really narrow. It simulates something maybe like a tube light or something like that. 
16. We can also change what's called the barn door angle and the barn door length. So I'm going to increase that barn door length so you can see it. And then you change that barn door angle and you can get kind of a soft spotlight effect. And again, this is very similar to a softbox. 
__NOTE__ Barn doors are light modifiers that shape and direct light. They are flexible to use and can create focused light. They also make a variety of shapes. Barn doors are fixed onto the front of studio or theatre lights. They have four hinged doors around the light source.
17. Now, finally, the last light that we have is probably one you're not going to be using if you use stuff such as sun and sky, but that's called the directional light. So let's go into lights, directional light. And it's very similar to sunlight in that it's not positioned in any one spot. 
18. So if I were to move this, nothing happens. The only thing I can do is basically rotate it. So I can rotate it, but the light is basically coming from an infinite source. And so it's kind of a way to simulate sunlight and sometimes it's helpful. Typically, I use sun and sky for this, but you can also use a directional light. So let's go through these lights again. We have directional light. Delete that. We have the rect light, which is essentially a softbox, spotlight, and point light. So all those lights can be used in combination or alone to create very specific lighting effects.