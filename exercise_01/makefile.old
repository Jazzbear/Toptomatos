SOURCES=main.cpp part1.cpp part2.cpp
OBJECTS=$(SOURCES :.cpp=.o)
DEPS=$(SOURCES :.cpp=.d)
EXE=prog
CXXFLAGS=-I.

# Making for host
# > make ARCH=host
ifeq (${ARCH},host)
CXX=gcc

BUILD_DIR=build/host
endif

 # Making for host
 # > make ARCH=target
 ifeq (${ARCH},target)
 CXX=arm -devkit -g++
 BUILD_DIR=build/target
 endif


 $(EXE): $(DEPS) $(OBJECTS) # << Check the $(DEPS) new dependency
 $(CXX) $(CXXFLAGS) -o $@ $(OBJECTS)

 # Rule that describes how a .d (dependency) file is created from a .cpp
file
 # Similar to the assigment that you just completed %.cpp -> %.o
 ${BUILD_DIR }/%.d: %.cpp
 $(CXX) -MT${BUILD_DIR }/$(@:.d=.o) -MM $(CXXFLAGS) $^ > $@

 ifneq ($(MAKECMDGOALS),clean)
 -include $(DEPS)
 endif