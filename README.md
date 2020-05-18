<<<<<<< HEAD
# Falcor 4.1

Falcor is a real-time rendering framework supporting DirectX 12. It aims to improve productivity of research and prototype projects.

Features include:
* Abstracting many common graphics operations, such as shader compilation, model loading, and scene rendering
* DirectX Raytracing abstraction
* Render Graph system
* Python scripting
* Common rendering effects such as shadows and post-processing effects
* Unbiased path tracer
=======
Falcor 3.0
=================

Falcor is a real-time rendering framework supporting DirectX 12 and Vulkan. It aims to improve productivity of research and prototype projects.
Its features include:
* Abstracting many common graphics operations, such as shader compilation, model loading and scene rendering
* VR support using OpenVR
* Common rendering effects such as shadows and post-processing effects
* DirectX Raytracing abstraction 

Prerequisites
------------------------
- GPU that supports DirectX 12 or Vulkan
- Windows 10 RS2 (version 1703) or newer, or Ubuntu 17.10

On Windows:
- Visual Studio 2017
- [Microsoft Windows SDK ver 10.0.15063.468](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive)
- To run DirectX 12 applications with the debug layer enabled, you need to install the Graphics Tools optional feature. The tools version must match the OS version you are using (not to be confused with the SDK version used for building Falcor). There are 2 ways to install it:
    - Click the Windows button and type `Optional Features`, in the window that opens click `Add a feature` and select `Graphics Tools`.
    - Download an offline pacakge from [here](https://docs.microsoft.com/en-us/windows-hardware/test/hlk/windows-hardware-lab-kit#supplemental-content-for-graphics-media-and-mean-time-between-failures-mtbf-tests). Choose a ZIP file that matches the OS version you are using. The ZIP includes a document which explains how to install the graphics tools.

DirectX Raytracing 
-------------------------
Falcor 3.0 adds support for DirectX Raytracing. It adds 2 new build configurations - `ReleaseDXR` and `DebugDXR`. These are the only configurations which will build the DXR abstraction layer.
The HelloDXR sample demonstrates how to use Falcor’s DXR abstraction layer.

- Requirements:
    - Windows 10 RS4 (version 1803)
    - Windows 10 Developer Mode enabled (Windows Settings -> Update & Security -> For developers -> Developer mode)
    - You do not need to download the DXR SDK yourself, it is packaged with Falcor.
    - A GPU which supports DirectX Raytracing, such as the NVIDIA Titan V or GeForce RTX (make sure you have the latest driver).

Currently, Falcor doesn’t support the DXR fallback layer. We will add support for it in the near future.  
Please note that the DXR abstraction layer is considererd an experimental feature, just like DXR itself. The interfaces and features might change in future releases.

TensorFlow Support
--------------
Refer to the README located in the `Samples\Core\LearningWithEmbeddedPython` for instructions on how to set up your environment to use TensorFlow and Python with Falcor.

Linux
--------------
Falcor is tested on Ubuntu 17.10, but may also work with other versions and distributions.

To build and run Falcor on Linux:
- Install the Vulkan SDK following the instructions [HERE](https://vulkan.lunarg.com/doc/view/latest/linux/getting_started.html)
- Install additional dependencies:
    - `sudo apt-get install python libassimp-dev libglfw3-dev libgtk-3-dev libfreeimage-dev libavcodec-dev libavdevice-dev libavformat-dev libswscale-dev libavutil-dev`
- Run the `Makefile`
    - To only build the library, run `make Debug` or `make Release` depending on the desired configuration
    - To build samples, run `make` using the target for the sample(s) you want to build. Config can be changed by setting `SAMPLE_CONFIG` to `Debug` or `Release`

Building Falcor
---------------
Open `Falcor.sln` and it should build successfully in Visual Studio out of the box. If you wish to skip this step and add Falcor to your own Visual Studio solution directly,
follow the instructions below.

Creating a New Project
------------------------
- If you haven't done so already, create a Visual Studio solution and project for your code. Falcor only supports 64-bit builds, so make sure you have a 64-bit build configuration
- Add Falcor.props to your project (Property Manager -> Right click your project -> Add existing property sheet)
- Add Falcor.vcxproj to your solution
- Add a reference to Falcor in your project (Solution Explorer -> Your Project -> Right Click `References` -> Click `Add Reference...` -> Choose Falcor)
>>>>>>> parent of 5a12f298... Merge pull request #150 from NVIDIAGameWorks/rel-3.1.0

The included path tracer requires NVAPI. Please make sure you have it set up properly, otherwise the path tracer won't work. You can find the instructions below.

<<<<<<< HEAD
## Prerequisites
- Windows 10 version 1809 or newer
- Visual Studio 2019
- [Microsoft Windows SDK version 1903 (10.0.18362.1)](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive)
=======
Build Configurations
--------------------
Falcor has the following build configurations for DirectX 12, Vulkan and DXR, respectively:
- `DebugD3D12`
- `ReleaseD3D12`
- `DebugVK`
- `ReleaseVK`
- `DebugDXR`
- `ReleaseDXR`
>>>>>>> parent of 5a12f298... Merge pull request #150 from NVIDIAGameWorks/rel-3.1.0

Optional:
- A GPU which supports DirectX Raytracing, such as the NVIDIA Titan V or GeForce RTX (make sure you have the latest driver)
- Windows 10 Graphics Tools. To run DirectX 12 applications with the debug layer enabled, you must install this. There are two ways to install it:
    - Click the Windows button and type `Optional Features`, in the window that opens click `Add a feature` and select `Graphics Tools`.
    - Download an offline package from [here](https://docs.microsoft.com/en-us/windows-hardware/test/hlk/windows-hardware-lab-kit#supplemental-content-for-graphics-media-and-mean-time-between-failures-mtbf-tests). Choose a ZIP file that matches the OS version you are using (not the SDK version used for building Falcor). The ZIP includes a document which explains how to install the graphics tools.
- NVAPI (see below)

## NVAPI installation
After cloning the repository, head over to https://developer.nvidia.com/nvapi and download the latest version of NVAPI (this build is tested against version R435).
Extract the content of the zip file into `Source/Externals/.packman/` and rename `R435-developer` to `NVAPI`.

Finally, set `_ENABLE_NVAPI` to `true` in `Source/Falcor/Core/FalcorConfig.h`

## CUDA Support
Refer to the README located in the `Source/Samples/CudaInterop/` for instructions on how to set up your environment to use CUDA with Falcor.

## Falcor Configuration
`FalcorConfig.h` contains some flags which control Falcor's behavior.
- `_LOG_ENABLED` - Enable/disable log messages. By default, it is set to `true`.
- `_PROFILING_ENABLED` - Enable/Disable the internal CPU/GPU profiler. By default, it is set to `true`.

## Resources
- [Falcor](https://github.com/NVIDIAGameWorks/Falcor): Falcor's GitHub page.
- [Documentation](./Docs/index.md): Additional information and tutorials.
    - [Getting Started](./Docs/Usage/Getting-Started.md)
    - [Render Graph Tutorials](./Docs/Tutorials/index.md)
- [ORCA](https://developer.nvidia.com/orca): A collection of high quality scenes and assets optimized for Falcor.
- [Slang](https://github.com/shader-slang/slang): Falcor's shading language and compiler.

## Citation
If you use Falcor in a research project leading to a publication, please cite the project.
The BibTex entry is

```bibtex
@Misc{Benty20,
   author =      {Nir Benty and Kai-Hwa Yao and Petrik Clarberg and Lucy Chen and Simon Kallweit and Tim Foley and Matthew Oakes and Conor Lavelle and Chris Wyman},
   title =       {The {Falcor} Rendering Framework},
   year =        {2020},
   month =       {03},
   url =         {https://github.com/NVIDIAGameWorks/Falcor},
   note=         {\url{https://github.com/NVIDIAGameWorks/Falcor}}
}
```

