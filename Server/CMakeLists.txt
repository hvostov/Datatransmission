include_directories(${SQLITE_PATH})

# Server CMake file
add_executable(Server src/main.cpp
        src/helper.h
        src/helper.cpp
        src/server.h
        src/server.cpp)

# Link against the filesystem library if necessary
if (CMAKE_COMPILER_IS_GNUCC AND CMAKE_CXX_COMPILER_VERSION VERSION_LESS 9)
    target_link_libraries(Server PRIVATE stdc++fs)
endif()

# Link against the Winsock library on Windows
if(WIN32)
    target_link_libraries(Server PRIVATE Ws2_32)
endif()

# Include sqlite3
include_directories(Server PRIVATE ${SQLITE_INCLUDE_DIR})
target_link_libraries(Server PRIVATE ${SQLITE_LIBRARY})

# Find LZ4 and link
include_directories(${LZ4_INCLUDE_DIR})
target_link_libraries(Server PRIVATE ${LZ4_LIBRARY})

# Include Libsodium
include_directories(${LIBSODIUM_INCLUDE_DIR})
target_link_libraries(Server PRIVATE ${LIBSODIUM_LIBRARY})