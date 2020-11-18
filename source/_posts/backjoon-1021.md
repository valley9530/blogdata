---
title: backjoon_1021
date: 2020-11-19 01:00:00
tags: [backjoon]
categorries:
- [backjoon]
---

백준 1021 deque구현 python 파이썬
[백준1021문제](https://www.acmicpc.net/problem/1021)

{% codeblock lang:python %}

class deque: #deque 이 다
    def __init__(self):
        self.deque =[]
        self.start=0

    def push_front(self,a):
        self.deque.insert(self.start,a)
        return

    def push_back(self,a):
        self.deque.append(a)

        return

    def pop_front(self):
        if len(self.deque[self.start:])==0:
         return -1
        self.start+=1
        return self.deque[self.start-1]

    def pop_back(self):
        if len(self.deque[self.start:])==0:
         return -1
        a=self.deque[-1]
        del(self.deque[-1])
        return a

    def size(self):   
        return len(self.deque[self.start:])

    def empty(self):
        if len(self.deque[self.start:])==0:
         return 1
        else:
         return 0

    def front(self):
        if len(self.deque[self.start:])==0:
         return -1
        return self.deque[self.start]
    def back(self):
        if len(self.deque[self.start:])==0:
         return -1
        return self.deque[-1]

q=deque()#
cnt=0
a,b =map(int,input().split())

for i in range(a):#deque 에 a만큼 숫자를 넣어준다.
    q.push_back(i+1)

for i  in list(map(int,input().split())): #제거해줄 숫자를 입력받는다.

    dequee=q.deque[q.start:]
    ii=dequee.index(i)+1

    if (q.size()-ii+1)<=(ii-1): #앞으로 입력받은 수가 앞으로움직이는 횟수와 뒤로 움직이는 횟수를 비교한다.
        for k in range(q.size()-ii+1):
         q.push_front(q.pop_back()) #오른쪽으로 움직이는 행위
         cnt+=1
    else:
        if q.front()==i:
            pass
        else:
         for k in range(ii-1):
            q.push_back(q.pop_front())#왼쪽으로 움직이는 행 위
            cnt+=1

    q.pop_front()#제거할 수가 deque의 맨 앞에 있으므로 pop_front 한다.  
print(cnt)



{% endcodeblock %}
