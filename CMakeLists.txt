cmake_minimum_required(VERSION 3.9)

project("soil2" LANGUAGES CXX C)

set(SOIL2_HEADERS
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/etc1_utils.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/image_DXT.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/image_helper.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/jo_jpeg.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/pkm_helper.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/pvr_helper.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/SOIL2.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/stbi_DDS.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/stbi_DDS_c.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/stbi_ext.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/stbi_ext_c.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/stb_image.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/stb_image_write.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/stbi_pkm.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/stbi_pkm_c.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/stbi_pvr.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/stbi_pvr_c.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/common/common.hpp
)

set(SOIL2_SRC
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/etc1_utils.c
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/image_DXT.c
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/image_helper.c
        ${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/SOIL2.c
        ${CMAKE_CURRENT_SOURCE_DIR}/src/common/common.cpp
)

add_library( soil2 SHARED ${SOIL2_HEADERS} ${SOIL2_SRC} )

target_include_directories(
        soil2 PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src/SOIL2/>
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src/common/>
        $<INSTALL_INTERFACE:include>
)

install(TARGETS soil2 EXPORT soil2
        ARCHIVE DESTINATION lib/ COMPONENT libraries
        LIBRARY DESTINATION lib/ COMPONENT libraries
        RUNTIME DESTINATION bin/ COMPONENT libraries
)
