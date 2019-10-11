---
title: LeetCode - Regular Expression Matching
date: 2017-09-04T01:16:50.000Z
categories: Study
tags:
- leetcode
---

## Problem

Implement regular expression matching with support for`'.'`and`'*'`.

`'.'`Matches any single character. `'*'`Matches zero or more of the preceding element.

<!--more-->

The matching should cover the entire input string (not partial).

The function prototype should be: bool isMatch(const char \*s, const char \*p)

-   Example

```
isMatch("aa","a") → false 
isMatch("aa","aa") → true 
isMatch("aaa","aa") → false 
isMatch("aa", "a\*") → true 
isMatch("aa", ".\*") → true 
isMatch("ab", ".\*") → true 
isMatch("ab", "c\*ab") → true
```

<!--more-->

## Solution

Similar to regular expression matching, but this problem is a little weird:

1. The first line of the string will not contain `'.'`和`'*'`. Otherwise the difficulty will skyrocket.
2. The `'*'` can match ZERO characters! Did not pay attention at first, wasted for half an hour.

So what is the correct way to deal with this? It is obviously the recursion of DP, but there are many boundaries necessary to care.

Important optimization: I saw the code of the Ace and found that I don't need to judge the end. It can be judged while walking.

## Code

```python
# -*- coding: utf-8 -*-
class Solution(object):
    def isMatch1(self, ss, pp):
        """
        :type s: str
        :type p: str
        :rtype: bool
        """
        
        global s, p
        s = ss + '\n'
        p = pp + '\n'

        def match(sn, pn):
            if p[pn] == '\n':
                return s[sn] == '\n'

            else:
                if len(p) - pn == 1 or p[pn + 1] != "*":
                    if len(s) - 1 > sn and (s[sn] == p[pn] or p[pn] == '.'):
                        return match(sn + 1, pn + 1)
                    else:
                        return False
                else:
                    while sn < len(s) - 1 and (s[sn] == p[pn] or p[pn] == '.'):
                        if match(sn, pn + 2):
                            return True
                        else:
                            sn += 1
                    else:
                        return match(sn, pn + 2)

        return match(0, 0)

    def isMatch2(self, s, p):
        """
        :type s: str
        :type p: str
        :rtype: bool
        """
        if not p:
            return not s

        if len(p) == 1 or p[1] != '*':
            if len(s) > 0 and (p[0] == s[0] or p[0] == '.'):
                return self.isMatch(s[1:], p[1:])
            else:
                return False

        else:
            while len(s) > 0 and (p[0] == s[0] or p[0] == '.'):
                if self.isMatch(s, p[2:]):
                    return True
                s = s[1:]
            return self.isMatch(s, p[2:])


if __name__ == '__main__':
    print(Solution().isMatch1("aab", "a*c*a*ab"))
```
