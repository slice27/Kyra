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

DEBUG_LDFLAGS    := ${DEBUG_LDFLAGS} -shared
RELEASE_LDFLAGS  := ${RELEASE_LDFLAGS} -shared
LIBS := SDL2

#****************************************************************************
# Targets of the build
#****************************************************************************

OUTPUT := libkyra.a
OUTPUT_LD := libkyra.so

all: ${OUTPUT}

#****************************************************************************
# Source files
#****************************************************************************

SRCS := action.cpp \
		box.cpp \
		boxresource.cpp \
		canvas.cpp \
		canvasresource.cpp \
		color.cpp \
		dataresource.cpp \
		dirtyrectangle.cpp \
		encoder.cpp \
		engine.cpp \
		fontresource.cpp \
		krmath.cpp \
		image.cpp \
		imagetree.cpp \
		imnode.cpp \
		kyraresource.cpp \
		painter.cpp \
		parser.cpp \
		pixelblock.cpp \
		rle.cpp \
		sdlutil.cpp \
		sprite.cpp \
		spriteresource.cpp \
		textbox.cpp \
		tile.cpp \
		tileresource.cpp \
		vault.cpp \
        namefield.cpp \
		ogltexture.cpp \
		../util/glbitstream.cpp \
		../util/glintarrayset.cpp \
		../util/glstring.cpp \
		../util/glisomath.cpp \
		../../grinliz/gldebug.cpp \
		../../grinliz/glperformance.cpp \
		../../grinliz/glgeometry.cpp \
		../../grinliz/glprime.cpp \
		../../grinliz/glmatrix.cpp \
		../../grinliz/glrandom.cpp \
		../../grinliz/glmemorypool.cpp \
		../../grinliz/glutil.cpp \
		../../grinliz/gldynamic.cpp \
		../gui/console.cpp \
		../gui/widget.cpp \
		../gui/button.cpp \
		../gui/eventmanager.cpp \
		../gui/textwidget.cpp \
		../gui/listbox.cpp \
		../guiExtended/progress.cpp \
		../guiExtended/KrImageListBox.cpp \
		../../tinyxml/tinyxml.cpp \
		../../tinyxml/tinyxmlparser.cpp \
		../../tinyxml/tinyxmlerror.cpp \
		../../tinyxml/tinystr.cpp


SRCS := ${SRCS}

OBJS := $(addsuffix .o,$(basename ${SRCS}))


#****************************************************************************
# Output
#****************************************************************************

${OUTPUT}: ${OBJS}
	${AR} ${OUTPUT} ${OBJS}

#	${LD} -shared -o ${OUTPUT_LD} ${OBJS} $(shell sdl-config --libs)


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

#install: ${OUTPUT}
#	install -m755 libkyra.a /usr/local/lib ; \
#	cp libkyra.a libkyra_2_1_0.a ; \
#	install -m755 libkyra_2_1_0.a /usr/local/lib ; \
#	mkdir -p /usr/local/include/kyra/engine ; \
#	install -m755 *.h /usr/local/include/kyra/engine ; \
#	mkdir -p /usr/local/include/kyra/util ; \
#	install -m755 ../util/*.h /usr/local/include/kyra/util ; \
#	mkdir -p /usr/local/include/kyra/gui ; \
#	install -m755 ../gui/*.h /usr/local/include/kyra/gui ; \
#	mkdir -p /usr/local/include/kyra/guiExtended ; \
#	install -m755 ../guiExtended/*.h /usr/local/include/kyra/guiExtended ; \
#	mkdir -p /usr/local/include/kyra/tinyxml ; \
#	install -m755 ../tinyxml/*.h /usr/local/include/kyra/tinyxml


# Dependencies. Badly over included, but there were just too many problems
# using makedepend and sharing the makefiles.

include ../makefiledefines
${OBJS} :  ${ENGINE_HEADERS} $(addprefix ../util/, ${UTIL_HEADERS}) $(addprefix ../gui/, ${GUI_HEADERS})
