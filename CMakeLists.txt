#
# project: fips-cjson
#

if (NOT FIPS_IMPORT)
    cmake_minimum_required(VERSION 2.8)
    get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
    include("${FIPS_ROOT_DIR}/cmake/fips.cmake")
    fips_setup()
    fips_project(fips-cjson)
endif()

fips_begin_lib(cjson)
    fips_dir(cJSON GROUP .)
    fips_files(cJSON.c cJSON.h)
fips_end_lib()

if (NOT FIPS_IMPORT)
    fips_finish()
endif()


