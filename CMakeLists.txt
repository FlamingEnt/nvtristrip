project(NvTriStrip)

# set include directories
include_directories(
	./Src
)

# NvTriStrip code
file(GLOB NVTRISTRIP_INCLUDES Src/*.h)
file(GLOB NVTRISTRIP_SOURCES Src/*.cpp)
source_group("Inc" FILES ${NVTRISTRIP_INCLUDES})
source_group("Src" FILES ${NVTRISTRIP_SOURCES})

# build NvTriStrip static library
add_library(NvTriStrip STATIC ${NVTRISTRIP_INCLUDES} ${NVTRISTRIP_SOURCES})

if(MSVC)
    # reset default struct packing for MSVC
    target_compile_options(NvTriStrip PRIVATE /Zp8)
endif()