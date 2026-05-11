---
description: Simple setups and tool paths using an Omio x8-2200L and Mach3Mill
---

# Using the Omio X8-2200L CNC Router Machine

To begin, you'll need to already have your panel or plate designed in Onshape, which can be done by following the [onshape-cad](../../design-guides/onshape-cad/ "mention") documentation.

Following that, move to the computer connected to the CNC machine to open Fusion360, another CAD software - similar to Onshape - but one with the CAM[^1] studio that we will be utilizing to convert your CAD file to gcode[^2] that the CNC router can cut out.

## Importing model from Onshape to Fusion

Stepper blocks let you break down a tutorial or guide into separate, but clearly linked steps. Each step can contain multiple different blocks, allowing you to add detailed information.

{% stepper %}
{% step %}
#### Export from Onshape

Export your model from Onshape as a Parasolid,which should produce a\
downloadable `.x_t` file.
{% endstep %}

{% step %}
#### Upload into Fusion360

Once you’ve inserted your stepper block, you can start adding content to it — including code blocks, drawings, images and much more.
{% endstep %}

{% step %}
#### Confirm Units

Click the `+` below the step numbers or hit `Enter` twice to add another step to your stepper block. You can remove or change the style of the step header or step body if you wish.
{% endstep %}
{% endstepper %}

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

### Orienting Model for Ease of Use Later

Depending on how your file came into Fusion, you may want to reorient it before starting CAM. I like to use the Move/Copy tool to rotate my part so that it’s laying how it will look on the machine; it usually saves me some work on the WCS (work-coordinate system)

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

### Changing Workspaces

Once your model is oriented, change from the Design workspace to the Manufacture workspace.

The Manufacture workspace is where you will set up your operations, toolpaths, and eventually generate your gcode.

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

### Creating a Setup

To begin, create a _New Setup_.

The “setup” is how the part is related to its original stock and how it is oriented on the machine.

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

### Choose Your Machine

In the Setup window, under Machine, choose Select.

Since this isn’t the first time we’re setting up CAM on the CNC Controller machine, we can go to My machines -> Local, then select the machine listed. If you are doing this on a different machine, you can select the Autodesk Generic 3-axis YXZ axis on the Head machine from the Fusion Library.

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

### Work Coordinate System (WCS)

In the Work Coordinate System section, if your X- and Y-axes are not already pointing in the directions you want them, or your Z is not pointing UP, you can use the orientation dropdown to help choose the alignment of those axes. I usually do this part in Design, just to make things easier to see.

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

Choose Stock Box Point as your origin, click Box Point to select where the origin is, and select a point on the TOP of your stock (where you want to put the corner closest to the front-left of the actual machine.

What we are selecting here is where is our “origin” for our x- y- and z-axes so the machine knows where to go relative to some point.

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

### Stock Setup

Still in setup, but under Stock, I will usually use a fixed stock size, since I know what piece of material I have in front of me. You may want to use a relative stock size, which allows you to set how much wider/taller your stock is compared to your model. Either way, make sure the model position in the Z is offset from the bottom and set the offset to 0 in.

If you’re using fixed sized stock, set its dimensions in the Width (X), Depth (Y) and Height (Z) sections.

There are no other options in Stock, Part Position, or Post Process that need to be changed, so you can click OK and move on to your toolpaths.

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

### Toolpaths, Pockets

Before you cut a part free of the stock, you should clear all of the holes/pocket geometry from it. This model has three holes in it, so under 2D operations, we select 2D Pocket.

In the dialogue box that pops up, first select your tool.

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

### Toolpaths, Tool Library

We have all of our tools set up on the CNC Controller machine, and each tool has a preset of speeds/feeds based on the material being cut.

Select the tool you are using, then under presets at the bottom, select the material you are cutting. Larger tools tend to be able to cut more aggressively and clear material faster, so I would use the largest tool you can to complete an operation while minimizing tool changes between operations if possible.

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

### Toolpaths, Pockets, Take 2

Once your tool is selected, all of the speeds and feeds will be pre-populated for you, so you can move on to the Geometry menu.

In the pocket selections box, select Chain, then click the BOTTOM of your first hole

[^1]: Computer-Aided Manufacturing

[^2]: Gcode commands tell your 3D printer or CNC router exactly what actions to perform – where to move, what speed to use, what temperatures to set, and much more.
