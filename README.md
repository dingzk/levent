# levent:
A event library just like libevent or libev but more lighter.

# example:

    // define callback
    void *on_read(int sock, short which, void *args) {}

    // main 
    include "levent/epoll.h"
    Epoll ep(1024);
    struct event_s ev[request_num];
    int i = 0;
    while(i < request_num) {
        // add event
        ep.set(ev + i, fd, EV_READ, on_read, (void *)this);
        ep.add(ev + i);
        i++;
    }
    // dispatch
    ep.dispatch(max_timeout);

# TODO:

- 对事件模型进行了抽象，目前抽象到epoll。已经定义了虚基类，其他模型进行继承即可，接下来会进一步进行抽象和扩展。
- 最终目标是打造一系列的网络编程生态。
