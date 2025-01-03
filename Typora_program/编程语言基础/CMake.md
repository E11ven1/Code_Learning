#  `Cmake`

### `CMake`中的变量

+ 变量和含义  

    | 常用变量                        | 含义 |   
    | :-:                         | :-: |
    | ***`PROJECT_NAME`***            | 工程名变量 |
    | ***`PROJECT_SOURCE_DIR`***      | 顶层的项目目录 | 
    | ***`PROJECT_BINARY_DIR`***      | 使用`cmake`的路径 | 
    | ***`CMAKE_ROOT`***              |`CMAKE`安装的根目录 |
    |***`CMAKE_BUILD_TYPE`***         | 编译类型：`empty`，`Debug`，`Release`...|
    | ***`CMAKE_SOURCE_DIR`***        |顶层的`CMakeLists.txt`所在路径|
    | ***`CMAKE_BINARY_DIR`***        |顶层的`CMakeLists.txt`的`build`所在目录|
    |***`CMAKE_<LANG>_COMPILER`***    |设定某个语言`LANG`的编译器，比如`g++`|
    | ***`CMAKE_INSTALL_PREFIX`***    | 指令`install`的路径 | 
    |***`CMAKE_CURRENT_SOURCE_DIR`*** |当前`CMakeLists.txt`所在路径|
    |***`CMAKE_CURRENT_BINARY_DIR`*** |当前`CMakeLists.txt`的`build`所在目录|
    |***`EXECUTABLE_OUTPUT_PATH`***   | 可执行文件输出路径|
    |***`LIBRARY_OUTPUT_PATH`***      | 库输出路径|
+ 个别变量解释
  [源码](./smuduo)目录结构
    ```bash
        jmudou   
        ├── build.sh
        ├── CMakeLists.txt
        └── muduo
           └── base
               ├── Atomic.h
               ├── CMakeLists.txt
               ├── copyable.h
               ├── tests
               │   ├── Atomic_unittest.cc
               │   ├── CMakeLists.txt
               │   └── Timestamp_unittest.cc
               ├── Timestamp.cc
               ├── Timestamp.h
               └── Types.h
    ```
    三个`CMakeLists.txt`输出
    ```cmake
        jmuduo/CMakeLists.txt: 
            PROJECT_SOURCE_DIR= 11/jmuduo
            PROJECT_BINARY_DIR= 11/build/debug 
            CMAKE_SOURCE_DIR= 11/jmuduo            # 指定顶层的CMakeLists.txt的，因此所有的都相同
            CMAKE_BINARY_DIR= 11/build/debug
            # 上面四项都是与整个项目相关，因此都是一致的。
            CMAKE_CURRENT_SOURCE_DIR= 11/jmuduo     # 指定当前层的CMakeLists.txt的，因此与层相关
            CMAKE_CURRENT_BINARY_DIR= 11/build/debug
  
        muduo/base/test/CMakeLists.txt: 
            PROJECT_SOURCE_DIR= 11/jmuduo
            PROJECT_BINARY_DIR= 11/build/debug
            CMAKE_SOURCE_DIR= 11/jmuduo
            CMAKE_BINARY_DIR= 11/build/debug
            CMAKE_CURRENT_SOURCE_DIR= 11/jmuduo/muduo/base/tests
            CMAKE_CURRENT_BINARY_DIR= 11/build/debug/muduo/base/tests
  
        muduo/base/CMakeLists.txt: 
            PROJECT_SOURCE_DIR= 11/jmuduo
            PROJECT_BINARY_DIR= 11/build/debug
            CMAKE_SOURCE_DIR= 11/jmuduo
            CMAKE_BINARY_DIR= 11/build/debug
            CMAKE_CURRENT_SOURCE_DIR= 11/jmuduo/muduo/base
            CMAKE_CURRENT_BINARY_DIR= 11/build/debug/muduo/base
    ```
  


### 函数
所有的函数列表中，`<>`表示的参数必须要有，`[]`表示的参数为可选。  
+ ***`set`***
    可以设置三个类型的变量值：正常变量，`cache variable`、环境变量。    
    + ` Normal Variable`:*`set(<variable> <value>... [PARENT_SCOPE])`*  
    + `cache`：`set(<variable> <value>... CACHE <type> <docstring> [FORCE])`
    + `env`：`set(ENV{<variable>} [<value>])`

