# Creality Raptor Scanner Tutorial
This is a tutorial repository for the creality raptor 3D scanner. This repository will explain how to set up the scanner, scan an object, and process its 3D model in other software.

# Table of Contents

- [Introduction](#introduction)
- [Scanning Process](#scanning-process)
   - [Scan an Object](#scan-an-object)
   - [Processing the Scan in Creality](#processing-the-scan-in-creality)
- [Post-Processing](#post-processing)
   - [Process the Exported Model in Blender](#process-the-exported-model-in-blender)
   - [Edit the Texture Map in Krita](#edit-the-texture-map-in-krita)
      -  [Erasing markers from texture maps](#erasing-markers-from-texture-maps)
      -  [Fixing "glitchy" tone patterns in texture maps](#fixing-glitchy-tone-patterns-in-texture-maps)

# Introduction
- The scanner we use is the Creality Raptor.
- There are 2 scanning modes:
   - blue laser mode (which uses blue lasers to scan)
   - infra-red mode (uses infrared camera to scan.)

Blue filter mode works with markers and infra-red filter mode works without markers.

- There are 2 connection configurations:
   - WiFi
   - Wired
  
They can be seen below. In the WiFi configuration, you connect the scanner to the WiFi handle. The handle will create a closed network for sending data to the creality software as well as power the scanner. For the wired configuration, you connect the scanner to power and use a long USB cable to connect to the computer. ![modes](https://github.com/user-attachments/assets/ec1a4d6c-0b4d-4b07-aad4-e020d38a8b5d)


- When the WiFi handle mode is used, you can place a phone on top of the scanner so that you can better see what the computer sees when you scan. To do this, while on the scanning screen press the button shown below circled in red and follow the instructions. ![phone_scan_mode](https://github.com/user-attachments/assets/c470e7af-465d-40c2-9d85-082467e34e8d)



- You can calibrate the scanner while it is connected in the USB wired configuration.
- The ▷| button on the scanner has an LED ring aroung it, this is a representation of the histogram shown during scanning (see picture below.) When it is blue, you are too far from the object for it to scan properly. When it is green, you are just right. When it is red, you are too close. When it flashes, it has lost track of its location, and you need to hold it still in a familiar area for a moment. ![histogram_flat](https://github.com/user-attachments/assets/0decc243-28f3-4986-92c9-0810220236ed)

# Scanning Process
## Scan an Object
The purpose of scanning an object is to create a point cloud in the software to be processed. A point cloud is a large collection of XYZ coordinates that represents an object. After you open the creality software, scanning an object is the first step to a fully processed 3D model.

**1.** Open the creality scan software. Connect the scanner to the computer either through WiFi or the USB wire. Once you are connected, this is what you will see:
![01](https://github.com/user-attachments/assets/2a0ad620-b635-44f7-80a8-ec4a18256bc3) At the top, you can see there are multiple tabs- device, home, scan, process, and edit. The device tab is where you just were when you were connecting the scanner. The home tab is where you are now, here you can open past projects, calibrate the scanner, and create new projects. The scan tab is where you will be during the process of scanning. The process tab is where you will process your scan into a point cloud, then a mesh, then add a texture map, and then export the model as a .obj. We will not use the edit tab, but it is used for editing the mesh.

**2.** Press "New Project" and name your scan. Follow the naming convention of all lowercase with underscores for spaces. For example, `metal_cube`, `basketball`, `table_red`. ![02](https://github.com/user-attachments/assets/1154d03d-c3e7-4ddd-bcff-a4cf70eefcf5)

**3.** Choose Blue Laser Mode. The default settings are all ok except color mapping, make sure that is checked "Yes". (Make sure all of your scans get the color map, because the software will not merge scans without a color map to ones that do.)

**4.** Press the `Scan` button at the bottom to start.

### Scanning tips
- Ensure that the object is in a stable position- if the object moves while you're scanning, you have to end the scan immediately and take a new one or else it will mess up the data.
- Provide sufficient lighting.
- Take as few scans as possible to avoid the model appearing bumpy or having a strange texture map. You want to avoid scanning the same area in a new take as much as you can, but still get a little bit of common area for the purpose of merging.
- You can pause or resume the scan at any time by pressing the pause/play button in the software, on your phone, on the scanner, or on the wifi handle.
- In the software the green areas are where the scanner was able to get a lot of information, the red areas are where it has not enough information about the object. You want as much green as possible.

**5.** When you have scanned the areas needed and you have a nice green representation of it in the software, press the red square button to end the scan.

   If you would like to take another scan, hit the `+` button near the top left of the screen (shown below.)
   
   ![image](https://github.com/user-attachments/assets/16ae6941-edb4-4d2c-9d17-046d369ed91e)

   If that was the last scan needed, you now have to process your scan(s) in the creality software.


## Processing the Scan in Creality
**1.** Edit the point cloud of your scans.

   Now that you have finished scanning, you should be on the process tab. You will see something like this:

   ![05](https://github.com/user-attachments/assets/56d60de2-6ff6-421b-bbaf-52e2560f2bda)

   For whatever reason, your scan may grab extra points for the point cloud that are not an accurate representation of the object you're trying to scan. Because of this you will usually have to delete the table from under the object. Rotate your point cloud by left clicking and dragging the mouse. Move your point cloud by right clicking and dragging. Select points by holding shift and left clicking, then draw around the area you want to select. If you've accidentally selected too much, you can de-select by holding `ctrl` and then drawing around what you want to deselect. Once you have selected the points you want gone, press `DEL`.

**2.** Once you have cleaned up the point clouds, press the magic wand button to optimize your point clouds. The default settings are fine.

   ![06](https://github.com/user-attachments/assets/26a20d16-ac08-487e-a5db-953b33423f21)


**3.** If you have multiple scans, you will need to merge them together. Hit the button below the magic wand (looks like two puzzle pieces connecting) to open the merge menu. Here, you can either merge automatically or manually.

   ![07](https://github.com/user-attachments/assets/f55a6469-a243-4b1e-b46c-bf772463a50b)

   Automatic merging is shown below. To merge, select your scans on the left and then press start. Sometimes, it works very well. But if it doesn't, you have to switch to manual merging.
   ![08](https://github.com/user-attachments/assets/d1d3853f-6741-4bd8-98d1-6269da31b6c1)

   Manual merging is shown below. Select one scan for the fixed window and one scan for the float window. Select points on your scan that are the same on both by pressing shift + left click. To deselect a point press `ctrl` + `left` click. Once you have at least 3 (though you will usually need more) press start to merge.
   ![manual_merge](https://github.com/user-attachments/assets/54a58aae-4d74-4726-800f-9985cf21ef48)

**4.** Once you have a single point cloud that represents your object, hit the mesh button (under the merge button.) This converts your point cloud to a mesh. A mesh is a collection of vertices, edges, and faces to define the shape of an object. This is the usual form of 3D objects on a computer. Usually, checking the hole filling option is ok but the "closure" option may cause issues. Closure will ensure that the entire mesh is "sealed." It is usually too aggressive and will incorrectly combine areas of the object.

   ![09](https://github.com/user-attachments/assets/b93be5d2-dcf0-49fa-8dec-3e2ef44d38ca)

**5.** Now that you have a mesh, apply its color map by hitting the paint pallete button (under the mesh button.)

**6.** Export your finished scan to be processed in other software.

   ![11](https://github.com/user-attachments/assets/0e1ae032-c2d8-4faa-9b28-83dce273915b)

   Every scan will be edited in blender so that we can arrange the mesh, make it into a smaller file, and if needed edit the mesh's geometry. If you need to edit the texture map (usually for removing markers) this can be done in any software that allows for image editing, but this tutorial will use Krita because it is convenient.

# Post Processing
## Process the Exported Model in Blender

**1.** Bring your model into blender
- When you open blender, this is what you will see:

  ![image](https://github.com/user-attachments/assets/6dd0a23a-dff2-4a19-8e3f-966a31c4f1e9)

- Click on the cube and press the delete key.
- Go to File > Import > Wavefront (.obj)
- Select the folder containing the scan of your object from creality.
- Select the .obj file inside the folder. Press "Import Wavefront OBJ"

**2.** Arrange and size your model in the xyz space
- Because the model will be used in other programs, it needs to be aligned correctly in 3D space. We want the object to be centered at the origin and be positioned "straight" with respect to the x, y, and z axes. Also, when you scan the object in creality, it scales the model up by a large amount. So, the computer thinks the object is much larger than it is in real life. We have to scale the object down to fix this.
- Use the scroll wheel on your mouse to zoom out and find the object you imported.
- First, rescale the object; you should see a panel like the one shown below toward the bottom right of your screen.

  ![image](https://github.com/user-attachments/assets/e2885e50-50d6-4d40-b176-959e83a8e55d)

- Set the Scale X, Y, and Z to be 0.001
- Now we will move the object. Right click the object and go to Set Origin > Geometry to Origin.
- Shown below is a 3D model of a drill which I will be using as an example. Your screen should look something like this once you follow the steps above.

  ![image](https://github.com/user-attachments/assets/560a9744-4411-479b-b3da-367ca6b575e7)


- Press in on the scroll wheel to rotate your view. Press shift and in on the scroll wheel to pan your view.
- Press either x, y, or z on the axes map (shown below) to snap your view to the axis.

  ![image](https://github.com/user-attachments/assets/26a03e55-8075-413e-b18b-4e322de108e2)

- I chose the x axis first for this example. Here is how it looks:
  
  ![image](https://github.com/user-attachments/assets/67f1a632-b974-47c4-9ff8-f3ad1716a91f)

- To center your model, you will need to go to each axis, rotate it, and move it until by your judgement it is centered. To rotate the model around an axis: press R, move your mouse, and left click when the object is at the desired angle. To move the model around an axis: press G, move your mouse, and left click when the object is at the desired position. Generally, you want the +Z direction to be up and -Z to be down. Here is my centered drill, for reference:

  ![image](https://github.com/user-attachments/assets/b99dfb99-c086-4c93-bfb8-b37022a39af3)

- Once you have adjusted the scale, position, and rotation of your object click on the object and press `ctrl`+`A`.
- Click `All Transform`.

**3.** Export your blender model
- Go to File > Export > Wavefront (.obj)
- Navigate to the folder where your original object was stored
- Add _modified to the end of the file name and press Export as .obj

**4.** Ensure file size is < 10 MB
- Open file explorer and go to the folder where you exported your model
- Look at the file size of your modified .obj, is it less than 10 MB (or 10,000 kB ?)
- If yes, skip to step 6.
- If it is greater than 10,000 kB, go back into blender and look at your object. In the panel where you resized the object, click the wrench icon. Click add modifier.
  
  ![image](https://github.com/user-attachments/assets/ade7f81a-3d0d-49e7-a4d4-e87450d97057)

- Go to Generate > Decimate
- Change the ratio to make the file size under 10 MB. For example, if your file is 100 MB, you will change the ratio to 0.1.
- Export the file again, overwrite your previous "_modified" .obj file.

**5.** Re-assign texture map to .obj file
- A 3D model should be in a folder containing 3 files of the same name: a .obj file, a .png file, and a .mtl file. The .obj file is your 3D model. The .png file is your texture map. The .mtl file links the texture map to the 3D object. When we modified the object in blender, it still is set to use the texture map of the unmodified object. So, we are going to copy the texture map and change the .mtl file to tell it to use the copy. This way we can have 3 files for one object all with the same name, for organization purposes.
- Open file explorer and go to the folder that contains your model
- Click on the .png file and press `ctrl`+`C`.
- While in the same folder, press `ctrl`+`V`.
- Rename the copied `.png` file to have the same name as your modified object
- Open the `.mtl` file in notepad, it will look like this:
 
  ![image](https://github.com/user-attachments/assets/eb623c25-ad15-48ad-98c0-86490872acff)

- While being careful not to change anything else, change the circled part to the name of your new texture map
- Press `ctrl`+`S` to save your changes

That's it! You have successfully scanned an object and processed it in blender. If the texture map of your object needs to be edited, you can do so by following the next section of the tutorial. If you'd like to make sure your texture map is correct, you can press this button while viewing your object in blender to show it with the texture map.

  ![image](https://github.com/user-attachments/assets/a35da7b5-ef22-4667-b05b-504a8cd4e5fd)

## Edit the Texture Map in Krita
To edit the texture map of a 3D object, you can you use any software that can draw on a .png file. Because it is free and simple I will be using Krita for this tutorial. Below is a piece of a texture map for a traffic barrier:

![image](https://github.com/user-attachments/assets/9d7a2b7a-ba62-4bb5-adcb-fb385b133f99)

As you can see it is covered in markers which need to be removed. Here is another texture map for a metallic object:

![image](https://github.com/user-attachments/assets/e3f93f42-2a89-4f5d-a8b9-181e9e08e76c)

It has been partially edited, but as you can see the issue with this map is the yellowey tones. Because this is a metallic silver object, we need to remove the yellow spots. The creality raptor is not as good at getting texture maps as it is with getting dimensions. So, this yellowy pattern will likely show up on every metallic object. This could be because of the scanner or because of the way the creality software creates texture maps. So, let's start fixing these in Krita.

When you open Krita, this is what you will see:
![image](https://github.com/user-attachments/assets/bd50db96-bd94-453a-a739-072ebb37d29a)

Click Open Image and navigate to the .png file texture map you want to edit. In this example I will edit the metallic object. It is helpful to have the object open in blender with the texture map showing as a reference. When you open your file, you will see something like this:
![image](https://github.com/user-attachments/assets/40ae0ca6-8344-419e-a3ce-c7d320341210)

To fix texture maps, you need to know how to use the pen tool, the blend tool, the eyedropper tool, how to lock the transparency of the texture map, and how to filter the image.

On the left side of the screen, there is this toolbar:

![image](https://github.com/user-attachments/assets/42328e8c-d5e1-46e7-8ee1-77c5221df6e7)

Circled in red is the brush tool ![image](https://github.com/user-attachments/assets/93e25815-cd5f-4a16-b432-8ecf18dac71e) and the eyedropper tool ![image](https://github.com/user-attachments/assets/4b8de83c-0f16-4800-9922-8e9a8a2e1fd3)

You can think of this toolbar as different modes for your mouse cursor. All we will need to use is the brush and eyedropper tools. Toward the bottom right of your screen, you will see favorited brushes:

![image](https://github.com/user-attachments/assets/32412a47-babc-4638-8d38-d713617972d2)

You can hover your mouse over each brush to see what it does. On this computer I have favorited an airbrush tool, a pen tool, a soft pen tool, a blend tool, and a blur tool. These are all the brushes you will need to fix texture maps. When you have selected ![image](https://github.com/user-attachments/assets/93e25815-cd5f-4a16-b432-8ecf18dac71e) from the toolbar you can click on any of the brush icons to use them. In the provided screenshot I have selected the pen tool. 

At the top of the screen:

![image](https://github.com/user-attachments/assets/ddee2b6f-67bc-4bbd-ba0d-339d29f82764)

You can change the opacity (meaning how "see-through" your brush is) and size of your current brush

When you select the ![image](https://github.com/user-attachments/assets/4b8de83c-0f16-4800-9922-8e9a8a2e1fd3) from the toolbar you will be able to click any part of the image to copy that color. When you do this and switch back to your brush tool you will be able to draw with that color.

Now you need to know how to keep the transparency of the texture map while you are editing it. In the middle right of your screen is your layers panel:

![image](https://github.com/user-attachments/assets/669bc184-a2d7-478b-b8af-77870511982b)

Here you can change manage everything about your layers. When you open a .png in Krita, it will create one layer to work on called "Background." When we edit texture maps we need to make sure we leave the empty spaces empty, so we have to lock the transparency. To do this, click on your layer in the layer panel. Press this button ![image](https://github.com/user-attachments/assets/2bee91af-5f2c-4bbc-8a08-a1af41238927) to duplicate your layer. Now, press this button ![image](https://github.com/user-attachments/assets/814ed247-b49b-4d8a-bc86-4458f0ea45a7)

Once you have followed the above instructions, your layers panel should look like this:

![image](https://github.com/user-attachments/assets/b261a039-e3ef-4b11-b11c-0380b520fb10)

Now the copy of your layer is looking at the original layer for its transparency values. This means that now you can draw anywhere in the file and it will only draw over the texture that was already there. This step is very important. You are now ready to edit the texture map.

Helpful keyboard shortcuts:
* CTRL+A is select all
* CTRL+C is copy
* CTRL+V is paste
* CTRL+T is transform
* CTRL+SHIFT+A deselect all
* B switches to the brush tool
* P switches to the eyedropper tool

### Erasing markers from texture maps

**Draw-over method**
- Use the eyedropper tool to pick the color you want to replace the marker with
- Use the pen tool to draw over the marker with the selected color
- Use the blend tool to blur the edges of the marker covers to make them look natural

**Copy-paste method**
- Press ![image](https://github.com/user-attachments/assets/db67045b-5845-41d2-901a-9023a04796c0) on the toolbar
- Draw around a texture you want to copy
- Copy it with CTRL+C
- Paste it with CTRL+V
- Press CTRL+T to move the copied section over your marker
- Press enter to complete the move
- Blend in the edges of the pasted texture


### Fixing "glitchy" tone patterns in texture maps

The method to fix this depends on the object. Usually you can will use a combination of the Draw-over and Copy-paste methods listed above along with filtering the image. You can filter an image in Krita by pressing ![image](https://github.com/user-attachments/assets/c901f322-8575-4c6b-a6ec-4e16a0e4abfe) 

The following link provides documentation on how to use every filter from the official Krita manual.
https://docs.krita.org/en/reference_manual/filters/adjust.html

### Export your edited texture map
* Go to File > Save As 
* Name your file
* Save it as a .png with the following settings:
  
  ![image](https://github.com/user-attachments/assets/8e898373-c1a9-4709-9891-42e6edf440cd)

* Make sure that you edit the .mtl file of your object to tell it to use the new texture map.


