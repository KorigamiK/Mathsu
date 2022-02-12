cmake_minimum_required(VERSION 3.12)
set(CMAKE_CXX_STANDARD 17)

# Project variables
set(PROJECT_NAME              "mathsu")
set(LOCAL_PROJECT_VERSION     "0.0.1")
set(LOCAL_PROJECT_DESCRIPTION "Description")

# Project setup
project(${PROJECT_NAME}
        VERSION ${LOCAL_PROJECT_VERSION}
        DESCRIPTION ${LOCAL_PROJECT_DESCRIPTION}
        LANGUAGES CXX)



# Header files (relative to "include" directory)
set(HEADERS
    header.h
)

# Source files (relative to "src" directory)
set(SOURCES
    main.cpp
)

# Compiler definitions
set(DEFINES
)

# Compiler options
set(OPTIONS
)

add_executable(${PROJECT_NAME})
list(TRANSFORM HEADERS PREPEND "include/")
list(TRANSFORM SOURCES PREPEND "src/")
target_include_directories(${PROJECT_NAME} PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/include)
target_sources(${PROJECT_NAME} PRIVATE ${SOURCES} ${HEADERS})
target_compile_definitions(${PROJECT_NAME} PRIVATE ${DEFINES})
target_compile_options(${PROJECT_NAME} PRIVATE ${OPTIONS})

set(PLATFORM_PSP OFF)

if(PLATFORM_PSP)
    message(STATUS "Building for PSP!")
else()  
    message("Build Desktop!")
    target_link_libraries(${PROJECT_NAME} PRIVATE SDL2main SDL2)
    set_target_properties(${PROJECT_NAME} PROPERTIES RUNTIME_OUTPUT_DIRECTORY "bin")
endif()






