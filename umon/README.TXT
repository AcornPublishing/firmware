***************   Embedded Systems Firmware Demystified README  **************

This is the README file for the MicroMonitor portion of the 
"Embedded Systems Firmware Demystified" book.                      

The intent of this distribution is to support the text of the book and to
generate some discussion on the MicroMonitor boot platform.
Feedback to the author in the form of bug reports or enhancements may
generate new versions of the platform.  The goal is to keep the "common"
code common and put all target specific code in the target-specific directory.
This will allow future versions (including enhancements and/or fixes) to
be reusable by those interested.

Lucent is providing this "AS-IS", meaning that there are absolutely no
guarantees of any kind regarding advertised functionality.  Please feel
free to email the author, but realize that there is no formal support.
  
*******************************************************************************

MICRO-MONITOR PLATFORM INSTALLATION:

1. At START-RUN type:   D:\umon\install (where 'D' is the drive in which the 
   "Embedded Systems Firmware Demystified" CD is currently installed).
   The installation process will ask you for a destination directory to place
   all of the monitor source code and html files.  It is set up to force you
   to install into a new directory.  This is done so that it is a simple
   removal of that directory for uninstallation. 
  
2. At this point the package is installed.  If you want to informally browse
   the source, you can browse the .c.html files under the installed src
   directory.  Or you can install the real source from the .tar file also in
   the src directory.  The important thing to realize is that the
   subdirectories under src of the installed package contain "html-ized"
   source (.c.html).  To extract the "real" source, un-tar the content of
   micromon.tar (in the src directory) to some other new directory
   (say... realsrc).  See notes below regarding source code.
   Also, the toolsrc.tar file contains the source code for all the monitor
   support tools, so that too, can be installed in some new directory under
   the package.
     

*******************************************************************************

GETTING STARTED:

1. Point your browser to index.html in the installation destination directory
   and start reading.

2. The monitor source code is "html"ized under the src directory so that it
   can be viewed with a browser, but there is also a micromon.tar.gz file that
   contains the actual source.  

3. The source code for the host-based tools is in the file toolsrc.tar and
   contains source for the most of the PC-based tools that are used in
   conjunction with the monitor

*******************************************************************************

WHAT IS IN THIS PACKAGE?

   The package includes source code for building the monitor package, plus 
   source code to build the host-based (primarily PC, but some SOLARIS) tools
   that work with the monitor once it is installed on a target.
   The index.html page is the opening, or top-level, page that provides a good
   amount of overview as well as a full set of manual pages for the API that
   the monitor presents to the application and the command set that the monitor
   presents to the console port.

*******************************************************************************

INSTALLING MICROCROSS TOOLS:

    Refer to the top level of the CD and follow MicroCross-specific
    installation instructions.

*******************************************************************************

INSTALLING MONITOR-SPECIFIC HOST-BASED TOOLS:

    Nothing to install here, just copy the .exe files under tools/win95
    to some directory in your PATH, or add tools/win95 to your PATH.

*******************************************************************************

NOTE REGARDING THE SOURCE CODE...

 *  All of the source code has been edited with "vi" using 4-space tabs.
    You would be wise to start browsing the code with your editor configured
    in a similar way; otherwise, it will look quite out of shape! 

 *  Prior to being able to sucessfully run a clean build, you must install
    the MicroCross tools and the monitor-specific tools into your PATH.
    For each target/XXX/monitor directory (where XXX is the name of the target)
    there is a file called .bashrc.  This is a bash shell run-control file.
    Its purpose is similar in to a .profile (UNIX) or an autoexec.bat (DOS)
    file in that it establishes an environment for bash to run in.  This 
    environment is assumed to be installed when the make files are run, so
    either run the script or include it in some shortcut (see note below).

 *  Some of the target-specific make files assume that you first run
    "make cscope" so that a tags file can be built for use by ctags.

*******************************************************************************

CREATING A BASH SHORTCUT THAT WILL AUTOMATICALLY RUN .bashrc...

 *  For NT, copy some shortcut already on your desktop to another one that
    can be edited.  Then, right click on the copy of the short cut and
    click on properties.  Set the "Target" field to:

        D:\Cygwin\bin\bash.exe -rcfile .bashrc

    The actual path used is dependent on where you install bash.  Set the
    "Start In:" field to:

        D:/umondir/targets/eval5272/monitor

    The actual path used here is dependent on the target and the place
    you installed the monitor source code.
    The point is that after having set this up, you can simply click on a
    short cut and the bash shell will be started and the .bashrc file will
    automatically be run when bash starts up.