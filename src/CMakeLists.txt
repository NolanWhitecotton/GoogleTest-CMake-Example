#/src/CMakeLists.txt

#Set the variable "SOURCES" to a list of all the sources our project has.
#Putting them in a list helps to avoid having to type them more than once
#as we will be putting them in both a library and an executable
set(SOURCES 
	Example.h
	Example.cpp
)

#Create Example_lib as a static library with all of the sources listed above
add_library(
	${PROJECT_NAME}_lib STATIC ${SOURCES}
)

#Create Example with all above sources
add_executable(
	${PROJECT_NAME} ${SOURCES}
)
