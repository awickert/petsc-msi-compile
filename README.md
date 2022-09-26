# petsc-msi-compile

Guidance from @KCallaghan

## Get PETSc
```sh
# Get PETSc
git clone -b release https://gitlab.com/petsc/petsc.git petsc
```

## Configure PETSc

I tried to configure with --with-cc=gcc, but this failed with the following message:

```
PETSc requires c99 compiler! Configure could not determine compatible compiler flag.
Perhaps you can specify it via CFLAGS.
Perhaps you have an Intel compiler environment or module set that is interferring with the GNU compilers.
Try removing that environment or module and running ./configure again.
```

Instead of removing that environment, I just used --with-cc=c99. Hopefully that's not too bad.
```sh
./configure --with-cc=c99 --with-fc=gfortran --with-cxx=g++ --with-clanguage=cxx --download-fblaslapack --download-mpich --force
```

This then returned:
```
=============================================================================================
                         Configuring PETSc to compile on your system                         
=============================================================================================

=============================================================================================
WARNING -with-clanguage=C++ is a developer feature and is *not* required for regular usage of PETSc either from C or C++
=============================================================================================
=============================================================================================
***** WARNING: You have a version of GNU make older than 4.0. It will work,
but may not support all the parallel testing options. You can install the
latest GNU make with your package manager, such as brew or macports, or use
the --download-make option to get the latest GNU make *****
=============================================================================================
=============================================================================================
Trying to download https://www.mpich.org/static/downloads/4.0.1/mpich-4.0.1.tar.gz for MPICH
=============================================================================================
=============================================================================================
Trying to download http://ftp.mcs.anl.gov/pub/petsc/externalpackages/mpich-4.0.1.tar.gz for MPICH
=============================================================================================
=============================================================================================
Running configure on MPICH; this may take several minutes
=============================================================================================
=============================================================================================
Running make on MPICH; this may take several minutes
=============================================================================================
```

Based on the GNU message, I am currently thinking of simply removing that `./configure` flag.
