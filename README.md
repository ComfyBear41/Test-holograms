# 3D binary stereoscopic hologram generation

The following it's an explanation of how to generate a 3D binary stereoscopic hologram using Blender and Python from the coded attatched to this repoitory. The process its divided in three main processes:

1. **Subimages generation using Blender.**
2. **Hogel generation from the subimages.**
3. **Binary hologram generation.**

The ultimate result should be a bmp file which can be printed or used in computational simulations verify the generated hologram.

## How does it work

A detailed explanation is given in *inserte cita chida*

## How to use

Make sure you download all the files,especially the file *BinaryStereograhpicHologramFunctions.py* which contains all the important functions for the hologram generation. Also check all the requirements mentioned in *requirements.txt* to avoid having troubles when running the file codes.

The variables the user must be careful when using all the different file codes are:
- *N_in* : Number of inches.
- *res* : Resolution of the printer.
- *N_proj_i* : Number of vertical projections.
- *N_proj_j* : Number of horizontal projections.

If these do not coincide in all the files, it may cause errors when compiling the codes. There are some other variables that the user may play around at their own discretion to obtain different results.

### Subimages generation using Blender

To generate the subimages prepare a centered scene in Blender (It's highly reccomendable to center the scene since the program was built that way). Then in the **Scripting** tab use the code from *SubimageGeneration.py* and run it. An important thing is to coincide the name of the variable *current_object* with the object name in Blender. This program normally works with only one object (as seen in the [Example](https://github.com/ComfyBear41/Test-holograms/edit/main/README.md#example)) but if desired make sure you choose one specific object which the camera will follow and make that object part in blender coincide with the name of the variable *current_object*.

Normally, we would import **stl files** to the scene and generate the subimages. That being said all directories must be changed according to the user and if everything is being generated within Blender some parts of the code may be commented and compiled as usual. One variable that the user may want to change is:

- *max_abs_azimut* : Maximum angle that will be spaned horzintonally (by default its set at 48°)
- *max_abs_polar* : Maximum angle that will be spaned vertically (by default its set at 24°)

**NOTE:** The script from the aforementioned file can be used as a base program and can be modified at the users desire. The important thing is to capture the desired object from different ordered perspectives. 

### Hogel generation from the subimages

Once the subimages are generated, the user must compile the file *mainHogelGeneration.py* which will calculate the hogels for each perspective and return an *npy file* with the information of all the hogels stacked in order of perspective in a single matrix. The variables that the user may want to change are: 

- *scale* : Scaling factor for the perpesctive of the scene within a single hogel (by default its set to 0.3 that gave us the best results). The user can input several scaling factors in a vector to obtain different results.
- *N_cicles* : Number of cycles that the algorithm to generate the hogel will use (by default its set to 500 which guarantees convergence).
- *crop_percentage* : A percentage to crop each subimage from the edges where 0 represents 0% croping the edges and 1 croping 100% of the image. Value
    of 1 for this parameter is won't do anything to the hogel. Change this parameter at your own discretion depending on the subimages.
    

como jala
que se le puede cambiar
notas adicionales


### Binary hologram generation

como jala
que se le puede cambiar
notas adicionales

## Example

