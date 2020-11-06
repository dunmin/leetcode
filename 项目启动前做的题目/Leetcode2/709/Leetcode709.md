# leetCode 709

## 题目描述：

实现函数 ToLowerCase()，该函数接收一个字符串参数 str，并将该字符串中的大写字母转换成小写字母，之后返回新的字符串。

示例 1：

```
输入: "Hello"
输出: "hello"
```
示例 2：
```
输入: "here"
输出: "here"
```
示例 3：
```
输入: "LOVELY"
输出: "lovely"
```

## solution@dunmin:
C++:
```
class Solution {
public:
    string toLowerCase(string str) {
        for(int i=0;i<str.length();i++){
            if(str[i]>='A'&&str[i]<='Z'){
                str[i]+='a'-'A';
            }
        }
        return str;
    }
};
```

## 说明@dunmin:
```
简单题
```