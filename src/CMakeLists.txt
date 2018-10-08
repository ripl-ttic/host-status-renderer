add_definitions(-std=gnu99)

add_library(host-status-renderer SHARED
            renderer_host_status.c)

target_link_libraries(host-status-renderer ${OPENGL_LIBRARIES})

set(REQUIRED_LIBS bot2-vis lcmtypes_host-status)

pods_use_pkg_config_packages(host-status-renderer ${REQUIRED_LIBS})

pods_install_headers(renderer_host_status.h DESTINATION
                     host_status_renderer)

pods_install_libraries(host-status-renderer)
pods_install_pkg_config_file(host-status-renderer
    CFLAGS
    LIBS -lhost-status-renderer
    REQUIRES ${REQUIRED_LIBS}
    VERSION 0.0.1)
