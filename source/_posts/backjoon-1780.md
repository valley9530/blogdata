---
title: backjoon_1780
date: 2020-11-20 00:00:00
tags: [backjoon]
categories:
- [backjoon]
---

백준 1780 종이의 개수 분할정복 python 파이썬
[백준1780문제](https://www.acmicpc.net/problem/1780)

{% codeblock lang:python %}
a=int(input())
jong=[]
ahp=""
l1=0
l22=0
l3=0
for i in range(a):
    jong.append(list(map(int,input().split())))
def jal(list1,k):
    global l1,l22,l3
    cnt=0
    zerocnt=0
    s=int(k/3)

    for l in range(k):
        for l2 in range(k):
                cnt+=list1[l][l2]
                if list1[l][l2]!=0:
                    zerocnt=1
    if cnt==(k*k):
           l3+=1
           return
    if zerocnt==0:
           l22+=1
           return
    if cnt==-(k*k):
           l1+=1
           return
    else:
        paper11 = []
        paper12 = []
        paper13 = []
        paper21 = []
        paper22 = []
        paper23 = []
        paper31 = []
        paper32 = []
        paper33 = []

        for i in range(s):
            paper11.append(list1[i][:s])
            paper12.append(list1[i][s:2*s])
            paper13.append(list1[i][2*s:])
            paper21.append(list1[s + i][:s])
            paper22.append(list1[s + i][s:2*s])
            paper23.append(list1[s + i][2*s:])
            paper31.append(list1[2*s+i][:s])
            paper32.append(list1[2*s+i][s:2*s])
            paper33.append(list1[2*s+i][2*s:])
        jal(paper11, s)
        jal(paper12, s)
        jal(paper13, s)
        jal(paper21, s)
        jal(paper22, s)
        jal(paper23, s)
        jal(paper31, s)
        jal(paper32, s)
        jal(paper33, s)

jal(jong,a)
print(l1)
print(l22)
print(l3)

{% endcodeblock %}
