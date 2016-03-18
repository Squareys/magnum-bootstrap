find_package(Magnum REQUIRED)

if(CORRADE_TARGET_NACL)
    find_package(Magnum REQUIRED NaClApplication)
else()
    find_package(Magnum REQUIRED Sdl2Application)
endif()

set_directory_properties(PROPERTIES CORRADE_USE_PEDANTIC_FLAGS ON)

add_executable(MyApplication MyApplication.cpp)
target_link_libraries(MyApplication
    Magnum::Application
    Magnum::Magnum)

if(CORRADE_TARGET_NACL)
    install(TARGETS MyApplication DESTINATION ${CMAKE_INSTALL_PREFIX})
    install(FILES MyApplication.html MyApplication.nmf NaClApplication.js WebApplication.css DESTINATION ${CMAKE_INSTALL_PREFIX})
endif()
