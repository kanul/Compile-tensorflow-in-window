# Compile-tensorflow-in-window

Ref1] https://github.com/tensorflow/tensorflow/blob/master/tensorflow/contrib/cmake/README.md

Ref2] http://blog.naver.com/atelierjpro/220830797975

Ref3] http://stackoverflow.com/questions/23497304/vs-2013-and-msbuild

Ref4] http://blog.naver.com/atelierjpro/220830743694

Ref5] http://www.kunal-chowdhury.com/2015/07/download-visualstudio-2015.html#ZqbX2gycoVlEX1g4.97

Recccomand] Apperently my Anti-Virus was the problem. When I turned it off my installation worked.

1. Pre-requisites

Windows7

CMake version 3.5 or later.

Git

SWIG

Additional pre-requisites for Microsoft Windows:

Visual Studio 2015

Python 3.5

NumPy 1.11.0 or later

2. Environment variable

F:\Program\Tensorflow\cmake-3.8.1-win64-x64\cmake-3.8.1-win64-x64\bin

3. Command

(1) Install the pre-requisites detailed above, and set up your environment.

The following commands assume that you are using the Windows Command Prompt (cmd.exe). You will need to set up your environment to use the appropriate toolchain, i.e. the 64-bit tools. (Some of the binary targets we will build are too large for the 32-bit tools, and they will fail with out-of-memory errors.) The typical command to do set up your environment is:

"C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"

"C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\bin\amd64\vcvars64.bat"

(2) Clone the TensorFlow repository and create a working directory for your build:

D:\temp> git clone https://github.com/tensorflow/tensorflow.git

D:\temp> cd tensorflow\tensorflow\contrib\cmake

D:\temp\tensorflow\tensorflow\contrib\cmake> mkdir build

D:\temp\tensorflow\tensorflow\contrib\cmake> cd build

D:\temp\tensorflow\tensorflow\contrib\cmake\build>

(3) Invoke CMake to create Visual Studio solution and project files.

D:\...\build> cmake .. -A x64 -DCMAKE_BUILD_TYPE=Release 
-DSWIG_EXECUTABLE="E:\Program\Tensorflow\swigwin-3.0.10\swigwin-3.0.10\swig.exe" 
-DPYTHON_EXECUTABLE="C:\Users\kanul\Anaconda3\python.exe" 
-DPYTHON_LIBRARIES="C:\Users\kanul\Anaconda3\libs\python35.lib"

(4) Invoke MSBuild to build TensorFlow.

To build the C++ example program, which will be created as a .exe executable in the subdirectory .\Release:

D:\...\build> MSBuild /p:Configuration=Release tf_tutorials_example_trainer.vcxproj

D:\...\build> Release\tf_tutorials_example_trainer.exe

D:\...\build> MSBuild /p:Configuration=Release tf_python_build_pip_package.vcxproj
