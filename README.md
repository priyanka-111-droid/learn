# Codespaces , Linux Distros

## 1. Codespaces on Github
- Gives access to VSCode editor and underlying virtual machine
## 2. Shell scripts
- .sh scripts
- Run by : 
    ```
    chmod +x hello.sh 
    ./hello.sh
    ``` 
- where chmod changes access permission to make file executable and ./hello.sh helps us to run the executable binary
- Can also do `bash hello.sh`.

### i) Multiline scripts
- To execute multiline scripts, use EOF command.
- EOF command used in here document 
- Here documents helps us to directly pass multiple lines of text directly into command.
- EOF MUST be used at start and end of string.
- EOF can be any unique string, not necessarily EOF.
- See eof.sh.

## Linux

- Virtual Machines for Codespaces run on Images.
- Images are created using [Github Runner Image](https://github.com/actions/runner-images)
- We will use an Ubuntu image.


Doubts:
- Do we need !bin/sh?? - for executing file using sh(bash shell)


# Server and Virtualization Overview

## Hardware Overview
### Dell PowerEdge AI Servers
- **Servers**: Dell PowerEdge AI servers.
- **Network**: Radiowaves used for encoding and decoding (e.g., from tower to phone).
- **Ports**: Ethernet (LAN) cable.

## Connecting to Host
- **SSH**: To connect to a host machine running CentOS:
  ```
  ssh root@<hostname_or_ip>
  ```

## Installing Virtualization Tools
- On CentOS, install **Virtual Machine Manager** (VMM).
  - **VMM** uses **QEMU** library to help the host interact with virtual machines (VMs).
  - **Create a New VM** using VMM.

## CPU Information
- **Command**: `lscpu`
- **CPU Details**: Shows Intel Xeon CPU details.

### CPU Architecture:
  - **Socket**: Refers to a physical socket on the motherboard.
  - Each CPU has **1 socket**, and the system can have up to **2 CPUs**.
  - Each core can run **2 threads** simultaneously.
  - **26 cores per socket** - these are the actual processing units.
  - Each core can perform multiple operations at once.
  - 2 CPUs × 26 cores = 52 logical processors

### What is a Core?
- **Core**: A compute unit inside the physical processor (CPU) that can independently process instructions.
  - Each core has its own **ALU** (Arithmetic Logic Unit) and **registers**.
  - Essentially, a mini-processor inside the CPU.
  - **Multicore** means multiple cores on a single chip.

---

## NUMA (Non-Uniform Memory Access) Nodes
- In a **multi-socket system** like Dell, you may see different NUMA node configurations:
  - **NUMA Node 0**: CPU with even-numbered cores.
  - **NUMA Node 1**: CPU with odd-numbered cores.
- This setup is due to the system having **2 separate CPUs** (sockets), with each CPU having **26 cores**.
  - Each CPU has 26 cores, and each core can handle **2 threads** simultaneously, resulting in **52 processors** in total (26 × 2 = 52).

---

## Virtualization Cache Overview
### Cache Levels:
- **L1d Cache**: Data cache (small, stores frequently accessed data).
- **L1i Cache**: Instruction cache (small, stores frequently accessed instructions).
- **L2 Cache**: Shared between data and instructions, acts as a backup for L1.
- **L3 Cache**: Shared across multiple cores within a CPU, the largest cache.

### Cache Distribution:
- **L1d and L1i**: Each core has its own dedicated L1 cache (data and instruction).
- **L2 Cache**: Can be shared between cores in a CPU or may be separate.
- **L3 Cache**: Shared across all cores in a CPU socket.

---

## Byte Order: Little Endian
- **Byte Order**: **Little Endian** is used.
  - Little Endian means that the **Least Significant Byte (LSB)** is stored first at the lowest memory address.
  - This is important for systems that store **multibyte data** (e.g., integers) in memory.
  
- **Big Endian**: Some systems (e.g., network protocols) may use Big Endian.
  - **Consistency**: Protocols like **TCP/IP** often define the byte order to ensure consistency across different systems.
  - **Little Endian** is most common on modern systems (especially on x86 architecture).

- **Note**: When working with binary files, it's essential to ensure the correct byte order is used.

---

## CPU Flags and Their Importance
### CPU Flags:
- **HW Virtualization**: Important for running virtual machines (e.g., VMware, Docker).
  - **Intel VT-x** (or equivalent) should be enabled for hardware-assisted virtualization.
  
- **SSE (Streaming SIMD Extensions)**: These flags indicate that the CPU supports performing **multiple operations simultaneously** (SIMD).
  
- **Randomness (RDSEED)**: Required for hardware random number generation, essential in certain network functions like **packetcore** in **4G/5G** networks.

---

## Network Functionality (Packetcore)
- **Packetcore**: The backend for **4G/5G** networks.
  - **User Plane Functions** (UPF) are critical components.
  - **Hardware Flags**: Some functions, such as **randomness** generation (e.g., using `RDSEED`), are necessary for specific network tasks like **data encryption** and **random number generation**.