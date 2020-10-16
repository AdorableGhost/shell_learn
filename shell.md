# Shell 

- bc 数值计算.
  - 示例: `echo "scale=3; 1/13"  | bc`
- printf 输出数值.
  - 示例: `printf "imr lallaa"`
- $0 在shell 中表示输入调用的本身
  
### awk

- awk、sed、grep更适合的方向：

    -  grep 更适合单纯的查找或匹配文本
    -  sed 更适合编辑匹配到的文本
    -  awk 更适合格式化文本，对文本进行较复杂格式处理
- 关于awk内建变量个人见解，简单易懂

- 变量：

- 变量：分为内置变量和自定义变量;输入分隔符FS和输出分隔符OFS都属于内置变量。

- 内置变量就是awk预定义好的、内置在awk内部的变量，而自定义变量就是用户定义的变量。

  1. FS(Field Separator)：输入字段分隔符， 默认为空白字符
  2. OFS(Out of Field Separator)：输出字段分隔符， 默认为空白字符
  3. RS(Record Separator)：输入记录分隔符(输入换行符)， 指定输入时的换行符
  4. ORS(Output Record Separate)：输出记录分隔符（输出换行符），输出时用指定符号代替换行符
  5. NF(Number for Field)：当前行的字段的个数(即当前行被分割成了几列)
  6. NR(Number of Record)：行号，当前处理的文本行的行号。
  7. FNR：各文件分别计数的行号
  8. ARGC：命令行参数的个数
  9. ARGV：数组，保存的是命令行所给定的各参数
- 自定义变量的方法

  - 方法一：-v varname=value ，变量名区分字符大小写。
  - 方法二：在program中直接定义。

- seq 用于产生从某个数到另外一个数之间的所有整数

  - 用法：seq [选项]... 尾数
    -  或：seq [选项]... 首数 尾数 或：seq [选项]... 首数 增量 尾数

  - 选项：

    -  -f, --format=FORMAT      use printf style floating-point FORMAT
    -  -s, --separator=STRING   use STRING to - - separate numbers (default: \n)
    - -w, --equal-width        equalize width by padding with leading zeroes

- 补充：在 Bash 版本 3 以上，在 for 循环的 in 后面，可以直接通过 {1..5} 更简洁地产生自 1 到 5 的数字（注意，1 和 5 之间只有两个点），例如：

    - `$ for i in {1..5}; do echo -n "$i "; done
1 2 3 4 5`

- sed 命令 ,行编辑命令

    - 语法: `sed [-hnV][-e<script>][-f<script文件>][文本文件]`
  
    - 参数说明
      - `-e<script>或--expression=<script> 以选项中指定的script来处理输入的文本文件。`
      - `-f<script文件>或--file=<script文件> 以选项中指定的script文件来处理输入的文本文件。`
      - `-h或--help 显示帮助。`
      -` -n或--quiet或--silent 仅显示script处理后的结果`。
      - `-V或--version 显示版本信息。`

    - 动作说明:
        ```
        a ：新增， a 的后面可以接字串，而这些字串会在新的一行出现(目前的下一行)～
        c ：取代， c 的后面可以接字串，这些字串可以取代 n1,n2 之间的行！
        d ：删除，因为是删除啊，所以 d 后面通常不接任何咚咚；
        i ：插入， i 的后面可以接字串，而这些字串会在新的一行出现(目前的上一行)；
        p ：打印，亦即将某个选择的数据印出。通常 p 会与参数 sed -n 一起运行～
        s ：取代，可以直接进行取代的工作哩！通常这个 s 的动作可以搭配正规表示法！例如 1,20s/old/new/g 就是啦！
        ```

