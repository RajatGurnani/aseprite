https://github.com/aseprite/aseprite/blob/master/INSTALL.md

instructions taken from above, but a complete summary specifically for windows (in the right order) is below

1. download [cmake](https://cmake.org/) and install it
2. download [ninja](https://ninja-build.org/) and install it
3. download [Visual Studio Community 2019](https://visualstudio.microsoft.com/downloads/)
4. install Visual Studio Community 2019 with the "Desktop development with C++ item", ensuring "Windows 10.0.18362.0 SDK" is selected
![](https://i.imgur.com/lnW0x5L.png)
5. download latest [pre-built skia library (aseprite branch)](https://github.com/aseprite/skia/releases)
6. extract the skia library to a directory (e.g. `C:\deps\skia`) (make note of this directory*)
7. clone repo, create build directory, create the build files, build it, with these commands:
  ```
  # clone the repository (assuming you have git installed)
  git clone --recursive https://github.com/aseprite/aseprite.git
  call "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat" -arch=x64
  # open the repository
  cd aseprite
  # create a build directory
  mkdir build
  # open the build diretory
  cd build
  # create build files. NOTE: replace `C:\deps\skia` (3x) in the command below with the directory you created above*
  cmake -DCMAKE_BUILD_TYPE=RelWithDebInfo -DLAF_BACKEND=skia -DSKIA_DIR=C:\deps\skia -DSKIA_LIBRARY_DIR=C:\deps\skia\out\Release-x64 -DSKIA_LIBRARY=C:\deps\skia\out\Release-x64\skia.lib -G Ninja ..
  # build it
  ninja aseprite
  ```
8. open the aseprite executable in the bin folder
![](https://i.imgur.com/WhR8IIP.png)


cmake command for install
'''
cmake -DCMAKE_BUILD_TYPE=RelWithDebInfo -DLAF_BACKEND=skia -DSKIA_DIR=D:\Downloads\Skia-Windows-Release-x64 -DSKIA_LIBRARY_DIR=D:\Downloads\Skia-Windows-Release-x64\out\Release-x64 -DSKIA_LIBRARY=D:\Downloads\Skia-Windows-Release-x64\out\Release-x64\skia.lib -G Ninja ..
'''
