cmake_minimum_required(VERSION 3.15)
project(MyProject VERSION 1.0 LANGUAGES CXX)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# library target
add_library(mylib STATIC
  src/mylib.cpp
  src/mylib.hpp
)
target_include_directories(mylib PUBLIC
  ${CMAKE_CURRENT_SOURCE_DIR}/src
)

# executable target
add_executable(app src/main.cpp)
target_link_libraries(app PRIVATE mylib)

# install rules (optional)
install(TARGETS app mylib
  RUNTIME DESTINATION bin
  ARCHIVE DESTINATION lib
  PUBLIC_HEADER DESTINATION include
)
