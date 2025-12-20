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

<img width="659" height="128" alt="图片" src="https://github.com/user-attachments/assets/7385ae04-f719-44ed-8069-973e9615b424" />
<img width="659" height="128" alt="图片" src="https://github.com/user-attachments/assets/7b63c1d6-9d51-4c1c-9086-215d9fce056a" />


nginx test

<img width="659" height="128" alt="图片" src="https://github.com/user-attachments/assets/883b487f-51f3-49c3-a728-243e7c1aa286" />

cinatra test

<img width="659" height="128" alt="图片" src="https://github.com/user-attachments/assets/97bb7fa2-3dc7-47f4-acd7-778ebb4046db" />

step 2. coroutine api

        协程基本封装完成 The basic functionality of the coroutine is complete.
        参考 https://github.com/bugwang/coo fork from https://github.com/avplayer/ucoro 
请访问 [ucoro](https://github.com/avplayer/ucoro) 
<a href="https://github.com/bugwang/coo"> coo </a>

step 3. server + coroutine

        start ... 
