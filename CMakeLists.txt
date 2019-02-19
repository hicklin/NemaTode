cmake_minimum_required(VERSION 3.10)
project(nematode)

set(CMAKE_CXX_STANDARD 14)

set(LIB_SOURCES
    src/GPSFix.cc
    src/GPSService.cc
    src/NMEACommand.cc
    src/NMEAParser.cc
    src/NumberConversion.cc
    )

add_library(NemaTode SHARED ${LIB_SOURCES})
target_include_directories(NemaTode PRIVATE include/nmeaparse)

install(TARGETS NemaTode DESTINATION ${LIB_DIR})

set(LIB_HEADERS
    include/nmeaparse/Event.h
    include/nmeaparse/GPSFix.h
    include/nmeaparse/GPSService.h
    include/nmeaparse/NMEACommand.h
    include/nmeaparse/nmea.h
    include/nmeaparse/NMEAParser.h
    include/nmeaparse/NumberConversion.h
    )

install(FILES ${LIB_HEADERS} DESTINATION ${INCLUDE_DIR})

