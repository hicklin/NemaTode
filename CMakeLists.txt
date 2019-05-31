cmake_minimum_required(VERSION 3.10)
project(nematode)

## build settings
set(VERSION_MAJOR 1)
set(VERSION_MINOR 0)
set(VERSION_PATCH 0)

set(NEMATODE_VERSION ${VERSION_MAJOR}.${VERSION_MINOR}.${VERSION_PATCH})

set(CMAKE_CXX_STANDARD 14)

set(LIB_SOURCES
    src/GPSFix.cc
    src/GPSService.cc
    src/NMEACommand.cc
    src/NMEAParser.cc
    src/NumberConversion.cc
    )

add_library(NemaTode SHARED ${LIB_SOURCES})
include_directories(NemaTode PRIVATE include/nmeaparse)

## set the shared library soname
set_target_properties(NemaTode PROPERTIES
        VERSION ${NEMATODE_VERSION}
        SOVERSION ${VERSION_MAJOR})

## install the shared library
install(TARGETS NemaTode
        LIBRARY DESTINATION lib)

set(LIB_HEADERS
    include/nmeaparse/Event.h
    include/nmeaparse/GPSFix.h
    include/nmeaparse/GPSService.h
    include/nmeaparse/NMEACommand.h
    include/nmeaparse/nmea.h
    include/nmeaparse/NMEAParser.h
    include/nmeaparse/NumberConversion.h
    )

install(FILES ${LIB_HEADERS} DESTINATION include/nmeaparse)
