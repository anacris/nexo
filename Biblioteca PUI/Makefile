#@author Sebastián Marichal
# 		   sebastian_marichal@hotmail.com
# 		   sebarocker@gmail.com
#
# Universidad de la República, Montevideo , Uruguay
#
INC_DIR= ../ARToolkit/include
LIB_DIR= ../ARToolkit/lib/
SRC_DIR= c++
BIN_DIR= ../bin

LDFLAG=-pthread -lgstreamer-0.10 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lxml2 -lglib-2.0 -L/usr/X11R6/lib -L/usr/local/lib -L$(LIB_DIR)
LIBS= -lARgsub -lARgsub_lite -lARvideo -lARMulti -lAR -lpthread -lglut -lGLU -lGL -lXi -lX11 -lm -lXmu -lcv -lcvaux -lSDL -lSDL_mixer -lSDL_gfx

#Para optimizacion agresiva. Cuidado, pueden variar los resultados por la perdida de precision
CFLAG_RELEASE_AGGRESIVE= -pipe -O2 -ffast-math -funroll-all-loops -march=native -mtune=native -msse -msse2 -msse3 -mmmx -m3dnow -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I/usr/include/opencv -I$(INC_DIR)

#CFLAG_RELEASE incluye todas las banderas de optimizacion menos -funroll-all-loops
CFLAG_RELEASE= -fPIC -pipe -O2 -ffast-math -march=native -mtune=native -msse -msse2 -msse3 -mmmx -m3dnow -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I/usr/include/opencv -I$(INC_DIR)

#Banderas para debug, no optimizan (compilacion mas rapida) y generan simbolos de debug
CFLAG_DEBUG   = -pipe -g -O0 -fPIC -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I/usr/include/opencv -I$(INC_DIR)

CFLAG= $(CFLAG_DEBUG)

OBJS =
HEADDERS =

all: Pui.o Funciones.o cvUtilities.o

Pui.o: $(SRC_DIR)/Pui.cpp cvUtilities.o Funciones.o TimeUtils.o
	g++ -c $(CFLAG) -DGLUT_HABILITADO=-1 $(SRC_DIR)/Pui.cpp

TimeUtils.o: $(SRC_DIR)/TimeUtils.cpp
	g++ -c $(CFLAG) $(SRC_DIR)/TimeUtils.cpp

Funciones.o: $(SRC_DIR)/Funciones.cpp 
	g++ -c $(CFLAG) $(SRC_DIR)/Funciones.cpp

cvUtilities.o: $(SRC_DIR)/cvUtilities.cpp Funciones.o
	g++ -c $(CFLAG) $(SRC_DIR)/cvUtilities.cpp

clean:
	rm -f *.o

allclean:
	rm -f *.o