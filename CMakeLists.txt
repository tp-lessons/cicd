cmake_minimum_required(VERSION 3.4)

project(hello VERSION 1.0.0 LANGUAGES CXX)

add_subdirectory(src)

# Куда будет производиться установка приложения
install(TARGETS hello
    RUNTIME DESTINATION "bin"
    CONFIGURATIONS Release
)

# Настройка CPack для генерации MSI
set(CPACK_GENERATOR "WIX")
set(CPACK_PACKAGE_NAME "HelloWorld")
set(CPACK_PACKAGE_VENDOR "YourCompany")
set(CPACK_PACKAGE_VERSION ${PROJECT_VERSION})
set(CPACK_PACKAGE_INSTALL_DIRECTORY "HelloWorld")
set(CPACK_WIX_PRODUCT_GUID "2ee2d854-75f0-432a-bfa6-8a1ce8fb1c02") # Здесь для каждого релиза нужен новый GUID
set(CPACK_WIX_UPGRADE_GUID "a1df024f-5ac8-4459-90d0-f5747165dcbd") # Здесь для каждого релиза нужен новый GUID
set(CPACK_WIX_CMAKE_PACKAGE_REGISTRY TRUE)
set(CPACK_WIX_ARCHITECTURE "x64")

include(CPack)
