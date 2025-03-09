---
layout: page
title: Little Computer
description: An implementation of the LC-3 VM, a 16-bit educational computer architecture from scratch in C.
importance: 1
# category: work
---

#### Overview

The LC3 VM is a fully functional virtual machine implementing the LC-3 (Little Computer 3) architecture, a 16-bit educational computer. Written from scratch in C, this project simulates the LC-3 instruction set, allowing it to execute compiled LC-3 assembly programs.

This implementation follows the fetch-decode-execute cycle and includes:

- `Memory management` to store instructions and data.
- `Instruction decoding & execution` for all LC-3 opcodes.
- `Trap routines` for basic I/O operations (e.g., reading/writing characters).

The project was built for low-level programming enthusiasts and provides a great opportunity to understand how virtual machines and CPU instruction sets work at the hardware level.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/lc3-vm-1.jpg" title="search screen for mojster" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/lc3-vm-2.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    On the left is the server listening on port <code>8000</code>, and on the right is the client connected to port <code>8000</code>
</div>

#### Technologies Used
- C
- Socket Programming

#### How to Use
Installation  

```bash
git clone git@github.com:usyntest/lc3-vm.git
cd lc3-vm
mkdir build && cd build
cmake ..
make
```

Running images on the VM, you can download any `LC3` image and run it:
```bash
./lc3 ../images/2048.lc3
```

#### Links

- 📂 [GitHub Repository](https://github.com/usyntest/realtime-chat)