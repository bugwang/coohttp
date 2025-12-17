# coohttp

The goal is to hunt and kill the microservices of go.
本项目最终目标就是干掉 go 在web或者http的微服务架构。

idea：
http server ，http client api:
use epoll 
use pool
use coroutine
and don't depend on third party or only header file.

yes, i need time

desc：

        server
        one loop per pthread  - > one coro of pool per loop -> ( one request one coro)  for  parallel request hander

        hander
        aio or coio for one request and thread safe  (one request -> more demand -> parallel demand per coro -> one reply) 

step 1. no coroutine

<img width="659" height="130" alt="图片" src="https://github.com/user-attachments/assets/bc6081e6-02e0-42fd-a710-37940f1bd219" />

<img width="659" height="132" alt="图片" src="https://github.com/user-attachments/assets/d0912744-bb77-4fd7-b6f6-1387f4dff55e" />

nginx test

<img width="659" height="129" alt="图片" src="https://github.com/user-attachments/assets/883b487f-51f3-49c3-a728-243e7c1aa286" />


step 2. coroutine api
        协程基本封装完成 The basic functionality of the coroutine is complete.
        参考 https://github.com/bugwang/coo fork from https://github.com/avplayer/ucoro

step 3. server + coroutine
        start ... 
