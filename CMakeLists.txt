cmake_minimum_required(VERSION 2.8.7)

#-----------------------------------------------------------------------------
set(MODULE_NAME elastixExtension) # Do not use 'project()'

#-----------------------------------------------------------------------------
set(MODULE_HOMEPAGE "http://www.slicer.org/slicerWiki/index.php/Documentation/Snapshot/Developers/Tutorials/ExtensionWriting")
set(MODULE_CATEGORY "Examples")
set(MODULE_STATUS "Beta")
set(MODULE_CONTRIBUTORS "Sonia Pujol")
set(MODULE_DESCRIPTION "This is an example of CLI module built as an extension")
set(MODULE_ICONURL "http://viewvc.slicer.org/viewvc.cgi/Slicer4/trunk/Extensions/Testing/elastixExtension/elastixExtension.png?revision=19437&view=co")
set(MODULE_SCREENSHOTURLS "http://wiki.slicer.org/slicerWiki/images/a/ab/Slicer-r19441-elastixExtension-screenshot.png http://wiki.slicer.org/slicerWiki/images/1/1e/Slicer-r19441-elastixExtension-screenshot-2.png")
set(MODULE_ACKNOWLEDGEMENTS "This work was supported by ...")
set(MODULE_MAJOR_VERSION 0)
set(MODULE_MINOR_VERSION 1)
set(MODULE_PATCH_VERSION 0)

#-----------------------------------------------------------------------------
if(NOT Slicer_SOURCE_DIR)
  find_package(Slicer REQUIRED)
  include(${Slicer_USE_FILE})
endif()

# Configure XML description
configure_file(
  ${MODULE_NAME}.xml.in
  ${CMAKE_CURRENT_BINARY_DIR}/${MODULE_NAME}.xml
  @ONLY
  )

#-----------------------------------------------------------------------------
#add_subdirectory(Logic)

#-----------------------------------------------------------------------------
set(cli_module_include_directories
  )

set(cli_module_SRCS
  )

set(cli_module_target_libraries
  ${ITK_LIBRARIES}
  )

#-----------------------------------------------------------------------------
slicerMacroBuildCLI(
  NAME ${MODULE_NAME}
  #LOGO_HEADER ${Slicer_SOURCE_DIR}/Resources/NAMICLogo.h
  TARGET_LIBRARIES ${cli_module_target_libraries}
  INCLUDE_DIRECTORIES ${cli_module_include_directories}
  ADDITIONAL_SRCS ${cli_module_SRCS}
  #EXECUTABLE_ONLY
  )

#-----------------------------------------------------------------------------
if(BUILD_TESTING)
  add_subdirectory(Testing)
endif()

#-----------------------------------------------------------------------------
if(NOT Slicer_SOURCE_DIR)
  include(${Slicer_EXTENSION_CPACK})
endif()
