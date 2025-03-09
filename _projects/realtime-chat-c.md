---
layout: page
title: Realtime Chat
description: A real-time chat application written in C from scratch using socket and network programming.
importance: 1
# category: work
---

#### Overview
Realtime Chat is a simple yet powerful client-server chat application built from scratch in `C` using `socket programming`. The server listens for incoming client connections, while multiple clients can connect and exchange messages in real time. This project demonstrates low-level network programming, handling `TCP` connections, and implementing bi-directional communication between a server and multiple clients.

It was designed to be minimalistic, efficient, and provide a foundational understanding of networked applications in `C`. The application runs entirely on command-line interfaces, simulating real-time message exchange.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/realtime-chat.jpg" title="image of realtime chat application in action" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    On the left is the server listening on port `8000`, and on the right is the client connected to port `8000`
</div>

#### Technologies Used
- C
- Socket Programming

#### How to Use
Installation  

```bash
git clone https://github.com/usyntest/realtime-chat.git
cd realtime-chat
gcc server.c -o server
gcc client.c -o client
```

Running the server and client, run them both in different terminals:
```bash
./server 8000
```

```bash
./client 127.0.0.1 8000
```

#### Links

- 📂 [GitHub Repository](https://github.com/usyntest/realtime-chat)