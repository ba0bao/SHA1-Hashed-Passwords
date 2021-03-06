# SHA1-Hashed Passwords
   SHA1函数的应用之一是用户密码的校验。服务器通常不直接存储用户密码，而是存储其哈希值，每次用户输入密码时，
计算并比较其哈希值是否正确。本题基于这一背景，并给出了用户密码的哈希值，要求破解其密码。
   题目给出一个用户的密码的SHA1哈希值：67ae1a64661ac8b4494666f58c4822408dd0a3e4
要求破解其密码。同时题目还给出了用户输入密码进行一次成功登录的键盘的按键情况
SHA1是一种单向散列函数，在仅仅知道明文的散列值的情况下想要破解出明文是很难做到的。对于本题来说，如果只知道密码的散列值，
不知道密码的长度、组成字符等信息的话，要想恢复出用户密码也是很难做到的，好在本题给出了用户输入密码的键盘记录。题目给出的
是一个德国键盘，与我们平时用的键盘不同。同时题目也说明，此用户用的系统通过键盘的方向键来操作，所以我们可以认为方向键和
小键盘的2、4、6、8均不是密码的组成部分。同时根据德国键盘的特点，要输入某个键的第三个值，比如图中（* + ~）的‘~’，要用到‘Alt Gr’键，
图中并没有用到。所以现在基本可以确定密码的组成范围是：
 ['=','0']，['(','8']，['%','5']，['*','+']，['w','W']，['n','N']，['i','I']，['q','Q']，
暂时假定每个键使用一次，密码是8位的。接下来进行暴力破解。

本次代码用到了python的itertools库
函数product：计算笛卡尔积
函数permutations：全排列