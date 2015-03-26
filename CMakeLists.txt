cmake_minimum_required(VERSION 2.8.9)
message(FATAL_ERROR "testing 3 2 1")

project(MultidimData)

#-----------------------------------------------------------------------------
set(EXTENSION_HOMEPAGE "http://www.slicer.org/slicerWiki/index.php/Documentation/Nightly/Extensions/MultidimData")
set(EXTENSION_CATEGORY "Sequences")
set(EXTENSION_CONTRIBUTORS "Andras Lasso (PerkLab, Queen's), Matthew Holden (PerkLab, Queen's), Kevin Wang (PMH)")
set(EXTENSION_DESCRIPTION "A set of modules for generic sequences (multidimensional data) management in Slicer (0.3.0)")
set(EXTENSION_ICONURL "http://www.slicer.org/slicerWiki/images/c/cc/MultidimDataLogo.png")
set(EXTENSION_SCREENSHOTURLS "http://www.slicer.org/slicerWiki/images/1/17/CardiacCtReplay.gif http://www.slicer.org/slicerWiki/images/0/0f/UltrasoundToolGuidance3dOnly.gif http://www.slicer.org/slicerWiki/images/e/ea/ShapeModelSequenceBrowsing3dOnly.gif http://www.slicer.org/slicerWiki/images/thumb/5/5b/SequenceEditor.png/504px-SequenceEditor.png http://www.slicer.org/slicerWiki/images/thumb/e/ef/SequenceBrowser.png/397px-SequenceBrowser.png")

#-----------------------------------------------------------------------------
find_package(Slicer REQUIRED)
include(${Slicer_USE_FILE})

#-----------------------------------------------------------------------------
OPTION(SEQUENCES_ENABLE_EXPERIMENTAL_MODULES "Enable the building of work-in-progress, experimental modules." OFF)


#-----------------------------------------------------------------------------
add_subdirectory(Sequences)
add_subdirectory(SequenceBrowser)
add_subdirectory(MetafileImporter)

if (SEQUENCES_ENABLE_EXPERIMENTAL_MODULES)
  # In development
  add_subdirectory(SequenceRegistration)
  add_subdirectory(SequenceLabelStatistics)
  add_subdirectory(SequenceResample)
endif()

#-----------------------------------------------------------------------------
include(${Slicer_EXTENSION_CPACK})