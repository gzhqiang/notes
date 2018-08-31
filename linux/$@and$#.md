Linux shell 脚本中， $@ 和$# 分别是：

$@：表示所有脚本参数的内容

$#:表示返回所有脚本参数的个数。
示例：编写如下shell脚本，保存为test.sh

#!/bin/sh

echo "number:$#"

echo "argume:$@"

执行脚本:

./test.sh first_arg second_arg