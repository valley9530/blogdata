---
title: backjoon_1992
date: 2020-11-19 00:00:00
tags: [backjoon]
categories:
- [backjoon]
---

백준 1992 쿼드트리 분할정복 python 파이썬
[백준1992문제](https://www.acmicpc.net/problem/1992)

{% codeblock lang:python %}
a=int(input())
jong=[]
ahp=""
for i in range(a):
    jong.append(input())
def jal(list1,k):
    global ahp
    cnt=0
    s=int(k/2)

    for l in range(k):
        for l2 in range(k):
            if list1[l][l2]=="1":
                cnt+=1
    if cnt==(k*k):
           ahp+="1"
           return
    if cnt==0:
           ahp+="0"
           return
    else:
        ahp+="("
        paper1 = []
        paper2 = []
        paper3 = []
        paper4 = []
        for i in range(0, s):
            paper1.append(list1[i][:s])
            paper2.append(list1[i][s:])
            paper3.append(list1[s+i][:s])
            paper4.append(list1[s + i][s:])
        jal(paper1, s)
        jal(paper2, s)
        jal(paper3, s)
        jal(paper4, s)
        ahp+=")"
jal(jong,a)
print(ahp)

{% endcodeblock %}
