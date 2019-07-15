# Scratch
An OSL shader that generates texture to make swirly micro scratch look by controlling the anisotropy and roughness.

It works well with both metal:

<img src="./images/a.png" width="600" height="600">

and dielectric:

<img src="./images/b.png" width="600" height="600">

The original idea is from Hang Li(悬挂鲤) and Ben Paschke. Here I implemented it using OSL and exposured some arts friendly parameters.


# Parameters

### density
Controls the heaviness of the scratches.

More scratches takes longer to generate.

<img src="./images/0000.png" width="400" height="400">
<img src="./images/0008.png" width="400" height="400">
<img src="./images/0020.png" width="400" height="400">

### roughness default/min/max
*default* values set the roughness of areas that isn't scrached.

*min/max* controls the range of roughness randomness.

Bigger roughtness makes the swirl longer along it's direction.

<img src="./images/0114.png" width="400" height="400">
<img src="./images/0123.png" width="400" height="400">
<img src="./images/0131.png" width="400" height="400">

### anisotropy default/min/max
Similiar to roughness default/min/max, but namely controls the anisotropy.

Bigger anisotropy enlarge the swirl radius.

<img src="./images/0083.png" width="400" height="400">
<img src="./images/0092.png" width="400" height="400">
<img src="./images/0099.png" width="400" height="400">

### offset
Rotation offset.

> ##### 💡 Tips
> Tweak this parameter to achieve some intersting effect, like radiant or spiral scraches!

<img src="./images/0030.png" width="400" height="400">
<img src="./images/0033.png" width="400" height="400">
<img src="./images/0044.png" width="400" height="400">

### width
Width of the scratches, in UV space.

> ##### 💡 Tips
> 0.001 is a good value to start with.

<img src="./images/0132.png" width="400" height="400">
<img src="./images/0136.png" width="400" height="400">
<img src="./images/0141.png" width="400" height="400">

# Output
 - R: Should be connected to *roughness*.
 - G: Should be connected to *rotation* of anisotropy. With arnold you should add a aiNegate and set the offset to 0.25.
 - B: Should be connected to *anisotropy*.


# Usage

Take a look at the examples under "example_scenes/". For now there are only mtoa and Clarisse scenes shipped. But anyone is welcome to contribute any DCC oriented examples.

For clarisse:

![](./images/clarisse.png)

For maya:

![](./images/maya.png)

(Of course, again, the compatibility is not limited to the DCCs listed above.)

Note that the definition of "Anisotropic Rotation" is slightly different between Clarisse and Arnold. That's the reason that in maya we need some conversion when handling the rotation attribute.

