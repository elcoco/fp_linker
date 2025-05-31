## flatpak auto linker

Flatpak names are difficult to remember and running "flatpak run bla.bla.blabla" is hard.  
This script automatically creates symlinks for flatpak applications.  

Features:  
- Create sane symlinks to hard to remember flatpak binary names  
- Watch multiple directories for newly installed flatpaks and update links accordingly  
- Add an optional pre/postfix to link name to not pollute the namespace  

### Dependencies:  
    - https://pypi.org/project/watchdog

### Usage:

fp_linker tries to find binaries in the provided paths.  
The link name will be derived from the FQD flatpak name, eg:

    com.prusa3d.PrusaSlicer -> PrusaSlicer
    org.freecad.FreeCAD     -> FreeCAD

If the --to-lower flag is used, all link names will be converted to lower case only, eg:

    com.prusa3d.PrusaSlicer -> prusaslicer
    org.freecad.FreeCAD     -> freecad

fp_linker will by default look for flatpaks in the default locations.  
You can provide custom search locations with one or more --src-dir arguments.  
To keep watching the directories for changes, provide the --watch flag
    
    fp_linker --link-dir ~/path/to/links --watch

    --link-dir
        directory where links are placed
    --watch
        watch directories for changes

You can add the link directory to your $PATH so flatpaks are easy to launch from the terminal.  

### help

     > fp_linker --help
     usage: fp_linker [-h] [-w] -l LINK_DIR -s SRC_DIR [-p PREFIX] [-P POSTFIX] [-L] [-t NOTIFY_MS] [-D]

     Create links for flatpak apps

     options:
       -h, --help            show this help message and exit
       -w, --watch           keep watching for new packages
       -l, --link-dir LINK_DIR
                             directory where link is placed
       -s, --src-dir SRC_DIR
                             directory containing flatpak binaries
       -p, --prefix PREFIX   prefix link names with string
       -P, --postfix POSTFIX
                             postfix link names with string
       -L, --to-lower        make link names lowercase only
       -t, --notify_ms NOTIFY_MS
                             duration of notification in sec (-1 to disable), default=10
       -D, --debug           enable debugging