+ ***`OPTION`***：提供用户可以选择的选项
    + 格式：`option(<variable> "description" [initial value])` 
    + 比如：
        ```cmake
            option(
                USE_MYPATH
                "user path"
                ON
            )
        ```
+ ***`aux_source_directory `***
    + 语法：`aux_source_directory(<dir> <variable>)`
    + 查找目录`dir`下的所有源文件(即.c, .cpp, .cc等文件)，并将名称保存到 `variable` 变量

+ ***`add_subdirectory `***
    + `add_subdirectory(source_dir [binary_dir] [EXCLUDE_FROM_ALL])`
    + 添加一个将被编译的子目录。指明`CMakeLists.txt`所在目录下包含了一个子目录`source_dir`。这样`source_dir`下的源文件和`CMakeLists.txt`等也会被处理。

+ ***`target_link_libraries  `***
    + `target_link_libraries(exec libs)`
    + 表示可执行程序`exec`需要链接到一个名为`libs`的链接库。 

+ ***`add_library `***
    + `add_library (name dir)`
    + 用在目录`dir`下的源文件生成一个名为`name`的静态链接库：`libname.a`

+ ***`configure_file`***
    + 加入一个配置头文件，用于处理 CMake 对源码的设置
        ```cmake
            configure_file (
                "${PROJECT_SOURCE_DIR}/config.h.in" # config.h.in文件目录
                "${PROJECT_BINARY_DIR}/config.h"    # config.h 生成的头文件目录
            )
        ```
        在配置文件`config.h`中，配置相关项，比如`options`中的`USE_MYPATH`：
        ```cmake
            #cmakedefine USE_MYMATH
        ```
+ ***`include`***  
    + `include(file [optional])`：读取`CMake`的相关文件。
    + ` include(moudle [optional])`  
        the file with name <modulename>.cmake is searched in the `CMAKE_MODULE_PATH`。
+ ***`include_directories`***
    ```cmake
        include_directories([AFTER|BEFORE] [SYSTEM] dir1 [dir2 ...])
    ```
    添加指定目录到编译器搜索路径。
+ ***`install`***  
    使用：`cmake`之后，`sudo make install`就可以执行相应的库和头文件的安装。  
    + `TARGET`格式
        ```cmake
        install(TARGETS targets...
                [[ARCHIVE|LIBRARY|RUNTIME]
                [DESTINATION <dir>]
                [PERMISSIONS permissions...]
                [CONFIGURATIONS [Debug|Release|...]]
                [COMPONENT <component>]  
                [OPTIONAL]
                ] [...])
        ```
    + `targets`的类型   
        可以安装的库有`[ARCHIVE|LIBRARY|RUNTIME]`三种：  
        &emsp;&emsp;1) 可执行程序视为`runtime`  
        &emsp;&emsp;2) 静态库视为`archieve`  
        &emsp;&emsp;3) `Module Library`视为`library`  
        &emsp;&emsp;4) 共享库和平台有关
    + 参数
        + `DESTINATION`：  
        指定一个文件将要被安装的目录。如果给的是一个全路径，那么就直接使用；如果是相对路径，默认是相对`CMAKE_INSTALL_PREFIX`,其值默认是`/usr/local/`。  
            &emsp;&emsp;1) 头文件:`inclide`    
            &emsp;&emsp;2) 可执行文件:`bin`  
            &emsp;&emsp;3) 库:`lib`  

        + `PERMISSIONS`： 指定安装文件的权限：  
            &emsp;&emsp;1) user&emsp;: ` OWNER_READ, OWNER_WRITE, OWNER_EXECUTE`  
            &emsp;&emsp;2) group：`GROUP_READ, GROUP_WRITE, GROUP_EXECUTE`  
            &emsp;&emsp;3) other：`WORLD_READ, WORLD_WRITE, WORLD_EXECUTE`  
            &emsp;&emsp;4) uid&emsp;：` SETUID, and SETGID`。 
        
        + `CONFIGURATIONS`：为安装规则建立一个配置文件列表。 
