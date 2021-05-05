cmake_minimum_required(VERSION 3.16)

project(spiffs)

function(configure_spiffs CONFIG_FILE_DIR)

    add_library(spiffs
        ${CONFIG_FILE_DIR}/spiffs_config.h
        src/spiffs.h
        src/spiffs_cache.c
        src/spiffs_check.c
        src/spiffs_gc.c
        src/spiffs_hydrogen.c
        src/spiffs_nucleus.c
        src/spiffs_nucleus.h
    )

    target_include_directories(spiffs PUBLIC src/ ${CONFIG_FILE_DIR})

endfunction()