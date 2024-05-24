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