---
title: backjoon_10866
date: 2020-11-18 23:42:14
tags: [backjoon]
categorries:
- [backjoon]
---

백준 10866 deque구현 python 파이썬
[백준10866문제](https://www.acmicpc.net/problem/10866)

{% codeblock lang:python %}
class deque:
   def __init__(self):
       self.deque =[]
       self.start=0
       #리스트의 형태로 deque를 만들었다
       #deque의 앞 뒤에서 데이터가 들어올때
       #앞은 start를 옮김으로 데이터를 처리하고
       #뒤는 데이터를 삭제하고 붙임으로 해결하였다.

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

 # 문제에서 요구한 내용으로 작성하였다.
q=deque()
b=int(input()) #들어오는 입력의 수
for i in range(b):
         a=sys.stdin.readline().split()  #입력의 수만큼 입력을 받는다.
         #이문제는 input()을 사용하면 파이썬에서는 시간 초과가 발생한다 따라서 sys 모듈을 사용한다.
         if len(a)==2:
             if a[0]=="push_front":
                 q.push_front(int(a[1]))
             if a[0]=="push_back":
                 q.push_back(int(a[1]))
         if a[0]=="pop_front":
             print(q.pop_front())
         if a[0]=="pop_back":
             print(q.pop_back())
         if a[0]=="size":
             print(q.size())
         if a[0]=="empty":
             print(q.empty())
         if a[0]=="front":
             print(q.front())
         if a[0]=="back":
             print(q.back())


{% endcodeblock %}
