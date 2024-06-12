# LOD Real-time Viewer for LetsGo

## LetsGo: Large-Scale Garage Modeling and Rendering via LiDAR-Assisted Gaussian Primitives
Jiadi Cui*, Junming Cao*, Fuqiang Zhao*, Zhipeng He, Yifan Chen, Yuhui Zhong, Lan Xu, Yujiao Shi, Yingliang Zhang†, Jingyi Yu†

[Project page](https://zhaofuq.github.io/LetsGo/) | [Paper](https://arxiv.org/pdf/2404.09748) | [Video](https://www.youtube.com/watch?v=fs42UBKvGRw) | [LOD Viewer (SIBR)](https://zhaofuq.github.io/LetsGo/) | [Web Viewer](https://zhaofuq.github.io/LetsGo/)| [GarageWorld Dataset](https://zhaofuq.github.io/LetsGo/) <br>


## Setup

**Note**: The current release is for *Windows 10* only. 

#### Install requirements

- [**Visual Studio 2019**](https://visualstudio.microsoft.com/fr/downloads/)
- [**Cmake 3.16+**](https://cmake.org/download)
- [**7zip**](https://www.7-zip.org)
- [**Python 3.8+**](https://www.python.org/downloads/) for shaders installation scripts and dataset preprocess scripts
- [**Doxygen 1.8.17+**](https://www.doxygen.nl/download.html#srcbin) for documentation
- [**CUDA 10.1+**](https://developer.nvidia.com/cuda-downloads) and [**CUDnn**](https://developer.nvidia.com/cudnn) if projects requires it

Make sure Python, CUDA and Doxygen are in the PATH


#### Clone the repo

Checkout this repository's main branch:
  
```sh
## through HTTPS
git clone https://github.com/zhaofuq/LOD-SIBR-Viewer.git -b main
## through SSH
git clone git@github.com:zhaofuq/LOD-SIBR-Viewer.git -b main
```


#### Compilation

```sh
cd LOD-SIBR-Viewer
cmake . -B build
cmake --build build --target install --config RealWithDebInfo
```

## To run an example
For more details, please see the official documentation: http://sibr.gitlabpages.inria.fr

```sh
./install/bin/SIBR_gaussianViewer_app_rwdi.exe -m <path to model path> --dmax <max depth value>
```

# Citation
If you find our code or paper helps, please consider citing:
<section class="section" id="BibTeX">
  <div class="container is-max-desktop content">
    <pre><code>@article{cui2024letsgo,
        title={LetsGo: Large-Scale Garage Modeling and Rendering via LiDAR-Assisted Gaussian Primitives},
        author={Jiadi Cui, Junming Cao, Fuqiang Zhao, Zhipeng He, Yifan Chen, Yuhui Zhong, Lan Xu, Yujiao Shi, Yingliang Zhang, Jingyi Yu},
        journal={arXiv preprint arXiv:2404.09748},
        year={2024}
    }
</code></pre>
  </div>
</section>

## Troubleshooting

#### Bugs and Issues

We will track bugs and issues through the Issues interface on gitlab. Inria gitlab does not allow creation of external accounts, so if you have an issue/bug please email <code>sibr@inria.fr</code> and we will either create a guest account or create the issue on our side.

#### Cmake complaining about the version

if you are the first to use a very recent Cmake version, you will have to update `CHECKED_VERSION` in the root `CmakeLists.txt`.

#### Weird OpenCV error

you probably selected the 32-bits compiler in Cmake-gui.

#### `Cmd.exe failed with error 009` or similar

make sure Python is installed and in the path. 

#### `BUILD_ALL` or `INSTALL` fail because of a project you don't really need

build and install each project separately by selecting the proper targets.

#### Error in CUDA headers under Visual Studio 2019

make sure CUDA >= 10.1 (first version to support VS2019) is installed.

# Acknowledgements

**SIBR** is a System for Image-Based Rendering.  
It is built around the *sibr-core* in this repo and several *Projects* implementing published research papers.  
For more complete documentation, see here: [SIBR Documentation](https://sibr.gitlabpages.inria.fr) 
  
This **SIBR core** repository provides :
- a basic Image-Based Renderer
- a per-pixel implementation of Unstructured Lumigraph (ULR)
- several dataset tools & pipelines do process input images

```
@misc{sibr2020,
   author       = "Bonopera, Sebastien and Esnault, Jerome and Prakash, Siddhant and Rodriguez, Simon and Thonat, Theo and Benadel, Mehdi and Chaurasia, Gaurav and Philip, Julien and Drettakis, George",
   title        = "sibr: A System for Image Based Rendering",
   year         = "2020",
   url          = "https://gitlab.inria.fr/sibr/sibr_core"
}
```