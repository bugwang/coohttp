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
<img width="574" height="281" alt="图片" src="https://github.com/user-attachments/assets/fcc6a86d-771c-42a7-bc46-a7e69d985d98" />
