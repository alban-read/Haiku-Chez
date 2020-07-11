## Haiku-Chez Notes

Scheme is a wonderful programming language; Chez Scheme is a superb implementation of that language.

Chez has a very good compiler while still being highly interactive.

### Chez Scheme on Haiku

Haiku is an fun little operating system; regardless of what the dimwits say about it on arstechnica.

These are some minimal steps; on how to get Chez Scheme up and running on Haiku.

#### For 32 bit Haiku

Get the latest nightly image; and install it.

setarch x86

Install some dependencies
pkgman install devel:libuuid devel:libiconv devel:libncurses 

Pretend to be 32 bit linux when compiling.

./configure --disable-x11 -m=i3le

In version.h remove all the 64s from the lseek64 definitions; just use lseek.
 
In expediter.c remove all the locale commands.

In config.c make the search paths for the boot files the boot folder.

When linking 
-lc needs to be replaced by -lroot

Most things will now make; although I found that the linker never found the additional libs.


the uuid ncurses and iconv libraries needed to be copied into the build
folder to do the final link; since gcc does not see them.


Set up for use.
I created a scheme folder under home.
Copied Scheme and Petite from bin to the folder.
Created a boot subfolder.
Copied scheme.boot and petite.boot to the boot folder.

To run
./scheme  

The expeditor (which is an in terminal editor) worked fine; with the exception that the arrow keys do not work.
Since they are not needed to navigate anyway; this is not the end of the world.



