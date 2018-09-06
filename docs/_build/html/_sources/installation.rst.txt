Installation
============

Source code
-----------

The entire GALAMOST package is a Free Software under the GNU General Public License. The package is mainly distributed as source code and binary program. 
The code and binary program can be downloaded from our website http://galamost.ciac.jl.cn/. At present, only Linux operating systems are supported.
Here is the guide for installation by code. Before compiling and installing of source code, you should configure compiling system firstly, i.e. installation path, by ``configure``.

   Examples::

      ./configure --prefix=/opt/galamost3
	 
More configuration commands are given here:

============   ==========================   =======================
Commands       Functions                    Examples
============   ==========================   =======================
--prefix=      installation path            --prefix=/opt/galamost3
--cuda_arch=   compute capability of GPU    --cuda_arch=20
--precision=   precision format             --precision=double
--gprof=       profiling tool               --gprof=on
--gdb=         gdb tool                     --gdb=on
--cuda=        the path of CUDA toolkit     --cuda=/usr/local/cuda
--boost=       the path of boost library    --boost=/usr
--python=      the path of Python program   --python=/usr
============   ==========================   =======================

The compute capability of some NVIDIA GPU is listed. For more please visit https://developer.nvidia.com/cuda-gpus.

===================   ==================
GPUs                  Compute Capability
===================   ==================
Tesla V100            70
Tesla P100            60
Tesla P40             61
Tesla P4              61 
NVIDIA TITAN V        70 
NVIDIA TITAN Xp       61
NVIDIA TITAN X        61 
GeForce GTX 1080 Ti   61
===================   ==================

After configuration, a Makefile file will be generated in your current directory. Then you can compile and install the package  by ``make install``.

   Examples::
   
      make install -j4 
      # where -j indicates the number of threads to compile the code.

Binary program
--------------

The GALAMOST also can be installed by a compiled binary file which includes dependent libaries except CUDA libray.
The ``.rpm`` or ``.deb`` files corresponding to the CUDA version in your machine can be downloaded from our 
website http://galamost.ciac.jl.cn/.

1. Redhat Package Manager (RPM) file for Redhat, Fedora, and Suse Linux operating system.

   * Installation command, for example::
   
      rpm -ivh galamost-3.1.0-0.x86_64-cuda8.0.rpm
   
   * The environment variable for library files, for example::
   
      echo 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/galamost3/lib' >> /etc/profile
      source /etc/profile
   
   * Uninstallation command::
   
      rpm -e galamost

2. Debian (DEB) file for Ubuntu and Debian Linux operating system.

   * Installation command, for example::
   
      sudo dpkg -i galamost-3.1.0-0.x86_64-cuda8.0.deb
   
   * The environment variable for library files, for example::
   
      echo 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/galamost3/lib' >> /etc/profile
      source /etc/profile
   
   * Uninstallation command::
   
      dkpg -r galamost
