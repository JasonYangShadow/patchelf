PatchELF is a simple utility for modifying existing ELF executables and
libraries.  In particular, it can do the following:

* Change the dynamic loader ("ELF interpreter") of executables:

  $ patchelf --set-interpreter /lib/my-ld-linux.so.2 my-program

* Change the RPATH of executables and libraries:

  $ patchelf --set-rpath /opt/my-libs/lib:/other-libs my-program

* Shrink the RPATH of executables and libraries:

  $ patchelf --shrink-rpath my-program

  This removes from the RPATH all directories that do not contain a
  library referenced by DT_NEEDED fields of the executable or library.
  For instance, if an executable references one library libfoo.so, has
  an RPATH "/lib:/usr/lib:/foo/lib", and libfoo.so can only be found
  in /foo/lib, then the new RPATH will be "/foo/lib".

  In addition, the '--allowed-rpath-prefixes' option can be used for
  further rpath tuning. For instance, if an executable has an RPATH
  "/tmp/build-foo/.libs:/foo/lib", it is probably desirable to keep
  the "/foo/lib" reference instead of the "/tmp" entry. To accomplish
  that, use:

  $ patchelf --shrink-rpath --allowed-rpath-prefixes /usr/lib:/foo/lib my-program

* Remove declared dependencies on dynamic libraries (DT_NEEDED
  entries):

  $ patchelf --remove-needed libfoo.so.1 my-program

  This option can be given multiple times.

* Add a declared dependency on a dynamic library (DT_NEEDED):

  $ patchelf --add-needed libfoo.so.1 my-program

  This option can be give multiple times.

* Replace a declared dependency on a dynamic library with another one
  (DT_NEEDED):

  $ patchelf --replace-needed liboriginal.so.1 libreplacement.so.1 my-program

  This option can be give multiple times.

* Change SONAME of a dynamic library:

  $ patchelf --set-soname libnewname.so.3.4.5 path/to/libmylibrary.so.1.2.3
  

INSTALLING

You can download a pre-compiled binary from the releases or compile it by yourself:

  ./bootstrap.sh
  ./configure
  make

**After executing make command, you could find patchelf binary under src folder, you then copy it to the folder containing lpmx program. lpmx will automatically copy patchelf into target container during starting container.**

