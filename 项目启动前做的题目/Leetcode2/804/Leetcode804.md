# leetCode 804

## 题目描述：

国际摩尔斯密码定义一种标准编码方式，将每个字母对应于一个由一系列点和短线组成的字符串， 比如: "a" 对应 ".-", "b" 对应 "-...", "c" 对应 "-.-.", 等等。

为了方便，所有26个英文字母对应摩尔斯密码表如下：
```
[".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]
```
给定一个单词列表，每个单词可以写成每个字母对应摩尔斯密码的组合。例如，"cab" 可以写成 "-.-..--..."，(即 "-.-." + "-..." + ".-"字符串的结合)。我们将这样一个连接过程称作单词翻译。

返回我们可以获得所有词不同单词翻译的数量。

例如:
```
输入: words = ["gin", "zen", "gig", "msg"]
输出: 2
解释: 
各单词翻译如下:
"gin" -> "--...-."
"zen" -> "--...-."
"gig" -> "--...--."
"msg" -> "--...--."
```
共有 2 种不同翻译, "--...-." 和 "--...--.".
 

注意:

+ 单词列表words 的长度不会超过 100。
+ 每个单词 words[i]的长度范围为 [1, 12]。
+ 每个单词 words[i]只包含小写字母。

## solution@dunmin:
C++:
```
class Solution {
public:
    int uniqueMorseRepresentations(vector<string>& words) {
        vector<string> mapTostr = {".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."};
        vector<string> encryptStr;
        //encrypt the words
        for(int i=0;i<words.size();i++){
            string mid = "";
            for(int j=0;j<words[i].size();j++)
                mid.append(mapTostr[words[i][j]-'a']);
            encryptStr.push_back(mid);
        }
        
        //compare the words
        sort(encryptStr.begin(),encryptStr.end());
        
        //special case
        if(encryptStr.size()==0) return 0;
        
        //nomal case
        int coun = 1;
        for(int i=1;i<encryptStr.size();i++){
            if(encryptStr[i]!=encryptStr[i-1])
                coun++;
        }
        return coun;
    }
};
```

```
point:
注意最后翻译完求加密后的序列有多少组是不同的，不需要任意两组之间都比较，只要排序后，每一组和前一组相比较就可以了
```

## 说明@dunmin:
```
简单题
```