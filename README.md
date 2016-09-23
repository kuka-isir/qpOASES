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
### Notes
If you experience connection issues, such as
> svn: E230001: Unable to connect to a repository at URL 'https://projects.coin-or.org/svn/qpOASES/stable/3.2'
> svn: E230001: Server SSL certificate verification failed: issuer is not trusted

```
# query the svn repo to be asked about the certificate
svn list https://projects.coin-or.org/svn/qpOASES/stable/3.2/
# and choose "accept permanently"
```
