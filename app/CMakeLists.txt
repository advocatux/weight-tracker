# Searches for all qml and javascript files in the current directory
# to add them to the project, if you add new files in the directory
# rerun cmake to make sure they show up in the project tree
file(GLOB QML_JS_FILES *.qml *.js)

# Make the files visible in qtcreator
add_custom_target(weight-tracker_QMlFiles ALL SOURCES ${QML_JS_FILES})

# Substitute variables in the desktop file
configure_file(${DESKTOP_FILE_NAME}.in ${CMAKE_CURRENT_BINARY_DIR}/${DESKTOP_FILE_NAME}.in)

install(FILES ${CMAKE_CURRENT_BINARY_DIR}/${DESKTOP_FILE_NAME} DESTINATION ${DESKTOP_DIR})
install(FILES ${QML_JS_FILES} DESTINATION ${WEIGHT-TRACKER_DIR})
add_subdirectory(js)
add_subdirectory(QChart)
# Make the autpilot files visible in qtcreator
file(GLOB_RECURSE AUTOPILOT_TEST_FILES *.py)
add_custom_target(weight-tracker_AutopilotFiles ALL SOURCES ${AUTOPILOT_TEST_FILES})

# Make the qml test files visible in qtcreator
file(GLOB_RECURSE UNIT_TEST_FILES tests/unit/*.qml)
add_custom_target(weight-tracker_UnitTestFiles ALL SOURCES ${UNIT_TEST_FILES})

