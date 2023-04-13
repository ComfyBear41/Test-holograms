# 3D binary stereoscopic hologram generation

The following it's an explanation of how to generate a 3D binary stereoscopic hologram using Blender and Python from the coded attatched to this repoitory. The process its divided in three main processes:

1. **Subimages generation using Blender.**
2. **Hogel generation from the subimages.**
3. **Binary hologram generation.**

The ultimate result should be a bmp file which can be printed or used in computational simulations verify the generated hologram.

## How does it work

A detailed explanation is given in *inserte cita chida*

## How to use

### Subimages generation using Blender

To generate the subimages prepare a centered scene in Blender (It's highly reccomendable to center the scene since the program was built that way). Then in the **Scripting** tab use the code from *SubimageGeneration.py* and run it. An important thing is to coincide the name of the variable *current_object* with the object name in Blender. This program normally works with only one object (as seen in the [Example](https://github.com/ComfyBear41/Test-holograms/edit/main/README.md#example)) but if desired make sure you choose one specific object which the camera will follow and make that object part in blender coincide with the name of the variable *current_object*.

Normally, we would import stl files to the scene and generate de subimages. That being said all directories must be changed according to the user and if everything is being generated within Blender 

**NOTE:** The script from the aforementioned file can be used as a base program and can be modified at the users desire. The important thing is to capture the desired object from different ordered perspectives. 

### Hologram generation from the subimages

como jala
que se le puede cambiar
notas adicionales


### Binary hologram generation

como jala
que se le puede cambiar
notas adicionales

## Example

