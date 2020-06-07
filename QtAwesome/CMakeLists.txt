add_library(QtAwesome SHARED 
    "QtAwesome.cpp"
    "QtAwesomeAnim.cpp"
    "QtAwesome.qrc"
)

target_link_libraries(QtAwesome
    PUBLIC
        Qt5::Core
        Qt5::Gui
    PRIVATE
        Qt5::Widgets
)

target_include_directories(QtAwesome
    INTERFACE
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
        $<INSTALL_INTERFACE:include>
)

set_property(TARGET QtAwesome PROPERTY PUBLIC_HEADER 
        "QtAwesome.h"
        "QtAwesomeAnim.h"
)

install(
    TARGETS QtAwesome
    EXPORT qtawesome-targets
    DESTINATION "lib"
    PUBLIC_HEADER DESTINATION "include"
)
