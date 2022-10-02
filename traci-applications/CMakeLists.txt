# # -*- Mode: python; py-indent-offset: 4; indent-tabs-mode: nil; coding: utf-8; -*-

# # def options(opt):
# #     pass

# # def configure(conf):
# #     conf.check_nonfatal(header_name='stdint.h', define_name='HAVE_STDINT_H')

# def build(bld):
#     module = bld.create_ns3_module('traci-applications', ['core', 'wifi', 'applications', 'mobility',
#     'internet', 'config-store','stats', 'traci', 'applications'])
#     module.source = [
#         'model/traffic-control-app.cc',
#         'helper/traffic-control-app-helper.cc',
#         ]

#     headers = bld(features='ns3header')
#     headers.module = 'traci-applications'
#     headers.source = [
#         'model/traffic-control-app.h',
#         'helper/traffic-control-app-helper.h',
#         ]

#     if bld.env.ENABLE_EXAMPLES:
#         bld.recurse('examples')

#     # bld.ns3_python_bindings()



##### Cmake
build_lib(
  LIBNAME traci-applications 
  SOURCE_FILES # equivalent to module.source
    model/traffic-control-app.cc
    helper/traffic-control-app-helper.cc
  HEADER_FILES # equivalent to headers.source
    model/traffic-control-app.h
    helper/traffic-control-app-helper.h
  LIBRARIES_TO_LINK ${libinternet} # depends on internet and wifi,
                    ${libwifi}     # but both are prefixed with lib in CMake
                    ${libcore}
                    ${libapplications}
                    ${libmobility}
                    ${libconfig-store}
                    ${libstats}
                    ${libtraci}
#   TEST_SOURCES # equivalent to module_test.source
#     test/aodv-id-cache-test-suite.cc
#     test/aodv-regression.cc
#     test/aodv-test-suite.cc
#     test/loopback.cc
#     test/bug-772.cc
)

# # DEPENDENCY_NAME is used as a prefix to variables set by the find_external_library macro
# # HEADER_NAME(S) is(are) the name(s) of the header(s) you want to include
# # LIBRARY_NAME(S) is(are) the name(s) of the library(ies) you want to link
# # SEARCH_PATHS are the custom paths you can give if your library is not on a system path
# find_external_library(DEPENDENCY_NAME traci
#                       HEADER_NAME sumo-config.h sumo-socket.h sumo-storage.h sumo-TraCIAPI.h sumo-TraCIConstants.h sumo-TraCIDefs.h traci-client.h traci-module.h
#                       LIBRARY_NAME traci
#                       SEARCH_PATHS /Users/Res_proj/Documents/Research/ns-allinone-3.36.1/ns-3.36.1/src/traci)

# # If the header(s) and library(ies) are not found, a message will be printed during the configuration
# # If the header(s) and the library(ies) are found, we can use the information found by the buildsystem
# if(${traci_FOUND}) # Notice that the contents of DEPENDENCY_NAME became a prefix for the _FOUND variable
#     # The compiler will not be able to find the include that is not on
#     # a system include path, unless we explicitly inform it

#     # This is the equivalent of -I/optional/search/path/to/custom/sqlite3/include
#     # and AFFECTS ALL the targets in the CURRENT DIRECTORY and ITS SUBDIRECTORIES
#     include_directories(${traci_INCLUDE_DIRS})

#     # The compiler should be able to locate the headers, but it still needs to be
#     # informed of the libraries that should be linked

#     # This is the equivalent of -l/optional/search/path/to/custom/sqlite3/library/libsqlite3.so
#     # and AFFECTS ALL the targets in the CURRENT DIRECTORY and ITS SUBDIRECTORIES
#     link_libraries(${traci_LIBRARIES})
# endif()