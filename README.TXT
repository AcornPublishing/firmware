
README for "Embedded Systems Firmware Demystified Companion CD"

This CD contains two separate packages:

 1. Microcross GNU X-Tools cross compilation package
    and UNIX environment for Windows.
 2. Micromonitor package.

Each of these packages is installed separately, and for best
results, should be done in the suggested order...

**********************************************************************

INSTALLATION STEPS:

Assume X: is the drive on your PC that contains this CD)
Assume C:\cygwin is the directory onto which you install Microcross
Assume C:\umon is the directory onto which you install MicroMonitor

1. Run X:\setup (see note below) to install the Microcross GNU X-Tools
   package.  This will startup a program that will allow you to install...

     a: The Cygwin B-20 Bash shell and UNIX tools;

     b: A short-cut to the bash shell for your desktop;

     c: Cross-compilation packages for several different CPUs;

     d: An IDE front end for the development environment;

   As a minimum, install Cygwin B-20, the short-cut and at least one
   cross-compilation package.

   NOTE: on some older versions of Microsoft OSes, it may be necessary
   to run X:\osetup instead of X:\setup to install.

2. Change directory to X:\umon and click on install.  This will start
   up a program that will transfer (and convert) files from the CD to
   a directory that you specify on your hard drive.  This text
   assumes the installation destination to be C:\umon.
   NOTE that the install program automatically does some conversion
   of the *.c.html files so that they properly reference each other
   through a browser.  This means that direct access of the .html
   stuff on the CD will not be able to correctly browse through
   the html-ized source code.

3. At this point all packages are installed.  To start browsing the
   Micromonitor html pages, have your browser open up the file:
   C:\umon\index.html.  This is the opening page for the monitor and
   contains a lot of descriptive text, plus a complete user manual for
   the monitor's API and command set.
   The package includes a version of the source code that is viewable
   through your browser; however, if you want the real source, it
   needs to be installed.

4. Installing real monitor source:

   a. Create the directory C:\umon\realsrc.

   b. At your browser, click on the "Source Code Available?" hyperlink
      (you may have to scroll down just a bit to see this link).

   c. At this point you will see a basic description of the source tree,
      plus another hyperlink to a tar file that contains the source.

   d. Click on that link, and save the .tar file to C:\umon\realsrc.

   e. Now click on the Microcross short cut and cd to //c/umon/realsrc
      (this shell presents a UNIX-like environment, so C: becomes //c
      and backslash becomes slash).  Type "tar -xvf micromon.tar".
      This will extract the Micromonitor source code to the directory
      structure (beneath realsrc) specified in the html page.

5. Cross-compiling the ColdFire 5272 Evaluation board (for example)
   package:
   This assumes that you've installed the m68k-coff cross-compilation
   package with the Microcross installer, if not, just run X:\setup
   again and install that package.

   a. Click on the MicroCross Cygwin B-20 shortcut.

   b. Establish the following environment:

      export TOOLDIR=/usr
      export TARGET=m68k-coff
      export MAKE_MODE=UNIX
      PATH=$PATH://c/umon/tools/win95
      PATH=$PATH://c/cygwin/usr/lib/gcc-lib/$TARGET/2.8.1
      PATH=$PATH://c/cygwin/usr/$TARGET/bin

   c. Change directory to //c/umon/realsrc/targets/eval5272/monitor:
         cd //c/umon/realsrc/targets/eval5272/monitor

   d. Create directory obj:
         mkdir obj

   e. Run 'make':
         make

**********************************************************************

CONVENIENT DESK-TOP SHORTCUT:

Create a short-cut that will automatically establish the environment
discussed in step # 5 of the installation instructions above...
Assume we are creating a short cut that will open up a bash console
window for development work on the ColdFire 5272 Eval-board monitor...

  1. Make a copy of some shortcut on your desktop.

  2. Right-click on that copy and rename it appropriately
     (say "UMON MCF5272")

  3. Right-click on it again and go to Properties.  In this box,
     set the content of the "Start in:" text box to

        C:\umon\realsrc\targets\eval5272\monitor

     and the content of the "Target:" text box to

        C:\cygwin\bin\bash.exe -rcfile .bashrc

  4. The .bashrc file in C:\umon\realsrc\targets\eval5272\monitor
     should be modified to contain the same environment as was set
     up in step # 5 of the installation.

  5. Now this shortcut can be run and it will automatically open up
     a command window running the bash shell with the environment
     properly configured.

  6. If you are building more than one target, duplicate these steps
     for several shortcuts.

