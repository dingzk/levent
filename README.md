# levent
A Light events just like libevent or libev

# useage:

    include "levent/epoll.h"

    Epoll ep(1024);
    uint64_t request_id;
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
