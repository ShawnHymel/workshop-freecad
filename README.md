In this workshop, we create a simple two-part box (base and lid) using FreeCAD. If you have never used FreeCAD before, this is a great place to start!

 * **Audience**: Beginners
 * **Estimated time**: 2 hours

When you are done, you are welcome to 3D print the design.

![FreeCAD box demo 3D printed](.images/freecad-box-demo.png)

Want to go beyond this workshop? Check out my full *Introduction to 3D Printing and FreeCAD* series here:

<iframe width="560" height="315" src="https://www.youtube.com/embed/rbe8otH8vMs?list=PLEBQazB0HUyTQkRkbD02DZqnlV6oBMhHB" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## 1. Installation and Configuration

Head to [freecad.org](https://www.freecad.org/) to download the latest version of FreeCAD.

> **Important!** This tutorial was made with **FreeCAD v1.0.0**. Features change between versions--if you cannot find something in your FreeCAD, check the version. You may need to downgrade if you want all buttons, fields, etc. to be in the same place as my screenshots.

Run the installer for your OS.

Open FreeCAD, and click **Edit > Preferences...** In the navigation pane on the left, go to **Display > Navigation**. For the *3D Navigation* setting, select **TinkerCAD**.

![FreeCAD navigation setting in Preferences](.images/screen-01.png)

> *Note*: I personally found the TinkerCAD navigation to be the most intuitive (i.e. it matched my Cura slicer navigation style). Feel free to try other navigation schemes to find one you like. Any navigation instructions given in this guide will be based on the TinkerCAD navigation style.

## 2. Part Design Workbench and Navigation

When you first opened FreeCAD, you probably noticed a number of buttons at the top. These determine what actions you can take within a given *workbench*. A *workbench* is a collection of tools, buttons, views, etc. that allow you to act upon some object or document. Think of workbenches just like workbenches in a machine shop: each has its own uses and tools.

![FreeCAD workbenches](.images/screen-02.png)

You can click the **workbench drop-down** to select which workbench you'd like to use. By default, FreeCAD recommends the *Part Design* workbench. *Part Design* allows you to build up and carve out in a linear set of steps (e.g. by making sketches and then padding/extruding or pocketing/cutting). If you've worked with other modern CAD tools, like SolidWorks, Onshape, or Fusion, this will be a very familiar workflow.

> Note that changing the workbench changes the buttons, tools, menu items, and views!

*Part*, on the other hand, is an older workbench that allows you to create 3D objects by adding and subtracting simple shapes (e.g. cubes, spheres). If you've worked with CAD programs like Tinkercad, this workflow will be familiar.

We will work mainly in the *Part Design* and *Sketcher* workbenches in this tutorial. *Sketcher*, as the name implies, allows you to make fully parametric (i.e. defining shapes through the use of parameters and relationships) sketches. Other workbenches exist for more advanced functionality (e.g. finite element analysis, CAM for manufacturing).

 * Select the **Part Design** workbench (if not already selected)
 * Click **File > New** to create a new document
 * Select the document (named **Unnamed**) in the *tree view* pane on the top-left
 * Click the **Create body** button to create a new *Body* in the document

![Create a new body](.images/screen-03.png)

A *Body* is a single, contiguous object in the *Part Design* workbench. You add sketches, extrude ("pad") and cut ("pocket") in a body to make your object. Note that *Body* must be a single (contiguous) object--you cannot have disconnected parts in the same *Body*! If you try to do this, FreeCAD will throw an error. As you'll see, you can have multiple bodies in the same document!

 * Click on **Origin** under your *Body* in the *tree view*. Press the **spacebar** to toggle its visibility.
   * You should see axes and planes appear in the main 3D view
 * Right-click and hold in the main 3D view, drag your mouse around to adjust the viewing angle
   * A red dot appears to show you where you clicked (the camera rotates relative to that point)

![Rotate 3D view in FreeCAD](.images/screen-04.png)

 * Middle-click and hold in the main 3D view, drag your mouse around to pan the view
 * You can also left-click on objects, faces, lines, points, etc. in the 3D view to select them

> This navigation style is the *TinkerCAD* scheme we set in the Preferences window earlier. You are welcome to change the style if it is not to your liking.

## 3. Variable Set

The thing that makes *parametric* modeling unique (as opposed to *direct* modeling that you might find in e.g. Blender) is the ability to set parameters and relationships among your different design elements. For example, we can set a box length and width that can be adjusted long after we finish our design to easily scale our box! There are a number of ways to accomplish this in FreeCAD, such as sketch parameters or spreadsheets, but we'll use a *variable set*.

 * 


## **1\. Setting Up Global Parameters with Spreadsheets**

Using a spreadsheet in FreeCAD allows you to define global parameters that can be referenced throughout your design. This makes your model parametric and easily adjustable.

### **Steps:**

1. **Create a New Document**:  
   * Open FreeCAD.  
   * Close any previous documents.  
   * Go to **File** \> **New**.  
2. **Switch to Spreadsheet Workbench**:  
   * Select **Spreadsheet** from the workbench selector.  
3. **Create a New Spreadsheet**:  
   * Click the **New Spreadsheet** icon.  
   * Rename the spreadsheet to `globals` by right-clicking on it in the tree view and selecting **Rename**.  
4. **Define Parameters**:  
   * In column A, list the parameter names:  
     * `length`  
     * `width`  
     * `base_height`  
     * `lid_height`  
     * `fillet`  
     * `thickness`  
     * `gap`  
   * In column B, enter the corresponding values.  
     * `60 mm` (length)  
     * `40 mm` (width)  
     * `10 mm` (base\_height)  
     * `10 mm` (lid\_height)  
     * `4 mm` (fillet)  
     * `2 mm` (thickness)  
     * `0.2 mm` (gap)  
   * **Note**: Adjust these values as desired.  
5. **Assign Aliases**:  
   * Right-click on each cell in column B.  
   * Select **Properties** \> **Alias**.  
   * Assign the alias matching the parameter name (e.g., cell B1 alias is `length`).

%%%screen-01

## **2\. Designing the Box Base**

We'll use the Part Design workbench to create the base of the box.

### **Steps:**

1. **Switch to Part Design Workbench**:  
   * Select **Part Design** from the workbench selector.  
2. **Create a New Body**:  
   * Click the **Create Body** icon.  
3. **Create a New Sketch**:  
   * Click the **Create Sketch** icon.  
   * Select the **XY plane**.  
4. **Draw the Base Rectangle with Fillets**:  
   * Use the **Rectangle** tool to draw a rectangle centered around the origin.  
   * Use the **Fillet** tool to round all four corners.  
   * Apply **Equal Constraint** to all fillets to keep them the same size.  
5. **Constrain the Sketch**:  
   * **Set Length and Width**:  
     * Use the **Dimension** tool.  
     * Click on opposing points of the rectangle.  
     * Enter expressions referencing the spreadsheet (enter ‘=’ or click on the small equation editor icon):  
       * Length: `<<globals>>.length`  
       * Width: `<<globals>>.width`  
   * **Set Fillet Radius**:  
     * Click on a fillet arc.  
     * Set radius: `<<globals>>.fillet`  
   * **Center the Sketch**:  
     * Use the **Symmetry Constraint** to center the rectangle around the origin.

%%%screen-02

6. **Pad the Sketch**:  
   * Click **Close** to exit the sketch.  
   * With the sketch selected, click the **Pad** icon.  
   * Set the pad length: `<<globals>>.base_height`.

%%%screen-03

7. **Create outer lip:**  
   * Create a sketch on top of the box  
   * Create a rounded rectangle  
   * Make it symmetrical about the origin  
   * Give it the following dimensions:  
     * Length: \<\<globals\>\>.length \- \<\<globals\>\>.thickness  
     * Width: \<\<globals\>\>width \- \<\<globals\>\>.thickness  
     * Fillet radius: \<\<globals\>\>fillet \- \<\<globals\>\>.thickness / 2  
   * Give each of the dimensions names:  
     * Length: lip\_length  
     * Width: lip\_width  
     * Fillet: lip\_fillet  
8. **Create inner lip:**  
   * Create another rounded rectangle inside the first one  
   * Make it symmetrical about the origin  
   * Give it the following dimensions:  
     * Length: \<\<globals\>\>.length \- 2 \* \<\<globals\>\>.thickness  
     * Width: \<\<globals\>\>width \- 2 \* \<\<globals\>\>.thickness  
     * Fillet radius: \<\<globals\>\>fillet \- \<\<globals\>\>.thickness

%%%screen-04

9. **Pad the lip**  
   * Select previous sketch, pad 3 mm  
10. **Create pocket sketch**  
    * Create a new sketch on the top of the original box base  
    * Use the **external geometry** tool to bring in parts of the inner lip (should create pink dashed lines denoting external reference geometry)  
    * Draw a rounded rectangle  
    * Set the sides and fillet to be equal to the external geometry

%%%screen-05

* Set the rounded rectangle to be symmetrical about the origin  
  * When the sketch is fully constrained, close out of the sketch  
11. **Create a pocket**  
    * Select the previous sketch  
    * Click the **Pocket** tool  
    * Set the pocket depth: \<\<globals\>\>.base\_height \- \<\<globals\>\>.thickness

%%%screen-06

## **3\. Creating the Lid**

We'll create a lid that fits snugly over the base using a second body and a sub-shape binder.

### **Steps:**

1. **Create a New Body for the Lid**:  
   * Click the **Create Body** icon.  
   * Rename this body to `lid` by right-clicking and selecting **Rename**.  
2. **Create a Sub-Shape Binder**:  
   * Make sure `lid` is the active body.  
   * Select the `base` body in the tree view.  
   * Click the **SubShapeBinder** icon (green icon).  
   * This creates a reference of the base in the lid body.

%%%screen-07

3. **Create the Lid Sketch**:  
   * Offset the sketch (rather than sketching directly on the sub-shape binder)  
     * Click **Create Sketch**.  
     * Select the **XY plane**.  
     * After creating the sketch, adjust its position:  
       * In the **Property** panel, under **Attachment** \> **Position**, set **Z** to `<<globals>>.base_height + globals.gap`.  
4. **Draw the Lid Profile**:  
   * Use the **Rounded Rectangle** tool to match the base's outer dimensions.  
   * Make it symmetrical about the origin  
   * Use the external geometry tool to bring in the outermost lines/fillet from the base sub-shape binder as reference lines  
   * Set the top line, left line, and fillet to be equal to the external geometry

%%%screen-08

5. **Pad the Lid Sketch**:  
   * Exit the sketch.  
   * Select the sketch and click **Pad**.  
   * Set the pad length: `<<globals>>.lid_height`.  
6. **Create Shell**  
   * Click the bottom face of the lid  
   * Click the **Thickness** tool  
     * Set the thickness: \<\<globals\>\>thickness  
     * Click OK

%%%screen-09

7. **Create the Inner Lip of the Lid**:  
   * Create a new sketch on the bottom face (outer wall bottom face) of the lid  
   * Draw a rounded rectangle for the lip that will fit over the base's lip.  
   * Use expressions to set dimensions:  
     * Length: `Sketch001.Constraints.lip_length + 2 * <<globals>>.gap`  
     * Width: `Sketch001.Constraints.lip_width + 2 *` `<<globals>>.gap`  
     * Fillet: `Sketch001.Constraints.lip_fillet +` `<<globals>>.gap`  
   * **Pocket the Sketch**:  
     * Exit the sketch.  
     * Select the sketch and click **Pocket**.  
     * Set the pocket length: `Pad001.Length`  
8. **Change lid appearance**  
   * Right-click on the lid in the Tree View, select **Appearance**  
   * Change color via Custom appearance \> Ambient color  
   * Change the Transparency with the slider in the Task Pane

%%%screen-10

## **4\. Adding Chamfers and Fillets**

Adding chamfers and fillets enhances the aesthetic and functionality of your design.

### **Steps:**

1. **Click the Chamfer tool**  
   * Task Pane will guide you through creating chamfers  
2. **Select Edges for Chamfering**:  
   * Click on the edges you want to chamfer (e.g., bottom edges of the base).  
   * Hold **Ctrl** to select multiple edges.  
3. **Apply Chamfer**:  
   * Click the **Chamfer** icon.  
   * Set the chamfer size (e.g., `2 mm`).  
   * Click **OK**.

%%%screen-11

## **5\. Exporting and 3D Printing**

With your design complete, you're ready to export and 3D print. Feel free to check out our Introduction to 3D Printing series to learn more\!

### **Steps:**

1. **Export Bodies as STL Files**:  
   * Select the `base` body.  
   * Go to **File** \> **Export**.  
   * Choose **STL Mesh** format.  
   * Name the file (e.g., `keepsake_box_base.stl`).  
   * Repeat for the `lid` body.  
2. **Prepare for 3D Printing**:  
   * Open your slicing software (e.g., Cura, PrusaSlicer).  
   * Import both STL files.  
   * Arrange them on the print bed.  
   * Adjust settings (layer height, infill, supports if needed).  
   * Slice and save the G-code.  
3. **Print the Model**:  
   * Transfer the G-code to your 3D printer.  
   * Begin printing and monitor the process.

%%%3d-printed-box

## **Importing STEP Files for Reference**

Using STEP files allows you to design enclosures or mounts that fit existing components like a Raspberry Pi.

### **Steps:**

1. **Download a STEP File**:  
   * Visit [GrabCAD](https://grabcad.com/), go to Library, and search for your component (e.g., [Raspberry Pi](https://grabcad.com/library/raspberry-pi-5-2)).  
   * Download the STEP file.  
2. **Import the STEP File into FreeCAD**:  
   * Go to **File** \> **Import**.  
   * Select the downloaded STEP file.  
   * Wait for the import to complete.  
3. **Adjust Orientation**:  
   * If the model isn't oriented correctly:  
     * Right-click on the imported part in the tree view.  
     * Select **Transform**.  
     * Rotate it as needed.  
4. **Create a SubShapeBinder**:  
   * Create a new body for your enclosure or mount.  
   * With the new body active, select the imported part (e.g. PCB)  
   * Click the **SubShapeBinder** icon.  
   * Hide the original imported part.  
5. **Create Sketches Using Reference Geometry**:  
   * Use the **Sketcher** to create mounting holes or outlines.  
   * Use the **External Geometry** tool to reference edges from the SubShapeBinder.

%%%screen-12

6. **Design Your Enclosure or Mount**:  
   * Create pads, pockets, and other features as needed.  
   * Ensure all dimensions are accurate for a proper fit.

## **Challenge: Create a Mounting Plate**

Now that you've learned how to use STEP files and SubShapeBinders, try designing a mounting plate for one of your development boards.

%%%rpi-plate

### **Guidelines:**

* **Choose a Board**: Arduino, Raspberry Pi, or any other PCB.  
* **Import a STEP File**: Find and import the STEP file of your board.  
* **Design the Mount**:  
  * Use the board's mounting holes as references.  
  * Create a plate with pegs or holes to secure the board.  
* **Add Personal Touches**:  
  * Incorporate design elements like logos or text.  
  * Consider adding a snap-on lid or cover.  
* **Share Your Creation**:  
  * Take a screenshot or photo of your design.  
  * Share it on social media with the hashtag `#DKFreeCAD`.  
  * Tag relevant accounts to showcase your work.

## **8\. Conclusion**

Congratulations\! You've advanced your FreeCAD skills by learning how to work with multiple bodies, create assemblies, and use external references like STEP files. These techniques are invaluable for designing complex projects and ensuring your parts fit together perfectly.

**Next Steps**:

* Experiment with more complex assemblies.  
* Explore additional FreeCAD workbenches for advanced features.  
* Stay tuned for the next tutorial, where we'll dive into creating mounting holes and using heat-set inserts.

Happy designing\!

| Tags |  |
| :---: | :---- |
| **Development** |  |
| **Platforms** |  |
| **License** |  |
| **DK Part Numbers** |  |

