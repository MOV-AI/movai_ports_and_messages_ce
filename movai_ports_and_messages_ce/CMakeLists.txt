cmake_minimum_required(VERSION 3.0.2)
project(movai_ports_and_messages_ce)

#############
## Install ##
#############
# Installation

set (PACKAGE_DESTINATION ${CMAKE_INSTALL_PREFIX}/share/${PROJECT_NAME})

install(DIRECTORY ../metadata
        DESTINATION ${PACKAGE_DESTINATION}
        )

install(FILES ../manifest.txt
        DESTINATION ${PACKAGE_DESTINATION}
)