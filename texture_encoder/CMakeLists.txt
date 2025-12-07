add_library(TextureEncoder SHARED "TextureEncoder.cpp" "TextureEncoder.h" "TextureFormat.h")
set_target_properties(TextureEncoder PROPERTIES OUTPUT_NAME "textureencoder")

if (CMAKE_VERSION VERSION_GREATER 3.12)
    set_property(TARGET TextureEncoder PROPERTY CXX_STANDARD 20)
endif()

# Link directly to cuttlefish_lib target (built in this repo)
target_link_libraries(TextureEncoder PRIVATE cuttlefish_lib)

# Include the cuttlefish headers
target_include_directories(TextureEncoder PRIVATE
    ${CMAKE_SOURCE_DIR}/lib/include
)

cfs_set_folder(TextureEncoder)