+ ***`install`***
    + `FILES`格式
        ```cmake 
        INSTALL(FILES files... 
                DESTINATION <dir>
                [PERMISSIONS permissions...]
                [CONFIGURATIONS [Debug|Release|...]]
                [COMPONENT <component>]
                [RENAME <name>] [OPTIONAL])
        ```
        + `files`：即文件名
+ 测试
    + ***`enanle_testing()`***：启动测试
    + ***`add_test(testname Exename arg1 arg2 ...)`***：  
        + 需要先运行测试程序`enanle_testing()`，这个指令才有效。  
        + `Exename`是可执行程序名，参数`arg1, arg2`。
    + ***`set_tests_properties(...)`***
        + 括号内格式：`(Exename [Exename2...] PROPERTIES prop1 value1 prop2 value2)`，其中`PROPERTIES`是固定的单词不能改
        + 为`Exename`设置属性，如果没有这个属性，就报错，有如下属性：  
            &emsp;&emsp;1) `WILL_FAIL`：如果设置为`true`，那么会反转测试结果的`pass/fail`标志。  
            &emsp;&emsp;2) `PASS_REGULAR_EXPRESSION`： 匹配正则表达式，只少有一个匹配，则`pass`
            &emsp;&emsp;2) `FAIL_REGULAR_EXPRESSION`： 匹配正则表达式，则`fail`
    + 宏测试  
        ```camke
            macro(<name> [arg1 [arg2 [arg3 ...]]])
                COMMAND1(ARGS ...)
                COMMAND2(ARGS ...)
                ...
            endmacro(<name>)
        ```
        就类似于写一个函数，用宏实现，调用：`name(arg1,arg2,...)`。
+ 设置项目的版本号
    + 在顶层的`CMakeLists.txt`中：    
        ```cmake
            # 加入版本号是 1.0
            set (Project_VERSION_MAJOR 1) # 主版本号
            set (Project_VERSION_MINOR 0) # 副版本号
        ```
    + 在配置文件`config.h.in`中设置：
        ```cmake
            #define Project_VERSION_MAJOR @Project_VERSION_MAJOR@
            #define Project_VERSION_MINOR @Project_VERSION_MINOR@
        ```
    + `main`函数中就可以直接使用这两个宏，代表版本号：
        ```c
            printf("Version %d.%d\n",
                    Project_VERSION_MAJOR,
                    Project_VERSION_MINOR);
        ```
