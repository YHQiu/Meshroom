# ![Meshroom - 3D Reconstruction Software](/docs/logo/banner-meshroom.png)

[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/2997/badge)](https://bestpractices.coreinfrastructure.org/projects/2997)

Meshroom is a free, open-source 3D Reconstruction Software based on the [AliceVision](https://github.com/alicevision/AliceVision) Photogrammetric Computer Vision framework.

Learn more details about the pipeline on [AliceVision website](http://alicevision.github.io).

See [results of the pipeline on sketchfab](http://sketchfab.com/AliceVision).

Continuous integration:
* Windows: [![Build status](https://ci.appveyor.com/api/projects/status/25sd7lfr3v0rnvni/branch/develop?svg=true)](https://ci.appveyor.com/project/AliceVision/meshroom/branch/develop)
* Linux: [![Build Status](https://travis-ci.org/alicevision/meshroom.svg?branch=develop)](https://travis-ci.org/alicevision/meshroom)


## Photogrammetry

Photogrammetry is the science of making measurements from photographs.
It infers the geometry of a scene from a set of unordered photographs or videos.
Photography is the projection of a 3D scene onto a 2D plane, losing depth information.
The goal of photogrammetry is to reverse this process.

See the [presentation of the pipeline steps](http://alicevision.github.io/#photogrammetry).


## Manual

https://meshroom-manual.readthedocs.io


## Tutorials

* [Meshroom: Open Source 3D Reconstruction Software](https://www.youtube.com/watch?v=v_O6tYKQEBA) by [Mikros Image](http://www.mikrosimage.com)

Overall presentation of the Meshroom software.

* [Meshroom Tutorial on Sketchfab](https://sketchfab.com/blogs/community/tutorial-meshroom-for-beginners) by [Mikros Image](http://www.mikrosimage.com)

Detailed tutorial with a focus on the features of the 2019.1 release.

* [Photogrammetry 2 – 3D scanning with just PHONE/CAMERA simpler, better than ever!](https://www.youtube.com/watch?v=1D0EhSi-vvc) by [Prusa 3D Printer](https://blog.prusaprinters.org)

Overall presentation of the photogrammetry practice with Meshroom.

* [How to 3D Photoscan Easy and Free! by ](https://www.youtube.com/watch?v=k4NTf0hMjtY) by [CG Geek](https://www.youtube.com/channel/UCG8AxMVa6eutIGxrdnDxWpQ)

Overall presentation of the protogrammetry practice with Meshroom and detailed presentation how to do the retolopogy in Blender.

* [Meshroom Survival Guide](https://www.youtube.com/watch?v=eiEaHLNJJ94) by [Moviola](https://moviola.com)

Presentation of the Meshroom software with a focus on using it for Match Moving.


## Customization

### Custom Pipelines

You can create custom pipelines in the user interface and save it as template: `File > Advanced > Save As Template`.
You can define the `MESHROOM_PIPELINE_TEMPLATES_PATH` environment variable to specific folders to make these pipelines available in Meshroom.
In a standard precompiled version of Meshroom, you can also directly add custom pipelines in `lib/meshroom/pipelines`.

### Custom Nodes

You can create custom nodes in python and make them available in Meshroom using the `MESHROOM_NODES_PATH` environment variable.
[Here is an example](meshroom/nodes/blender/ScenePreview.py) to launch a Blender rendering from Meshroom.
In a standard precompiled version of Meshroom, you can also directly add custom nodes in `lib/meshroom/nodes`.
To be recognized by Meshroom, a custom folder with nodes should be a Python module (an `__init__.py` file is needed).


## License

The project is released under MPLv2, see [**COPYING.md**](COPYING.md).


## Citation

If you use this project for a publication, please cite the [paper](https://hal.archives-ouvertes.fr/hal-03351139):
  ```
  @inproceedings{alicevision2021,
    title={{A}liceVision {M}eshroom: An open-source {3D} reconstruction pipeline},
    author={Carsten Griwodz and Simone Gasparini and Lilian Calvet and Pierre Gurdjos and Fabien Castan and Benoit Maujean and Gregoire De Lillo and Yann Lanthony},
    booktitle={Proceedings of the 12th ACM Multimedia Systems Conference - {MMSys '21}},
    doi = {10.1145/3458305.3478443},
    publisher = {ACM Press},
    year = {2021}
  }
  ```

## Get the project

You can [download pre-compiled binaries for the latest release](https://github.com/alicevision/meshroom/releases).  

If you want to build it yourself, see [**INSTALL.md**](INSTALL.md) to setup the project and pre-requisites.

Get the source code and install runtime requirements:
```bash
git clone --recursive git://github.com/alicevision/meshroom
cd meshroom
pip install -r requirements.txt
```


## Start Meshroom

You need to have [AliceVision](https://github.com/alicevision/AliceVision) installation in your PATH (and LD_LIBRARY_PATH on Linux/macOS).

```bash
PRE:构建AliceVision以用于Meshroom的一般步骤。请按照以下指南进行操作：

1. 首先，确保你已经安装了必要的构建工具和依赖项。这些包括CMake、GCC、Git和一些图像处理库（例如OpenCV和Boost）等。你可以使用包管理器（如apt、yum或brew）来安装这些依赖项。

2. 下载AliceVision的源代码。你可以通过使用Git命令克隆AliceVision的存储库来完成此操作。在终端中执行以下命令：

   ```shell
   git clone https://github.com/alicevision/AliceVision.git
   ```

3. 进入AliceVision的源代码目录：

   ```shell
   cd AliceVision
   ```

4. 创建一个用于构建的目录（通常称为`build`目录）：

   ```shell
   mkdir build
   cd build
   ```

5. 使用CMake生成构建配置。运行以下命令：

   ```shell
   cmake -DALICEVISION_BUILD_DEPENDENCIES=ON -DCMAKE_INSTALL_PREFIX=$PWD/../install ../
   
   ```

   这将根据你的系统和安装的依赖项生成构建配置。

6. 编译AliceVision。运行以下命令：

   ```shell
   make -j10
   ```

   这将编译AliceVision的源代码并生成可执行文件和库文件。

7. 安装AliceVision。运行以下命令：

   ```shell
   sudo make install
   ```

   这将安装AliceVision到系统中，使其可供其他应用程序（如Meshroom）使用。

完成上述步骤后，你就成功构建了AliceVision，并可以将其用于Meshroom。请注意，构建AliceVision可能需要一些时间，具体取决于你的系统性能和网络连接速度。如果在构建过程中遇到任何错误，请检查错误信息并尝试解决它们（通常需要安装缺少的依赖项或解决配置问题）。
```

- __Launch the User Interface__

```bash
# Windows
set PYTHONPATH=%CD% && python meshroom/ui
# Linux/macOS
PYTHONPATH=$PWD python meshroom/ui
```

On Ubuntu, you may have conflicts between native drivers and mesa drivers. In that case, you need to force usage of native drivers by adding them to the LD_LIBRARY_PATH:
`LD_LIBRARY_PATH=/usr/lib/nvidia-340 PYTHONPATH=$PWD python meshroom/ui`
You may need to adjust the folder `/usr/lib/nvidia-340` with the correct driver version.

- __Launch a 3D reconstruction in command line__

```bash
# Windows: set PYTHONPATH=%CD% &&
# Linux/macOS: PYTHONPATH=$PWD
python bin/meshroom_batch --input INPUT_IMAGES_FOLDER --output OUTPUT_FOLDER
```

## Start Meshroom without building AliceVision

To use Meshroom (ui) without building AliceVision
````bash
mkdir extensions
cd extensions
````
*   Download a [release](https://github.com/alicevision/meshroom/releases) to extensions
````bash
ln -s Meshroom-2023.2.0-av3.1.0-centos7-cuda11.3.1/ Meshroom-2023.2.0
````
*   Checkout corresponding Meshroom (ui) version/tag to avoid versions incompatibilities
*   `LD_LIBRARY_PATH=./extensions/Meshroom-2023.2.0/aliceVision/lib/ PATH=$PATH:./extensions/Meshroom-2023.2.0/aliceVision/bin/ python3 meshroom/ui`

## Start and Debug Meshroom in an IDE

PyCharm Community is free IDE which can be used. To start and debug a project with that IDE,
right-click on `Meshroom/ui/__main__.py` > `Debug`, then `Edit Configuration`, in `Environment variables` : 
*   If you want to use aliceVision built by yourself add: `PATH=$PATH:/foo/build/Linux-x86_64/`
*   If you want to use aliceVision release add: `LD_LIBRARY_PATH=/foo/Meshroom-2023.2.0/aliceVision/lib/;PATH=$PATH:/foo/Meshroom-2023.2.0/aliceVision/bin/` (Make sure that you are on the branch matching the right version)

![image](https://user-images.githubusercontent.com/937836/127321375-3bf78e73-569d-414a-8649-de0307adf794.png)


## FAQ

See the [Meshroom wiki](https://github.com/alicevision/meshroom/wiki) for more information.


## Contact

Use the public mailing-list to ask questions or request features. It is also a good place for informal discussions like sharing results, interesting related technologies or publications:
> [alicevision@googlegroups.com](mailto:alicevision@googlegroups.com)
> [http://groups.google.com/group/alicevision](http://groups.google.com/group/alicevision)

You can also contact the core team privately on: [alicevision-team@googlegroups.com](mailto:alicevision-team@googlegroups.com).
