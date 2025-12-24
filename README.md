# coohttp

The goal is to hunt and kill the microservices of go.(hate and distaste for go's syntax)

本项目最终目标就是干掉 go 在web或者http的微服务架构（就是因为极其恶心go的语法）。

github上很多优秀的http架构。不过存在几个问题：

C++架构：过度封装，泛化模版 对半C/半C++ 的 很不友好，特别那些什么骆驼匈牙利命名法。

C架构：  过于细碎，语言本身带来的开发效率问题，对现代业务快速发展变化生态很不友好。


idea：
http server ，http client api:
use epoll 
use pool
use coroutine
and don't depend on third party or only header file.

yes, i need time

目前只是demo，经过性能测试目前已经世界级，特别C++里 TOP Level，不过还无法在生产环境使用。

desc：

        server
        one loop per pthread  - > one coro of pool per loop -> ( one request one coro)  for  parallel request hander

        hander
        aio or coio for one request and thread safe  (one request -> more demand -> parallel demand per coro -> one reply) 

step 1. no coroutine

<img width="659" height="128" alt="图片" src="https://github.com/user-attachments/assets/7385ae04-f719-44ed-8069-973e9615b424" />
<img width="659" height="128" alt="图片" src="https://github.com/user-attachments/assets/7b63c1d6-9d51-4c1c-9086-215d9fce056a" />

<img width="659" height="128" alt="图片" src="https://github.com/user-attachments/assets/5f063bff-7dc3-4d46-8f13-1b3e2ecf6283" />

nginx test

<img width="659" height="128" alt="图片" src="https://github.com/user-attachments/assets/883b487f-51f3-49c3-a728-243e7c1aa286" />

cinatra top 1 of 2022 world test

<img width="659" height="128" alt="图片" src="https://github.com/user-attachments/assets/97bb7fa2-3dc7-47f4-acd7-778ebb4046db" />

mrhttp top 1 of 2025 world test , mrhttp 是多进程、而且做了CPU指令优化，其实不能算微架构方面的。

<img width="659" height="128" alt="图片" src="https://github.com/user-attachments/assets/cb85ec65-a6f2-42b8-83ad-313f2a891478" />


step 2. coroutine api

        协程基本封装完成 The basic functionality of the coroutine is complete.
        参考 https://github.com/bugwang/coo fork from https://github.com/avplayer/ucoro 
请访问 [ucoro](https://github.com/avplayer/ucoro) 
<a href="https://github.com/bugwang/coo"> coo </a>

step 3. server + coroutine

        start ... 
