---
title: backjoon_2630
date: 2020-11-20 00:00:00
tags: [backjoon]
categories:
- [backjoon]
---

백준 2630 분할정복 색종이 만들기 python 파이썬
[백준2630문제](https://www.acmicpc.net/problem/2630)

{% codeblock lang:python %}
a=int(input())
jong=[] #종이를 받아올 리스트
blu=0 #파랑종이
whi=0 #하아얀 종이
for i in range(a):
    jong.append(list(map(int,input().split())))

def jal(list1,k):#종이가 파란종이 or 하얀종이인지 판단 후
                 #둘다 아닐경우 4 등분 후 자르기 실행
    cnt=0
    s=int(k/2)
    global blu, whi
    for l in range(k):
        for l2 in range(k):
            if list1[l][l2]==1:
                cnt+=1
    if cnt==(k*k):
           blu+=1
           return
    if cnt==0:
           whi+=1
           return
    else: #4등분
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

jal(jong,a)
print(whi) #출력
print(blu)
{% endcodeblock %}
