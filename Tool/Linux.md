## 命令

### 文件和目录管理基本命令

- ls 命令

  > 显示目标列表或目录的内容

  语法

  ```
  ls [参数] [目录或文件]
  ```

  参数

  | 参数 | 说明                                                         |
  | ---- | ------------------------------------------------------------ |
  | -a   | 显示指定目录下的所有子目录与文件，包括隐藏文件               |
  | -l   | 显示文件的详细信息                                           |
  | -d   | 显示目录                                                     |
  | -r   | 将文件以相反次序显示（原定依英文字母次序）                   |
  | -t   | 将文件依建立时间之先后次序列出                               |
  | -A   | 同 -a ，但不列出 "." （目前目录）及 ".." （父目录）          |
  | -F   | 在列出的文件名称后加一符号；例如可执行档则加 "*", 目录则加 "/" |
  | -R   | 若目录下有文件，则以下之文件亦皆依序列出                     |

- cd 命令

  > 切换工作目录

  语法

  ```shell
  $ cd [directory]
  ```

- pwd 命令

  > 显示当前工作目录的路径

  语法

  ```shell
  $ pwd
  ```

- mkdir 命令

  > 创建一个空目录

  语法

  ```shell
  $ mkdir [参数] dirname
  ```

  参数

  | 参数 | 说明                                                         |
  | ---- | ------------------------------------------------------------ |
  | -m   | 在创建新目录的同时设置目录权限，默认权限：755                |
  | -p   | 在创建新目录时，若所要建立目录的上层目录目前尚未建立，则一并建立上层目录 |

- touch 命令

  > 修改文件的创建日期或以当前系统日期创建一个空文件

  语法

  ```shell
  $ touch file1 file2 ...
  ```
