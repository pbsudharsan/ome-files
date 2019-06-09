# 0.6.0

This release comprises the following components:

| Component             | Version                                                                 |
| --------------------- | ----------------------------------------------------------------------- |
| ome-common-cpp        | [6.0.0](https://gitlab.com/codelibre/ome-common-cpp/tags/v6.0.0)        |
| ome-model             | [6.0.0](https://gitlab.com/codelibre/ome-model/tags/v6.0.0)             |
| ome-files-cpp         | [0.6.0](https://gitlab.com/codelibre/ome-files-cpp/tags/v0.6.0)         |
| ome-files-view        | [6.0.0](https://gitlab.com/codelibre/ome-files-view/tags/v6.0.0)        |
| ome-files-performance | [0.3.0](https://gitlab.com/codelibre/ome-files-performance/tags/v0.3.0) |
| ome-files-py          | [0.3.0](https://gitlab.com/codelibre/ome-files-py/tags/v0.3.0)          |

Please follow the links for a summary of the changes in each component.

## Platform support

* C++14 is the minimum required language version; C++17 may be
  optionally used when available.
* Microsoft Visual Studio 2017 and 2019 are now supported.
* LLVM 6 is now supported
* GCC up to version 9 is supported; GCC 9 does not currently work with
  C++17 builds, due to an incompatible change in std::filesystem

## New and updated features

* Support has been added for reading and writing OME-TIFF images with
  sub-resolutions (pyramids).
* Support for handling OME-TIFF files with missing TiffData planes has
  been improved.
* Support for handling OME-TIFF files with separate companion metadata
  files been improved.
* The Boost libraries have been made optional; some header-only Boost
  libraries are still required, but will be removed in a future
  release.
  * Use the CMake option `-Dfilesystem=standard|boost|qt5` to choose
    between std::filesystem, Boost.Filesystem or a Qt5-based
    equivalent.
  * Use the CMake option `-Doptions=boost|qt5` to choose between
    Boost.ProgramOptions or Qt5 Core options handling.
* The Xerces-C++ and Xalan-C++ libraries have been made optional, and
  can be replaced by the Qt5 Xml and XmlPatterns libraries,
  respectively.
  * Use `-Dxmldom=xerces|qt5` to choose the XML DOM
    implementation.
  * In this release, XSLT transforms are only supported with
    Xerces-C++ and Xalan-C++; model upgrades and downgrades are not
    functional with Qt5.
* The OME Common XML, XSLT and units support have been split into
  separate (optional) libraries, which will be built depending upon
  the configuration options above.  These are named `ome-xerces-util`,
  `ome-xalan-util` and `ome-unit-types`, respectively.

## Infrastructure changes

Continuous integration testing is performed on GitLab, testing on
FreeBSD, Linux, MacOS X and Windows platforms in a number of different
build configurations, including C++14 and C++17 variants, with Boost
or Qt, and with Python 3 or Python 2.

## Funding

I would like to thank Damir Sudar and Michel Nederlof of Quantitative
Imaging Systems, LLC for funding the completion of both the OME-TIFF
sub-resolution pyramid feature, and the work to replace Boost with
Qt5.  Additionally, thanks to Olivier de Gaalon and Renato Araujo at
KDAB for their collaboration and testing of these changes.
