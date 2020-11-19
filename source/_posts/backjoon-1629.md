---
title: backjoon_1629
date: 2020-11-20 00:00:00
tags: [backjoon]
categories:
- [backjoon]
---

백준 1629 곱셈 분할정복 python 파이썬
[백준1629문제](https://www.acmicpc.net/problem/1629)

{% codeblock lang:python %}
a=list(map(int,input().split()))
b=a[0]%a[2]
c=a[1]
cnt=1
su=b
dp=[b]
while c>cnt:
    su=(su*su)%a[2]
    cnt=cnt+cnt
    dp.append(su)
su=1

for i in range(len(dp)):

    if c==0:
        break
    if c>=(2**(len(dp)-i-1)):
        c=c-(2**(len(dp)-i-1))
        su=(su*dp[len(dp)-1-i])%a[2]

print(su)
{% endcodeblock %}