- sort 命令
  - 用法：sort [选项]... [文件]...
  - 排序选项：

    ```
    -b, --ignore-leading-blanks 忽略前导的空白区域
    -d, --dictionary-order 只考虑空白区域和字母字符
    -f, --ignore-case 忽略字母大小写
    -g, --general-numeric-sort 按照常规数值排序
    -i, --ignore-nonprinting 只排序可打印字符
    -n, --numeric-sort 根据字符串数值比较
    -r, --reverse 逆序输出排序结果
    ```

  - 其他选项：

    ```
    -c, --check, --check=diagnose-first 检查输入是否已排序，若已有序则不进行操作
    -k, --key=位置1[,位置2] 在位置1 开始一个key，在位置2 终止(默认为行尾)
    -m, --merge 合并已排序的文件，不再进行排序
    -o, --output=文件 将结果写入到文件而非标准输出
    -t, --field-separator=分隔符 使用指定的分隔符代替非空格到空格的转换
    -u, --unique 配合-c，严格校验排序；不配合-c，则只输出一次排序结果
    ```

- $? 是一个特殊变量，存放有上一次进程的结束状态（退出状态码）。
- shell 中 true 为0 ,false 为1


-  test 函数 : 数值测试（各种数值属性测试）、字符串测试（各种字符串属性测试）、文件测试（各种文件属性测试）
- 数值测试:
    ```
    -eq	等于则为真
    -ne	不等于则为真
    -gt	大于则为真
    -ge	大于等于则为真
    -lt	小于则为真
    -le	小于等于则为真

    ```
- 代码中的 [] 执行基本的算数运算，如：
    ```
    #!/bin/bash

    a=5
    b=6

    result=$[a+b] # 注意等号两边不能有空格
    echo "result 为： $result"

    ```

- 字符串测试
    ```
    =	等于则为真
    !=	不相等则为真
    -z 字符串	字符串的长度为零则为真
    -n 字符串	字符串的长度不为零则为真
    ```

- 文件测试
    ```
    -e 文件名	如果文件存在则为真
    -r 文件名	如果文件存在且可读则为真
    -w 文件名	如果文件存在且可写则为真
    -x 文件名	如果文件存在且可执行则为真
    -s 文件名	如果文件存在且至少有一个字符则为真
    -d 文件名	如果文件存在且为目录则为真
    -f 文件名	如果文件存在且为普通文件则为真
    -c 文件名	如果文件存在且为字符型特殊文件则为真
    -b 文件名	如果文件存在且为块特殊文件则为真
    ```
- 特殊字符串
    ```
    /dev/null 和 /dev/zero 设备非常有趣，都犹如黑洞，什么东西掉进去都会消失殆尽；后者还是个能源箱，总能从那里取到0，直到退出
    [[:space:]] 是 grep 用于匹配空格或 TAB 键字符的标记，其他标记请查帮助：man grep
    上面都是用 grep 来进行模式匹配，实际上 sed，awk 都可用来做模式匹配，关于匹配中用到的正则表达式知识，请参考后面的相关资料
    如果想判断字符串是否为空，可判断其长度是否为零，可通过 test 命令的 -z 选项来实现，具体用法见 test 命令，help test
    ```

- 计算字符串的长度
  - `echo ${#var}`
  - `expr length "$var"`
  - ` echo $var | awk '{printf("%d\n", length($0));}'`
  - ` echo -n $var |  wc -c`


- wc 命令
  - wc命令的功能为统计指定文件中的字节数、字数、行数, 并将统计结果显示输出。 
    ```

    - c 统计字节数。 

    - l 统计行数。 

    - w 统计字数。 

    这些选项可以组合使用。 

    输出列的顺序和数目不受选项的顺序和数目的影响。总是按下述顺序显示并且每项最多一列。 

    行数、字数、字节数、文件名 

    如果命令行中没有文件名，则输出中不出现文件名。 
    ```

- tr 命令 tr，translate的简写，主要用于压缩重复字符，删除文件中的控制字符以及进行字符转换操作。

- 语法:` tr [OPTION]... SET1 [SET2]`

    ```
    -s 替换重复的字符

    　　-s： squeeze-repeats，用SET1指定的字符来替换对应的重复字符 （replace each input sequence of  a  repeated  character  that  is listed in SET1 with a single occurrence of that character）

    -d 删除字符

    　　-d：delete，删除SET1中指定的所有字符，不转换（delete characters in SET1, do not translate）

    -t 字符替换

    　　-t：truncate，将SET1中字符用SET2对应位置的字符进行替换，一般缺省为-t

    -c 字符补集替换

    　　-c：complement，用SET2替换SET1中没有包含的字符
    ```