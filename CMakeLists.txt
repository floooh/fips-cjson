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
    fips_files(cJSON.c cJSON.h cJSON_Utils.c cJSON_Utils.h)
    add_definitions(-DCJSON_HIDE_SYMBOLS=1)
fips_end_lib()
if (FIPS_MSVC)
    # disable unknown pragma warning, macro redefinition, formal parameter X different from definition
    set_target_properties(cjson PROPERTIES COMPILE_FLAGS "/wd4068 /wd4005 /wd4028")
endif()

if (NOT FIPS_IMPORT)
    fips_finish()
endif()


