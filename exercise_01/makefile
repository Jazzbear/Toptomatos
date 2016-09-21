SOURCES=main.cpp part1.cpp part2.cpp
OBJECTS=$(SOURCES:.cpp=.o)
DEPS=$(SOURCES:.cpp=.d)
EXE=prog
CXXFLAGS=-I.

# Making for host
# > make ARCH=host
ifeq (${ARCH},host)
CXX=g++
BUILD_DIR=build/host
BUILD_DIR2=bin/host
endif

# Making for host
# > make ARCH=target
ifeq (${ARCH},target)
CXX=arm-devkit-g++
BUILD_DIR=build/target
BUILD_DIR2=bin/target
endif


${BUILD_DIR2}/$(EXE): $(addprefix ${BUILD_DIR}/,$(DEPS)) $(addprefix ${BUILD_DIR}/,${OBJECTS}) # << Check the $(DEPS) new dependency
	$(CXX) $(CXXFLAGS) -o $@ $(OBJECTS)


# Rule that describes how a .d (dependency) file is created from a .cpp file
# Similar to the assigment that you just completed %.cpp -> %.o
${BUILD_DIR}/%.d: %.cpp
	$(CXX) -MT${BUILD_DIR}/$(@:.d=.o) -MM $(CXXFLAGS) $^ > $@

${BUILD_DIR}/%.o: %.cpp
	$(CXX) -c $^ > $@

ifneq ($(MAKECMDGOALS),clean)
-include $(DEPS)
endif