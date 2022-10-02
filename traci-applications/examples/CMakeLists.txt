# -*- Mode: python; py-indent-offset: 4; indent-tabs-mode: nil; coding: utf-8; -*-

# def build(bld):
#     obj = bld.create_ns3_program('ns3-sumo-coupling-simple', ['traci-applications', 'wave', 'netanim', 'traci'])
#     obj.source = 'ns3-sumo-coupling-simple.cc'

build_lib_example(
    NAME ns3-sumo-coupling-simple # example named aodv
    SOURCE_FILES ns3-sumo-coupling-simple.cc # single source file aodv.cc
    LIBRARIES_TO_LINK # depends on wifi, internet, aodv and internet-apps
        ${libtraci-applications}
        ${libwave}
        ${libnetanim}
        ${libtraci}
    )