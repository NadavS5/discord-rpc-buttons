include_directories(${PROJECT_SOURCE_DIR}/include)
add_executable(
    send-presence
    MACOSX_BUNDLE
    send-presence.c
)
set_target_properties(send-presence PROPERTIES
    MACOSX_BUNDLE_BUNDLE_NAME "Send Presence"
    MACOSX_BUNDLE_GUI_IDENTIFIER "com.discordapp.examples.send-presence"
)
target_link_libraries(send-presence discord-rpc)


set_target_properties(send-presence PROPERTIES WIN32_EXECUTABLE TRUE)

if (WIN32)
    target_link_options(send-presence PRIVATE "/ENTRY:mainCRTStartup")
endif()


install(
    TARGETS send-presence
    RUNTIME
        DESTINATION "bin"
        CONFIGURATIONS Release
    BUNDLE
        DESTINATION "bin"
        CONFIGURATIONS Release
)