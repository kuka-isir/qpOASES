qpOASES wrapped in a catkin package
=====

It allows you to use catkin macros to find qpOASES to avoid installing it somewhere or exporting the path. 
- Builds a **static library**
- Fetches the **latest version** on the remote before a build.

To include qpOASES in your catkin package : 

`package.xml` : 
```xml
<build_depend>qpOASES<build_depend>
```
`CMakeLists.xml` : 
```cmake
find_package(catkin REQUIRED COMPONENTS qpOASES)
include_directories(${catkin_INCLUDE_DIRS})
target_link_libraries(my_super_target ${catkin_LIBRARIES})
```
`your_header.hpp` :
```c
#include <qpOASES.hpp>
``` 

