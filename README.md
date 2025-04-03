# All-About-Creality-Raptor-Scanner
This is a tutorial repository for the creality raptor 3D scanner. This repository will explain how to set up the scanner, scan an object, and process its 3D model in other software.

# Information About the Scanner
* The scanner we use is the Creality Raptor.
* There are 2 scanning modes: blue laser mode (which uses blue lasers to scan) and infra-red mode (uses infrared camera to scan.) Blue filter mode works with markers and infra-red filter mode works without markers.
* There are 2 connection configurations: WiFi or wired. In the WiFi configuration, you connect the scanner to the WiFi handle. The handle will create a closed network for sending data to the creality software as well as power the scanner. For the wired configuration, you connect the scanner to power and use a long USB cable to connect to the computer.
* There is a way to use your phone on top of the scanner so that you can better see what the computer sees when you scan. To do this, just scan the QR code and connect to the wifi (will add more info here when I can take screenshots in lab)
* You can calibrate the scanner while it is connected in the USB wired configuration.
* The ▷| button on the scanner has an LED ring aroung it, this is a representation of the histogram seen in the software. When it is blue, you are too far from the object for it to scan properly. When it is green, you are just right. When it is red, you are too close. When it flashes, it has lost track of its location, and you need to hold it still in a familiar area for a moment.

# Scan an object
The purpose of scanning an object is to create a point cloud in the software to be processed. A point cloud is a large collection of XYZ coordinates that represents an object.
1. Connect the scanner to the creality software either through WiFi or the USB wire.
2. Press "New Project" and name your scan. Follow the naming convention of all lowercase with underscores for spaces. For example, "metal_cube", "basketball", "table_red".
3. Choose Blue Laser Mode. The default settings are all ok except color mapping, make sure that is checked "Yes". (Make sure all of your scans get the color map, because the software will not merge scans without a color map to ones that do.)
4. Press the "Scan" button at the bottom to start.

### Scanning tips
* Ensure that the object is in a stable position- if the object moves while you're scanning, you have to end the scan immediately and take a new one or else it will mess up the data.
* Provide sufficient lighting.
* Take as few scans as possible to avoid the model appearing bumpy or having a strange texture map. You want to avoid scanning the same area in a new take as much as you can, but still get a little bit of common area for the purpose of merging.
* You can pause or resume the scan at any time by pressing the pause/play button in the software, on your phone, on the scanner, or on the wifi handle.
* In the software the green areas are where the scanner was able to get a lot of information, the red areas are where it has not enough information about the object. You want as much green as possible.

5. When you have scanned the areas needed and you have a nice green representation of it in the software, press the red ◼ button to end the scan. If you would like to take another scan, hit the + button near the top left of the screen. If that was the last scan needed, you now have to process your scan(s) in the creality software.

# Processing your scan in creality
1. Edit the point cloud of your scans.

   For whatever reason, your scan may grab extra points for the point cloud that are not an accurate representation of the object you're trying to scan. Because of this you will usually be deleting the table from under the object. Rotate your point cloud by left clicking and dragging the mouse. Move your point cloud by right clicking and dragging. Select points by holding shift and left clicking, then draw around the area you want to select. If you've accidentally selected too much, you can de-select by holding CTRL and then drawing around what you want to deselect. Once you have selected the points you want gone, press DEL.

2. Once you have cleaned up the point clouds, press the magic wand button to optimize your point clouds. The default settings are fine.

3. If you have multiple scans, you will need to merge them together. Hit the button below the magic wand (looks like two puzzle pieces connecting) to open the merge menu. Here, you can either merge automatically or manually. Sometimes automatic merging works very well, but if it doesn't, go to manual merge. Choose one point cloud for the fixed window and another for the floating window. (will add more details about how to manually merge here later. need to see the software.)

4. Once you have a single point cloud that represents your object, hit the mesh button (under the merge button.) This converts your point cloud to a mesh. A mesh is a collection of vertices, edges, and faces to define the shape of an object. This is the usual form of 3D objects on a computer. Usually, checking the option to close holes is ok but the "closure" option may cause issues. This option will ensure that the entire mesh is "sealed." It is usually too aggressive and will incorrectly combine areas of the object.

5. Now that you have a mesh, apply its color map by hitting the paint pallete button (under the mesh button.)

6. Export your finished scan to be processed in other software.

   Every scan will be edited in blender so that we can arrange the mesh, make it into a smaller file, and if needed edit the mesh's geometry. If you need to edit the texture map (say, for removing markers) this can be done in any software that allows for image editing but Krita is the most convenient.

# Process your exported model in blender
* will add more info here when I can see the software in lab

# Edit the texture map in Krita
* will add more info here when I can see the software in lab
