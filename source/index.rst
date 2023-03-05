#####
Index
#####

This is an overview of the build system and its components as used in Overte.

Python prebuild:
	- **prebuild.py**	prepares tools required for configuring and building. Runs VCPKG.
		- **hifi_android.py**	defines functions for downloading, checking, and preparing Android dependencies (including Qt)
		- **hifi_qt.py** 		defines functions for downloading, checking, and preparing Qt packages (exluding Android Qt)
		- **hifi_singleton.py** defines functions for locking files?
		- **hifi_utils.py**     defines micelanious functions
		- **hifi_vcpkg.py**		defines functions for downloading, checking (currently disabled), preparing, and using VCPKG

CMake configuration:
	- **CMakeLists.txt**		takes configuration arguments, runs prebuild.py, configures builds
		- cmake/**compiler.cmake**	Compiler detection and pre-configuration
		- cmake/**init.cmake**		Sets "global" options that don't change. (e.g. CMake policies, relative source paths, etc.)
		- cmake/**macros/**			CMake files defining macros to be used as functions.
		- cmake/**modules/**		CMake files that look for dependencies and define their paths. They are included in other CMake files as modules.

		- cmake/**externals/**		CMake files for getting external dependencies directly via CMake.

		- cmake/**installer/**		Resources for the Windows NSIS installer.

		- cmake/**templates/**	Templates, that will be configured by CMake macros and put wherever in the codebase they are needed. For example, `BuildInfo.h.in` will be filled out by `SetPackagingParameters.cmake`, and then saved to `build/includes/BuildInfo.h`.
		
VCPKG dependencies:
	- cmake/**ports/**		Contains VCPKG ports that will be used by VCPKG to install dependencies.

Misc:
	- **CMakeGraphvizOptions.cmake**	Graphviz configuration. Used for generating an "overview" of CMake dependencies.


####
TODO
####

**android/**









.. toctree::
    :maxdepth: 2
    :titlesonly:

    Index <self>
