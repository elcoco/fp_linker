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

Typical usage:

    # --link-dir specifies the destination directory where fp_linker will create the links
    fp-linker --link-dir /path/where/links/will/be/created

fp_linker tries to find desktop files in the provided source paths.  
If no paths are specified, the default flatpak locations are used:  

    /var/lib/flatpak/exports/share/applications
    $HOME/.local/share/flatpak/exports/share/applications

The package name can usually be found in the desktop file and will fallback to the last part of the FQDN.

    com.prusa3d.PrusaSlicer -> PrusaSlicer
    org.freecad.FreeCAD     -> FreeCAD

To keep watching the directories for changes, provide the --watch flag.  

You can add the link directory to your $PATH so flatpaks are easy to launch from the terminal.  

### help

    > fp_linker -h                                                                                                      18:18:38
    usage: fp_linker [-h] [-w] -l LINK_DIR [-s SRC_DIR] [-p PREFIX] [-P POSTFIX] [-L] [-n NOTIFY_MS] [-D]

    Create links for flatpak apps

    options:
      -h, --help            show this help message and exit
      -w, --watch           daemonize, keep watching for new packages
      -l, --link-dir LINK_DIR
                            directory where links are placed
      -s, --src-dir SRC_DIR
                            directory containing flatpak desktop files
      -p, --prefix PREFIX   prefix link names with string
      -P, --postfix POSTFIX
                            postfix link names with string
      -L, --to-lower        make link names lowercase only
      -n, --notify_ms NOTIFY_MS
                            duration of notification in sec (-1 to disable), default=10
      -D, --debug           enable debugging
