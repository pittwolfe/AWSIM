PACKAGE    = AWSIM
CC         = gcc
SRC_DIRS   = .
CFLAGS     = 
# if we want a lot of warnings
# CFLAGS     = $(CFLAGS) -Wall -Wno-unknown-pragmas -Wno-sign-compare -Wno-unused-variable -Wextra
CFLAGS_OPT = -O3 -ffast-math
LIBS       = -lm

# if using fftw:
# CFLAGS     = $(CFLAGS) -DALLOW_FFTW
# LIBS       = $(LIBS) -lfftw

INCUDE_DIRS := $(addprefix -I./, $(SRC_DIRS))
OBJECTS := $(wildcard $(addsuffix /*.c*, $(SRC_DIRS)))
OBJECTS := $(OBJECTS:.c=.o)
OBJECTS := $(OBJECTS:.cc=.o)
OBJECTS := $(OBJECTS:.cpp=.o)

all : $(PACKAGE)

$(PACKAGE) : $(OBJECTS)
	$(CC) -o $@ $(OBJECTS) $(LIBS)

%.o : %.cpp
	$(CC) -o $@ -c $< $(INCUDE_DIRS) $(CFLAGS) $(CFLAGS_OPT)

%.o : %.c
	$(CC) -o $@ -c $< $(INCUDE_DIRS) $(CFLAGS) $(CFLAGS_OPT)

%.o : %.cc
	$(CC) -o $@ -c $< $(INCUDE_DIRS) $(CFLAGS) $(CFLAGS_OPT)

.PHONY : clean

clean : 
	rm -r *.o
