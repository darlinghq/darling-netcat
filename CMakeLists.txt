project(netcat)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wno-error=int-conversion")
add_definitions(-DUSE_SELECT -DPRIVATE)

set(nc_sources
    atomicio.c
    netcat.c
    sourceroute.c
    socks.c
)

add_darling_executable(nc ${nc_sources})
target_link_libraries(nc libnetwork)

install(FILES nc.1 DESTINATION libexec/darling/usr/share/man/man1)
install(TARGETS nc DESTINATION libexec/darling/usr/bin)
