# Generic GNUMakefile
﻿MAKEFILE = gnu
CC = gcc
#debug options
DOPT = -Wall -g
#release options
ROPT = -o3
#opt will get the release/debug config for the compiler
# change to $(DOPT) to produce debugable executable
OPT = $(ROPT)
#release exe name
EXE = build/MidiLegend.exe
#debug exe name
DEXE = debug/MidiLegend_d.exe
#add all needed files here! (just C files not header)

SUBDIRS = src/GameControler/ src/GameDisplay/ src/GameModel/ src/SheetMusic/ src/Menu/ src/Shared/
RDIR = Release/
DDIR = Debug/

# Source files
GC_SRC = $(wildcard src/GameControler/*.c)
GD_SRC = $(wildcard src/GameDisplay/*.c)
GM_SRC = $(wildcard src/GameModel/*.c)
SM_SRC = $(wildcard src/SheetMusic/*.c)
MN_SRC = $(wildcard src/Menu/*.c)
SH_SRC = $(wildcard src/Shared/*.c)
SRC = main.c $(GC_SRC) $(GD_SRC) $(GM_SRC) $(SM_SRC) $(MN_SRC) $(SH_SRC)

GC_HDR = $(GC_SRC:.c=.h)
GD_HDR = $(GD_SRC:.c=.h)
GM_HDR = $(GM_SRC:.c=.h)
SM_HDR = $(SM_SRC:.c=.h)
MN_HDR = $(MN_SRC:.c=.h)
SH_HDR = $(SH_SRC:.c=.h)

HDR = $(GC_HDR) $(GD_HDR) $(GM_HDR) $(SM_HDR) $(MN_HDR) $(SH_HDR)

#object files for release version
GC_OBJ = $(GC_SRC:.c=.o)
GD_OBJ = $(GD_SRC:.c=.o)
GM_OBJ = $(GM_SRC:.c=.o)
SM_OBJ = $(SM_SRC:.c=.o)
MN_OBJ = $(MN_SRC:.c=.o)
SH_OBJ = $(SH_SRC:.c=.o)
OBJ = ./src/main.o $(GC_OBJ) $(GD_OBJ) $(GM_OBJ) $(SM_OBJ) $(MN_OBJ) $(SH_OBJ)

#object files for debug version
GC_DOBJ = $(GC_SRC:.c=_d.o)
GD_DOBJ = $(GD_SRC:.c=_d.o)
GM_DOBJ = $(GM_SRC:.c=_d.o)
SM_DOBJ = $(SM_SRC:.c=_d.o)
MN_DOBJ = $(MN_SRC:.c=_d.o)
SH_DOBJ = $(SH_SRC:.c=_d.o)
DOBJ = main_d.o $(GC_DOBJ) $(GD_DOBJ) $(GM_DOBJ) $(SM_DOBJ) $(MN_DOBJ) $(SH_DOBJ)

# List of the path to use when looking up for libraries
# modify path to match your target architecture ( x86 or x64), so it will link to the good library 
#LIBPATH = 
# list of libraries to be linked
LIBS = -I include -L lib -lmingw32 -lSDL2main -lSDL2 -lSDL2_image -lSDL2_mixer
#LIBS = -lmingw32 -lSDL2main -lSDL2 -lSDL2_image -lSDL2_mixer

# recipes

# ------------
# release rules

.c.o:
	$(CC) -c $(CFLAGS) $<

all: $(EXE)

$(EXE): $(OBJ)
	$(CC) $(ROPT) $(INCPATH) $(LIBPATH)  -o $@ $(OBJ) $(LIBS)

%.o : %.c $(HDR)
	$(CC) $(ROPT) $(INCPATH) $(LIBPATH) $(LIBS) -c $< -o $@


# ------------
# Debug rule

debug: $(DEXE)

$(DEXE): $(DOBJ) $(HDR)
	$(CC) $(DOPT) $(INCPATH) $(LIBPATH)  -o $@ $(DOBJ) $(LIBS)

%_d.o : %.c $(HDR)
	$(CC) $(DOPT) $(INCPATH) $(LIBPATH) $(LIBS) -c $< -o $@

	
# -----------
# clean rule

clean:
	-rm $(OBJ) $(DOBJ)  2>/dev/null || true

	
	
	
# memo internal macro
# $@ --> The file name of the target of the rule.
# $^ --> he names of all the prerequisites, with spaces between them.
# $< The name of the first prerequisite.
