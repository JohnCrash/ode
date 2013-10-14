set(PROJECTNAME drawstuff)

set(HEADER_FILES
   )

set(SOURCE_FILES
	src/drawstuff.cpp
   )

find_package(OpenGL)
find_package(GLUT)

if(WIN32)
	set(SOURCE_FILES ${SOURCE_FILES} src/windows.cpp)
elseif(APPLE)
	set(SOURCE_FILES ${SOURCE_FILES} src/osx.cpp)
else()
	set(SOURCE_FILES ${SOURCE_FILES} src/x11.cpp)
endif()

include_directories(
	${OPENGL_INCLUDE_DIR}
	${GLUT_INCLUDE_DIR}
)

add_library(drawstuff ${ODE_LIB_TYPE} ${HEADER_FILES} ${SOURCE_FILES} ${RESOURCE_FILES}) 
target_link_libraries(${PROJECTNAME} ${OPENGL_LIBRARIES} ${GLUT_LIBRARIES})

