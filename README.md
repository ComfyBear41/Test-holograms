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

**NOTE 1:** The script from the aforementioned file can be used as a base program and can be modified at the users desire. The important thing is to capture the desired object from different ordered perspectives. 

**NOTE 2:** The program is build to have certain order of the directories and name the subimages if changed, be aware that the results may lead to errors in the compilation.

### Hogel generation from the subimages

Once the subimages are generated, the user must compile the file *mainHogelGeneration.py* which will calculate the hogels for each perspective and return an *npy file* with the information of all the hogels stacked in order of perspective in a single matrix. The variables that the user may want to change are: 

- *directory0* : Directory to the subimages generated.
- *dir_transfer* : Directory where the *npy files* will be saved.
- *scale* : Scaling factor for the perpesctive of the scene within a single hogel (by default its set to 0.3 that gave us the best results). The user can input several scaling factors in a vector to obtain different results.
- *N_cicles* : Number of cycles that the algorithm to generate the hogel will use (by default its set to 500 which guarantees convergence).
- *crop_percentage* : A percentage to crop each subimage from the edges where 0 represents 0% croping the edges and 1 croping 100% of the image. Value
    of 1 for this parameter is won't do anything to the hogel. Change this parameter at your own discretion depending on the subimages.
    
### Binary hologram generation

With the Hogels generated, the last step is to generate the hologram by using the script in the file *mainBinaryHologram.py*. It is very important to say that specially this script was made to match the equipment that we had access to. So you will notice that this program as it is will work only for resolutions of 2400 or 3600 dpi. This is because part of the process involves using an angle to deviate the difracction orders from the optical axis, and our tries involved only using these resolutions. This does not mean that our method won't work for other resolutions but that a simulation of the holograms will be needed to adjust the difraction orders positions. The variables that are important for this program are:

- *directoryTransfer* : Directory where the hogels as a *npy file* were stored from the [previous step](https://github.com/ComfyBear41/Test-holograms/blob/main/README.md#hogel-generation-from-the-subimages).
- *directorySubimages* : Directory where the subimages generated by the [first step](https://github.com/ComfyBear41/Test-holograms/blob/main/README.md#subimages-generation-using-blender) were stored.
- *directoryTransfer_bmp* : Directory where the binary holograms will be stores as a *bmp file*.
- *lambd* : The wavelength where the hologram will be tested (In general monochromatic light will yiled better results when testing).
- *thz* : Deviation angle in the z-axis
- *thxy* : Deviation angle as a rotation in the plane-xy

When working with high resolutions you may notice that the size of the *npy files* of the hogels is heavy. In this file there are a few commented lines corresponding to a propagator that can be used to test the holograms generated, since the matrix can be to big, we reccomend using another package rather than *matplotlib* such as *rasterio* or *PyQt5* to see the results. After running this programm a *bmp file* with the binary hologram will be generated, this file is ready to print.

**NOTE**: The deviation angles can be constructed in several ways, in this case the proposal is to use $\pi /\alpha$ where $\alpha$ will controll the overall deviation angle. As seen in the parameters put by default, small angles are needed.


## Example

