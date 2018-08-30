title:  Dependencies
author: Jabir Ali Ouassou
date:   2016-04-13



The only thing that is *really* necessary to compile the project, would be a
compiler that supports the Fortran standards from 1977 to 2008. But for your
own convenience, it is strongly recommended that you have these available:

 * [CMake](https://cmake.org/) (2.6+):
   a free, open-source, and cross-platform build system that automates the compilation details.
 * [GFortran](https://gcc.gnu.org/wiki/GFortran) (5.0+):
   a free, open-source, and cross-platform Fortran compiler from the GNU Compiler Collection.
 * [IFort](https://software.intel.com/en-us/fortran-compilers) (16.0+):
   a commercial Fortran compiler developed by Intel, with free licenses for 
   [students](https://software.intel.com/en-us/qualify-for-free-software/student) and
   [academics](https://software.intel.com/en-us/qualify-for-free-software/academicresearcher).

The code was last verified to work with the compilers GFortran 5.4.0, GFortran 6.2.1, and 
IFort 17.0.1. Older versions than GFortran 5.0 and IFort 16.0 *may* or *may not* work;
older versions of the code worked fine with GFortran 4.9, but I haven't tested recently.

IFort generates much faster binaries than GFortran; for these programs, we're talking
about a speedup of ~4x on an Intel Core i7 processor. I am not really sure if this due
to better vectorization, more aggressive inter-procedural optimizations, or something
else. But the bottom line is that if you do have access to an IFort licence, I strongly
recommend using it. But if not, I *have* also tested the code extensively using only the
free/open-source tools CMake and GFortran, so no proprietary tools should be necessary.

Note that albeit slower, the binaries generated by GFortran can sometimes be more
stable than the ones generated by IFort. In many cases, this is just caused by
the IFort binaries placing more variables on the stack than the GFortran binaries;
in that case, the problem goes away by running the command `ulimit -s unlimited`
to increase the stack size (assuming a Linux/Unix system with a Bourne-based shell).
If this doesn't work, please send a bug report, and try GFortran in the mean time.

There are also some more optional dependencies:

 * [Gnuplot](http://www.gnuplot.info/) can be used to plot the results generated by my
   simulation programs. But it should be straight-forward to import the generated data
   files to e.g. Matlab or R instead if you prefer that.
 * [FORD](https://github.com/cmacmackin/ford) can be used to autogenerate documentation
   for modern Fortran projects, including this one. This should be installed if you plan
   to modify the source code, and wish to automatically update documentation accordingly.