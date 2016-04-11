# alpine-freetype-noinf
An APKBUILD for a version of freetype _without_ infinality patches

Right now, the freetype library used in Alpine Linux by default includes infinality patches. In my opinion, they make the font hinting look worse, not better, so I decided to modify the package's APKBUILD and remove references to these patches.

Building such a package should take two commands:

    $ abuild -r
    $ sudo abuild -i freetype
