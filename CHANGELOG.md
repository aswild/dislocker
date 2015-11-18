# v0.4.1
This version is only used to update dislocker's brew file for OSX users
to be able to download v0.4. If you're not an OSX user, you can use either v0.4
or v0.4.1, this won't make any difference.

# v0.4
- Bugfixes:
    - Installation process is now ok;
    - Various crashes have been fixed;
    - Some minor display errors have been fixed.

- Features improvement:
    - Adding of the write capability on some Windows 8 encrypted volumes;
    - Stealth password and recovery key in `ps' output;
    - Adding `--stateok' argument to tell dislocker not to check for the BitLocker
    volume state - as in 'partially decrypted', 'partially encrypted', and so on:
        - One can read partially encrypted volumes now!

- Notable changes:
    - A brew file is now available for OSX users;
    - The embedded PolarSSL library has been removed, due to licensing problems
      when packaging, so users need to install PolarSSL on their own now - see
      INSTALL.md for hints on how to do it;
    - The core part is now a library - dynamic shared object or dynamic library,
      depending on the OS - and four binaries are now using this library.
        - The library is not yet for use by other developers, its interface is not
          well enough defined yet.
        - The NOTE part of the README.md/INSTALL.md files lists these binaries.

- Portability:
    - Support added for FreeBSD.


# v0.3
- Bugfixes:
    - One can now read from a device from /dev;
        - The stat() syscall returns a *null size* (0) for these devices and
          dislocker used this size to tell the partition's size, which induced to
          present a zero-length NTFS file hence this bug.
    - Code cleaned and reorganised (yes, it's a bugfix);
    - Better BitLocker's files handling. This is not optimal yet, as it should
      involve the NTFS layer, which is currently completely dislocker-independant.

- Features improvement:
    - One can write on a BitLocker encrypted volume;
    - Adding `--readonly' argument to deny writes on the BitLocker volume;
    - Adding `--fvek' argument to decrypt a volume directly from a specially
      crafted FVEK file;
    - Default verbosity to CRITICAL level instead of QUIET, hence the `--quiet'
      option has been added;
    - One can use a user password to decrypt a volume through the
      '--user-password' option now.

- Notable changes:
    - OpenSSL is no longer used for decryption (and encryption). An embedded
      PolarSSL code is compiled along with the rest of Dislocker.


# v0.2
- Features improvement:
    - Now also able to decrypt/read BitLocker encrypted partitions from Windows
      Vista;
    - Better arguments handling (added verbosity and logging redirection);
    - Now able to pass an offset for the beginning of the partition (useful when
      all the disk has been copied instead of the partition);
    - Rules added into the Makefile: "make file" and "make fuse" to make binaries
      for using with FUSE or decrypting in a different file.

- Portability:
    - Support added for MacOSX (using osxfuse, tested on Snow Leopard).


# v0.1
- Features:
    - Decrypt BitLocker encrypted partitions from Windows 7 only;
    - A FUSE module is available for reading partitions;
    - Possibility to decrypt the entire partition into a file.