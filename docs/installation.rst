Installation
============

The entire GALAMOST package is a Free Software under the GNU General Public License. The package is mainly distributed as source code and binary program. 
The binary program and the code can be downloaded from our website http://galamost.ciac.jl.cn/
Here is the guide for installation by code. Before compiling and installing of source code, you should configure compiling system firstly, i.e. installation path

   Examples::

      ./configuration --prefix=/opt/galamost3
	 
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

After configuration, a Makefile file will be generated in your current directory. Then you can compile and install the package

   Examples::
   
      make install -j4 
      # where -j indicates the number of threads to compile the code.


