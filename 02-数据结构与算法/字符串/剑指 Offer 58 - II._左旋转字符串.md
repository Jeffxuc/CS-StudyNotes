[LeetCode: 剑指 Offer 58 - II. 左旋转字符串](https://leetcode.cn/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof/description/)


字符串的左旋转操作是把字符串前面的若干个字符转移到字符串的尾部。请定义一个函数实现字符串左旋转操作的功能。比如，输入字符串"abcdefg"和数字2，该函数将返回左旋转两位得到的结果"cdefgab"。

**示例**
>输入: s = "abcdefg", k = 2
输出: "cdefgab"

>输入: s = "lrloseumgh", k = 6
输出: "umghlrlose"

----
解析

本题可以借助于额外空间，也可以直接在原来的字符串上进行操作。直接在原字串上进行操作的方式为：
1. 先将字串以 k 为分界点，看成两个字子串，分别对两个字子串进行反转。
2. 再对整个字串进行反转，结果即为左旋转的字串

```cpp
string reverseLeftWords(string s, int n)
{
    reverse(s.begin(), s.begin() + n);
    reverse(s.begin() + n, s.end());
    reverse(s.begin(), s.end());

    return s;
}
```