+ 生成安装包  
  需要利用`CPack`工具，也是`CMake`提供的工具。
    + 先在顶层`CMakeLists.txt`中末尾添加：
        ```cmake
            # 构建一个 CPack 安装包
            include(InstallRequiredSystemLibraries)
            set (CPACK_RESOURCE_FILE_LICENSE
                "${CMAKE_CURRENT_SOURCE_DIR}/License.txt")
            set (CPACK_PACKAGE_VERSION_MAJOR "${Project_VERSION_MAJOR}")
            set (CPACK_PACKAGE_VERSION_MINOR "${Project_VERSION_MINOR}")
            include (CPack)
        ```
        + 导入`InstallRequiredSystemLibraries`模块，以便之后导入`CPack`模块
        + 设置一些`CPack`相关变量，包括版权信息和版本信息，其中版本信息用了上一节定义的版本号
        + 导入`CPack`模块
    + 生成二进制安装包：`cpack -C CPackConfig.cmake`
    + or 生成源码安装包
        + 格式：`cpack -C CPackSourceConfig.cmake`  
          在执行该命令的目录下得到：
            ```bash
                # Demo8是项目名
                $ ls -l | grep Demo8
                -rwxrwxrwx 1 szz szz  8631 Dec 12 22:03 Demo8-1.0.1-Linux.sh
                -rw-rw-r-- 1 szz szz  3709 Dec 12 22:03 Demo8-1.0.1-Linux.tar.gz
                -rw-rw-r-- 1 szz szz  4982 Dec 12 22:03 Demo8-1.0.1-Linux.tar.Z
            ````
        + 安装：`sh Demo8-1.0.1-Linux.sh`。  
          默认的安装路径：
            ```c
                By default the Demo8 will be installed in:
                "~/Study/SystemProgram/CMakeExe/Demo8/build/Demo8-1.0.1-Linux"
                
                Do you want to include the subdirectory Demo8-1.0.1-Linux?
                Saying no will install in: "~/Study/SystemProgram/CMakeExe/Demo8/build" [Yn]: 
            ```
        + 运行。安装后，就运行该程序
            ```bash
                $ ./Demo8-1.0.1-Linux/bin/Demo 2 5
                Now we use our own Math library. 
                2 ^ 5 is 32
            ```
        + Demo8-1.0.1-Linux下的目录结果
            ```bash
                Demo8-1.0.1-Linux
                ├── bin
                │   └── Demo        # 可执行程序
                ├── include         # 头文件
                │   ├── config.h
                │   └── MathFunctions.h
                └── lib             # 静态库
                    └── libMathFunctions.a
            ```
+ *`target_compile_definitions`*
    + 格式
        ```cmake
            target_compile_definitions(<target>
                                      <INTERFACE|PUBLIC|PRIVATE> [items1...]
                                      [<INTERFACE|PUBLIC|PRIVATE> [items2...] ...])
        ```
    + 作用：编译时定义的宏
+ *`string`*
    + `REPLACE`
        ```cmake
            string(REPLACE 
                  <match_string> <replace_string> 
                  <output_variable> <input> [<input>...])
        ```
        将所有`input`中出现的`match_String`替换为`replace_string`，并且将结果存在`output_variable`。
+ *`message`*
    ```cmake
        message([<mode>] "message to display" ...)
    ```
    + 显示信息给用户  
        `mode`取决于信息的类型：
        + `STATUS`：以简洁的方式显示用户感兴趣的信息。
            ```cmake
                message(STATUS 
                        "CXX_FLAGS = " 
                        ${CMAKE_CXX_FLAGS} 
                        " " 
                        ${CMAKE_CXX_FLAGS_${BUILD_TYPE}}
                        )
            ```
            可以理解为`printf`，把后面的几个信息以空格相间，然后打印出来。显示结果为(和上面对应分成三段):
            ```cmake
                CXX_FLAGS = 
                
                -g -D_FILE_OFFSET_BITS=64 -Wall -Wextra 
                -Werror -Wconversion -Wno-unused-parameter 
                -Wold-style-cast -Woverloaded-virtual 
                -Wpointer-arith -Wshadow -Wwrite-strings 
                -march=native -rdynamic 
                
                -O0
            ```

+ *`find_package`*
    ```cmake 
        find_package(<PackageName> 
                    [version] [EXACT] [QUIET] [MODULE]
                    [REQUIRED] [[COMPONENTS] [components...]]
                    [OPTIONAL_COMPONENTS components...]
                    [NO_POLICY_SCOPE])
    ```
    主要是寻找和加载外部项目。如果`PackageName`找到了，`PackageName-found`会显出，当没有找到时，默认显示
    `PackageName-not found`。通过模式的选择，可以处理在没有找到包时的解决方案。
    + `QUIET`：不显示有用信息，
    + `REQUIRED`：报错
+ *`find_path`*
    ```cmake
        find_path (<VAR> name0|NAMES name1 [path1 path2 ...])
    ```
    用以寻找包含着`name1`文件的目录，如果找到了结果存储在`VAR`，没有找到结果结果是`VAR-not found`。成功时，变量被清除`find_path`再次搜索，没有成功,`fin_path`再次以相同的变量被调用时搜索。

+ *`find_library`*  
    同上`find_path`
    ```cmake 
        find_library (<VAR> name0|NAMES name1 [path1 path2 ...])
    ```
    + OPTIONS
        + `NAMES`  
           为`library`指定一个或多个可能的名字。
---
+ 参考
    + [CMake官方文档](https://cmake.org/cmake/help/cmake2.4docs.html)
    + [CMake API搜索](https://cmake.org/cmake/help/latest/search.html?q=)
    + [CMake tutorial](https://cmake.org/cmake/help/latest/guide/tutorial/index.html)