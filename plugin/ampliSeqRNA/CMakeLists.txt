# Copyright (C) 2010 Ion Torrent Systems, Inc. All Rights Reserved
cmake_minimum_required (VERSION 2.6)

# derive the plugin name from the folder name
get_filename_component(PLUGIN_NAME ${CMAKE_CURRENT_SOURCE_DIR} NAME)
PROJECT(${PLUGIN_NAME})

# this method will search the plugin script for it's version number and insert that into the debian package
include(../cmake/CMakeLists.PluginGetVersion.txt)

# set the standard package attributes
include(../cmake/CMakeLists.PluginSetAttributes.txt)

# these are the package specific attributues which cannot be automated
SET(CPACK_PACKAGE_DESCRIPTION "This plugin analyzes RNA species reads mapped to a coanonical transcriptome reference, as produced from an AmpliSeq run targeting cDNA. Reads are collected for individual barcodes and a summary report made comparing the relative expressions of genes for different samples, as represented by individual barcodes.")
SET(CPACK_DEBIAN_PACKAGE_DEPENDS "python, ion-pipeline")
SET(CPACK_DEBIAN_PACKAGE_MAINTAINER "Brian Bourke-Martin")

# this will include the entire directory contents into the package
include(../cmake/CMakeLists.PluginInstallEverything.txt)

INCLUDE(CPack)
