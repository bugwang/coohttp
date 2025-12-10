# cohttp
idea：
http server api ，http client api:
use epoll 
use pool
use coroutine
and Don't depend on third party or only header file
but i need time

desc：

        server
        one loop per pthread  - > co_pool per loop -> ( one request one co)  for  parallel hander

        hander
        a or s io for (one request -> more demand -> parallel demand per co -> one reply)

step 1. no coroutine

<img width="578" height="157" alt="图片" src="https://github.com/user-attachments/assets/13e9158e-db3a-455b-a82a-2ef2b73a452c" />

<img width="550" height="127" alt="图片" src="https://github.com/user-attachments/assets/14106073-d526-494d-822d-7763b007c69f" />
