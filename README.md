## flatpak auto linker

Automatically create links for flatpak applications

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

Specify one or more source directories and one link directory where the links will be placed.  
To keep watching the directories for changes, provide the --watch flag
    
    fp_linker --src-dir /var/lib/flatpak/exports/bin --src-dir ~/.local/share/flatpak/exports/bin --link-dir ~/path/to/links --watch

You can add the link directory to your $PATH so flatpaks are easy to launch from the terminal.  
