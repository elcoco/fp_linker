# flatpak auto linker

Automatically create links for flatpak applications

Features:  
- Create usable symlinks to hard to remember flatpak binaries  
- Watches multiple directories for new installed packages and updates links accordingly  
- Can add a pre/postfix to link name to not pollute the namespace  

Dependencies:  
    - https://pypi.org/project/watchdog

Usage:
    
    ./fp_linker --src-dir /var/lib/flatpak/exports/bin --src-dir ~/.local/share/flatpak/exports/bin --link-dir ~/path/to/links --watch
