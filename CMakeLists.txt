cmake_minimum_required (VERSION 3.14.7)

project(spiffs)

set(SPIFFS_SOURCES
    ${CMAKE_CURRENT_LIST_DIR}/src/spiffs_cache.c
    ${CMAKE_CURRENT_LIST_DIR}/src/spiffs_check.c
    ${CMAKE_CURRENT_LIST_DIR}/src/spiffs_gc.c
    ${CMAKE_CURRENT_LIST_DIR}/src/spiffs_hydrogen.c
    ${CMAKE_CURRENT_LIST_DIR}/src/spiffs_nucleus.c
    CACHE INTERNAL "List of all spiffs sources"
)

set(SPIFFS_INCLUDES
    ${CMAKE_CURRENT_LIST_DIR}/src/spiffs.h
    ${CMAKE_CURRENT_LIST_DIR}/src/spiffs_nucleus.h
    CACHE INTERNAL "List of all spiffs sources"
)

set(SPIFFS_INCLUDE_DIRECTORIES
    ${CMAKE_CURRENT_LIST_DIR}/src/
    CACHE INTERNAL "List of all spiffs include directories"
)

function(configure_spiffs CONFIG_FILE_DIR)

    add_library(spiffs
        EXCLUDE_FROM_ALL
        ${SPIFFS_SOURCES}
        ${SPIFFS_INCLUDES}
        ${CONFIG_FILE_DIR}/spiffs_config.h
    )

    target_include_directories(spiffs PUBLIC ${SPIFFS_INCLUDE_DIRECTORIES} ${CONFIG_FILE_DIR})

endfunction()