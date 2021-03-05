cmake_minimum_required(VERSION 3.12)
project(dataformats-nq VERSION 1.0.0)

find_package(daq-cmake REQUIRED)

daq_setup_environment()

find_package(dataformats REQUIRED)
find_package(dataformats-serde REQUIRED)
find_package(nwqueueadapters REQUIRED)

# No sources, so we'll create an INTERFACE library
daq_add_library(LINK_LIBRARIES dataformats::dataformats dataformats-serde::dataformats-serde nwqueueadapters::nwqueueadapters)

# Plugins to make types nwqueueadapters-able
daq_add_plugin(FragmentNQ              duneNetworkQueue LINK_LIBRARIES dataformats-nq)
# daq_add_plugin(TriggerRecordHeaderNQ   duneNetworkQueue LINK_LIBRARIES dataformats-nq)

daq_install()
