* 命令格式 awk [-F] 'BEGIN{ command }{command}END{command}' input-file
  > 其中BEGIN{} 、{}、 END{}、都是可选的，但是必须在单引号内
* 默认分隔符是空格 分行符是\n 在单引号内通过 ${index} 使用 比如第一个为 $1
* 内置变量（可修改 ） e.g. : awk [-F] 'BEGIN{ FS="#" }{command}END{command}' input-file
  * FILENAME：用于保存输入文件的文件名称。
  * NF：用于保存当前正在处理的记录的域个数。
  * NR：用于保存从文本中读取记录的个数。
  * FNR：用于保存当前读取的记录数。当输入的文件有多个时，读取新文件时，awk会重置这个变量。
  * OFS：用于设置输出分隔字段的字符，默认为空格。
  * FS：用于设置字段分隔符。
  * ORS：用于设置输出记录分隔符，默认为新的一行。
  * RS：用于设置记录分隔符，默认为新行。
  * OFMT：数字的输出格式。
  * ENVIRON：读取环境变量。
* 简单流程判断格式
  * 正则判断 awk '/reg/{command}' input-file
  * 域值判断 awk '$1=="str"{command}' input-file
  * 域值正则判断 awk '$1 (!)~/reg/{command}' input-file
  * 混合判断（要有括号） awk '（$1 (!)~/reg/ && $2=="str"){command}' input-file
* 自定义变量
  * 在BEGIN中定义 awk 'BEGIN{A=0}{A+=$1}'
  * 在参数中定义 awk '$1==VAR{}' VAR="str" input-file
* 复杂流程控制
  * if( expression ) statement [ else statement ]
  * while( expression ) statement
  * for( expression ; expression ; expression ) statement
  * for( var in array ) statement
  * do statement while( expression )
  * break
  * continue
  * { [ statement ... ] }
  * expression              # commonly var = expression
  * print [ expression-list ] [ > expression ]
  * printf format [ , expression-list ] [ > expression ]
  * return [ expression ]
  * next                    # skip remaining patterns on this input line
  * nextfile                # skip rest of this file, open next, start at top
  * delete array[ expression ]# delete an array element
  * delete array            # delete all elements of array
  * exit [ expression ]     # exit immediately; status is expression
* 内置函数
  * 数学函数 exp, log, sqrt, sin, cos, and atan2 
  * length 作为字符串的参数的长度，如果没有参数，则为$0。
  * rand   随机数（0,1）
  * srand  为rand设置种子并返回前一个种子。
  * int    截断为整数值
  * substr(s, m, n) s的n个字符的子字符串，从位置m开始，从1开始计数。
  * index(s, t) 字符串t出现在s中的位置。
  * match(s, r) 正则表达式r出现在s中的位置，否则不为0。变量RSTART和RLENGTH设置为匹配字符串的位置和长度。
  * split(s, a, fs) 将字符串s拆分为数组元素a [1]，a [2]，...，a [n]，并返回n。如果不指定fs，则使用常规表达式fs或使用字段分隔符FS进行分隔。空字符串作为字段分隔符会将字符串分成每个字符一个数组元素。
  * sub(r, t, s) 将t替换为字符串s中第一次出现的正则表达式r。如果未给出s，则使用$ 0。
  * gsub  除了替换所有出现的正则表达式外，与sub相同； sub和gsub返回替换的数量
  * sprintf(fmt, expr, ... ) 根据printf（3）格式fmt格式化expr ...所得的字符串
  * system(cmd) 执行cmd并返回其退出状态
  * tolower(str) 返回str的副本，其中所有大写字符均转换为对应的小写字母。 
  * toupper(str) 返回str的副本，其中所有小写字符均转换为对应的大写字母。
