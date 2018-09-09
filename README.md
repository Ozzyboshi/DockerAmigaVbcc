# DockerAmigaVbcc
Docker image for Amiga Vbbc compiler

This docker image lets you compile simple c programs for the Commodore Amiga platform.
The vbcc compiler will produce binary files for the Motorola 68000 ( It works on my Amiga 600 but it should also work on A500 and A500+ )

The image was created according to this youtube tutorial:  https://www.youtube.com/watch?v=vFV0oEyY92I , many thanks to Wei-ju Wu for his wonderful work.

## Usage
1. create a directory where your C code will be stored (lets call it myamigacprogram)
2. create the program
3. create the makefile

```
mkdir ~/myamigacprogram/
cd ~/myamigacprogram/
wget https://raw.githubusercontent.com/weiju/amiga-stuff/master/os13/openwin.c
```


now create a the makefile inside myamigacprogram with your favourite text editor, the make file should be something like this

```
CC=vc
CFLAGS=-I$(NDK_INC)
all:
  $(CC) +kick13 -c99 $(CFLAGS) -lamiga -lauto /data/openwin.c -o /data/openwin
```
    
now it's time to compile openwin.c...

```
docker run -v $HOME/myamigacprogram:/data --rm -w /data  ozzyboshi/dockeramigavbcc make
```
   
You should now see the binary executable inside your myamigacprogram, copy it to a real Amiga or emulator and run it, a simple window should appear on the screen.
Happy coding & Amiga forever



  
