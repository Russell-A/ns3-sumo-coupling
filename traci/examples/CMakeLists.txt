# -*- Mode: python; py-indent-offset: 4; indent-tabs-mode: nil; coding: utf-8; -*-

# def build(bld):
#     obj = bld.create_ns3_program('traci-example', ['traci'])
#     obj.source = 'traci-example.cc'


build_lib_example(
  NAME traci-example # example named aodv
  SOURCE_FILES traci-example.cc # single source file aodv.cc
  LIBRARIES_TO_LINK # depends on wifi, internet, aodv and internet-apps
    ${libtraci}
)