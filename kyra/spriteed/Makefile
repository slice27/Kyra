#****************************************************************************
#
# Makefile for Kyra.
# Lee Thomason and David Leimbach
# www.grinninglizard.com
# www.sourceforge.net/projects/kyra
#
# This is a GNU make (gmake) makefile
#****************************************************************************

include ../makefilebuild


#****************************************************************************
# Targets of the build
#****************************************************************************

OUTPUT := krspriteed

all: ${OUTPUT}

#****************************************************************************
# Source files
#****************************************************************************

SRCS := dom.cpp \
		CONSOLEFONT.cpp \
		sharedstate.cpp \
		spriteed.cpp \
		statealign.cpp \
		stateempty.cpp \
		statemachine.cpp \
		statemovie.cpp \
		stateview.cpp \
		statehelp.cpp

# Add on the sources for libraries
SRCS := ${SRCS}

OBJS := $(addsuffix .o,$(basename ${SRCS}))

#****************************************************************************
# Output
#****************************************************************************

${OUTPUT}: ${OBJS} ../engine/libkyra.a
	${LD} -o $@ ${LDFLAGS} ${OBJS} ../engine/libkyra.a ${LIBS} ${EXTRA_LIBS}

#****************************************************************************
# common rules
#****************************************************************************

# Rules for compiling source files to object files
%.o : %.cpp
	${CXX} -c ${CXXFLAGS} ${INCS} $< -o $@

%.o : %.c
	${CC} -c ${CFLAGS} ${INCS} $< -o $@

clean:
	-rm -f core ${OBJS} ${OUTPUT}

#depend:
#	makedepend ${INCS} ${SRCS}

install: ${OUTPUT}
	install -m755 krspriteed /usr/local/bin

    #mkdir -p /usr/local/include/Kyra/spriteed ; \
	#install -m755 *.h /usr/local/include/Kyra/spriteed

# Dependencies. Badly over included, but there were just too many problems
# using makedepend and sharing the makefiles.

include ../makefiledefines
${OBJS} :  $(addprefix ../engine/, ${ENGINE_HEADERS}) $(addprefix ../util/, ${UTIL_HEADERS}) $(addprefix ../gui/, ${GUI_HEADERS}) \
           dom.h  sharedstate.h  statemachine.h  statemovie.h  states.h


