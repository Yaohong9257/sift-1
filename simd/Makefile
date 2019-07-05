CXXFLAGS ?= -march=native -O3
override CXXFLAGS := $(CXXFLAGS) -fPIC `gdal-config --cflags`
override LDLIBS   := $(LDLIBS) -lm `gdal-config --libs`

OBJ = LibImages/LibImages.o \
      LibSSE/LibSSE.o \
      LibSift/KeyPoint.o \
      LibSift/LibSift.o \
      LibSift/Octave.o \
      LibSift/ScaleSpace.o \
      Utilities/Memory.o \
      Utilities/Parameters.o \
      Utilities/Time.o \
      Utilities/Utilities.o

LIB = libsift4ctypes.so

BIN = sift_roi


all: $(BIN) $(LIB)

$(LIB): sift4ctypes.o $(OBJ)
	$(CXX) $(LDFLAGS) -shared -o $@ $^ $(LDLIBS)

$(BIN): sift_roi.cpp $(OBJ)


clean: ; $(RM) $(BIN) $(LIB) $(OBJ) *.o
