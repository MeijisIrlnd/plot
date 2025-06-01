examples: out/examples
	cd examples && ../out/examples

out/examples: *.cpp ../include/plot/*.h
	mkdir -p out
	g++ -std=c++11 -g -O3 \
		-Wall -Wextra -Wfatal-errors -Wpedantic -pedantic-errors \
		-I ../include \
		examples.cpp -o out/examples

clean:
	rm -rf out html

doxygen:
	doxygen Doxyfile-local

	# Files linked from the README
	cp ../include/plot/*.h html/
	cp ../LICENSE.txt html/LICENSE.txt
	mkdir -p html/doc/examples
	cp examples.cpp html/doc/examples.cpp
	cp -r examples/* html/doc/examples/

# Depends on my personal toolchain, you shouldn't need to use this
publish: examples doxygen
	publish-signalsmith-raw /code/plot
	cd .. && publish-signalsmith-git /code/plot.git
	git push github