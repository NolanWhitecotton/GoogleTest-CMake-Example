#/test/CMakeLists.txt

#List of all test sources
set(SOURCES
	test.cpp
)

#Create Example_tests
add_executable(
	${PROJECT_NAME}_tests ${SOURCES}
)

#Add Example_lib and gtest_main as link libraries to Example_tests
#Once it is linked we can #include it in the project
target_link_libraries(${PROJECT_NAME}_tests PUBLIC
	gtest_main
	${PROJECT_NAME}_lib
)

#Add the test for Example_tests
add_test(
	NAME ${PROJECT_NAME}_tests
	COMMAND ${PROJECT_NAME}_tests
)
