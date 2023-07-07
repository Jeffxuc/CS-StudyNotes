[LeetCode：替换空格](https://leetcode.cn/problems/ti-huan-kong-ge-lcof/description/)

请实现一个函数，把字符串 s 中的每个空格替换成 "%20"。

**示例**
>输入：s = "We are happy."
输出："We%20are%20happy."

---
解析：
本题可以直接借助额外空间，如vector来将新的元素存放在其中达到目的。但是也可以不借助额外空间，直接对原有的容器进行扩容，然后用双指针的方式来将其从后面进行填充，进而实现替换空格。从后往前填充的目的是避免了每次从前向后填充后，要移动后面的所有元素。

```cpp
string replaceSpace(string s)
{
    int spCnt = 0;
    int oldLen = s.size();

    //遍历容器，计算空格的数量
    for (auto i : s)
    {
        if (i == ' ')
            spCnt++;
    }

    int newLen = s.size() + 2 * spCnt;
    s.resize(newLen); //扩容重置容器的大小，以存放更新后的元素

    for (int i = oldLen - 1, j = newLen - 1; i >= 0; i--, j--)
    {
        if (s[i] == ' ')
        {
            //注意此处的替换是从后向前，所以要是 02% 的顺序
            s[j] = '0';
            s[j - 1] = '2';
            s[j - 2] = '%';
            j -= 2;
        }
        else
        {
            s[j] = s[i];
        }
    }

    return s;

}
```












