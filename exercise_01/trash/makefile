main: main.o part1.o part2.o
	g++ main.o part1.o part2.o

main.o: main.cpp part1.o part2.o
	g++ -o main main.cpp
part1.o: part1.cpp part1.h
	g++ -c part1.cpp
part2.o: part2.cpp part2.h
	g++ -c part2.cpp