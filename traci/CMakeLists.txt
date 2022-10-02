# # -*- Mode: python; py-indent-offset: 4; indent-tabs-mode: nil; coding: utf-8; -*-


# # def options(opt):
# #     pass

# # def configure(conf):
# #     conf.check_nonfatal(header_name='stdint.h', define_name='HAVE_STDINT_H')

# def build(bld):
#     module = bld.create_ns3_module('traci', ['core', 'mobility', 'internet'])
#     module.source = [
#         'model/traci-client.cc',
#         'model/sumo-socket.cc',
#         'model/sumo-storage.cc',
#         'model/sumo-TraCIAPI.cc',
#         ]

#     headers = bld(features='ns3header')
#     headers.module = 'traci'
#     headers.source = [
#         'model/traci-client.h',
#         'model/sumo-TraCIAPI.h',
#         'model/sumo-config.h',
#         'model/sumo-socket.h',
#         'model/sumo-storage.h',
#         'model/sumo-TraCIConstants.h',
#         'model/sumo-TraCIDefs.h',
#         ]

#     if bld.env.ENABLE_EXAMPLES:
#         bld.recurse('examples')

#     # bld.ns3_python_bindings()



### Cmake
build_lib(
  LIBNAME traci # aodv module, which can later be linked to examples and modules with ${libaodv}
  SOURCE_FILES # equivalent to module.source
    model/traci-client.cc
    model/sumo-socket.cc
    model/sumo-storage.cc
    model/sumo-TraCIAPI.cc
  HEADER_FILES # equivalent to headers.source
    model/traci-client.h
    model/sumo-TraCIAPI.h
    model/sumo-config.h
    model/sumo-socket.h
    model/sumo-storage.h
    model/sumo-TraCIConstants.h
    model/sumo-TraCIDefs.h
  LIBRARIES_TO_LINK ${libcore} # depends on internet and wifi,
                    ${libmobility}     # but both are prefixed with lib in CMake
                    ${libinternet}
#   TEST_SOURCES # equivalent to module_test.source
#     test/aodv-id-cache-test-suite.cc
#     test/aodv-regression.cc
#     test/aodv-test-suite.cc
#     test/loopback.cc
#     test/bug-772.cc
)