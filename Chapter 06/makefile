CSOBJS = codesnippets.o
UPPEROBJS = upper.o

ifdef DEBUG
DEBUGFLGS = -g
else
DEBUGFLGS =
endif
LSTFLGS =

LDFLAGS = -lSystem -syslibroot `xcrun -sdk macosx --show-sdk-path` -e _start -arch arm64

