#
# cmake file for python utilities
#

if(${PYTHON_ENABLED})

    set(module_name "pythonlibs")

    set(lib_src 
        buildtools.py 
        demo.py
        demoHelper.py
        dependency_installer.py
        download_helper.py
        find_ell.py 
        modelHelpers.py
        picluster.py
        procmon.py 
        remoterunner.py
        ziptools.py)

    add_custom_target(${module_name} DEPENDS SOURCES ${lib_src})

    set_property(TARGET ${module_name} PROPERTY FOLDER "tools/utilities")
    
    # copy files
    foreach(PY_FILE ${lib_src})
        configure_file(${PY_FILE} ${PY_FILE} COPYONLY)
    endforeach()

    add_subdirectory(gallery)

endif()  # PYTHON_ENABLED
