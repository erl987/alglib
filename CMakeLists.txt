# CMake file for ALGLIB
# Copyright(C) 2010-2022 Ralf Rettig
#
# This program is free software: you can redistribute it and / or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.If not, see <http://www.gnu.org/licenses/>

set( Alglib_VERSION_MAJOR 3 ) 		# Adjust here the version number manually
set( Alglib_VERSION_MINOR 19 ) 		# Adjust here the version number manually
set( Alglib_VERSION_PATCH 0 ) 		# Adjust here the version number manually
set( Alglib_DATE "Jun 13 2022" )      	# Adjust here the release date of ALGLIB manually

add_definitions( -DUNICODE -D_UNICODE )
add_definitions( /DAE_CPU=AE_INTEL )

# generate the version info header file
configure_file ( 
	"${PROJECT_SOURCE_DIR}/libraries/Alglib/libalglib/alglibversion.template"
	"${PROJECT_SOURCE_DIR}/libraries/Alglib/libalglib/alglibversion.h"
)

set( HEADERS
	libalglib/alglibinternal.h
	libalglib/alglibmisc.h
	libalglib/ap.h
	libalglib/dataanalysis.h
	libalglib/diffequations.h
	libalglib/fasttransforms.h
	libalglib/integration.h
	libalglib/interpolation.h
	libalglib/linalg.h
	libalglib/optimization.h
	libalglib/solvers.h
	libalglib/specialfunctions.h
	libalglib/statistics.h
	libalglib/alglibversion.h
	libalglib/stdafx.h
	libalglib/kernels_avx2.h
	libalglib/kernels_fma.h
	libalglib/kernels_sse2.h
)

set( SOURCE
	libalglib/alglibinternal.cpp
	libalglib/alglibmisc.cpp
	libalglib/ap.cpp
	libalglib/dataanalysis.cpp
	libalglib/diffequations.cpp
	libalglib/fasttransforms.cpp
	libalglib/integration.cpp
	libalglib/interpolation.cpp
	libalglib/linalg.cpp
	libalglib/optimization.cpp
	libalglib/solvers.cpp
	libalglib/specialfunctions.cpp
	libalglib/statistics.cpp
	libalglib/kernels_avx2.cpp
	libalglib/kernels_fma.cpp
	libalglib/kernels_sse2.cpp
)

add_library( Alglib STATIC ${SOURCE} ${HEADERS} )
target_include_directories( Alglib PUBLIC ${PROJECT_SOURCE_DIR}/libraries/Alglib )
