# Tugas 2 Sistem Operasi
## Practice Exercise

**Nama**: Ahnaf Hafizh Putra Efendi  
**NRP**: 3124500033  
**Dosen Pengajar**: Dr Ferry Astika Saputra ST, M.Sc  
**PROGRAM STUDI**: D3 TEKNIK INFORMATIKA  
**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA (PENS)**  
**TAHUN**: 2024

---

### 1.1 What are the three main purposes of an operating system?
1. **Resource Management**: The operating system manages hardware resources such as CPU, memory, and I/O devices, ensuring efficient allocation and utilization.
2. **Abstraction and Simplification**: It provides a simplified interface for users and applications to interact with the hardware, hiding the complexities of the underlying system.
3. **Security and Protection**: The operating system ensures that different processes and users do not interfere with each other, providing a secure environment.

### 1.2 When is it appropriate for the operating system to forsake efficiency and "waste" resources? Why is such a system not really wasteful?
An operating system (OS) may choose to forsake efficiency and "waste" resources in certain situations to prioritize other factors like fairness, robustness, or user experience. Here are some key scenarios where this might happen:

1. **Fairness**: When managing multiple processes or users, an OS might allocate resources equally or in a non-optimal way to ensure that every user or process gets a fair share of resources, even if this leads to some inefficiency. For example, a system might limit the CPU usage of a single process to prevent it from monopolizing resources, ensuring that other processes also get their fair share, which might reduce overall efficiency but improve the system's fairness.
   
2. **Robustness and Stability**: An OS may allocate more memory or CPU resources than strictly necessary to maintain system stability, especially in the case of real-time or critical systems where failure could have significant consequences. For example, when managing system tasks, an OS might over-allocate resources to guarantee that essential services or background processes always have enough resources to avoid crashing.

3. **User Experience**: Sometimes, efficiency is sacrificed to improve the user experience. For instance, the system might use more resources to provide a smoother, more responsive interface (such as keeping background applications running or maintaining a persistent cache) to avoid delays and ensure the system feels faster, even if it’s technically less efficient.

4. **Caching and Preloading**: An OS may keep more data in memory (caching) than strictly necessary to speed up future access, even though this may seem like a waste of memory. However, this often results in a much faster experience for users, especially in situations where response time is crucial.

#### Why it’s not really wasteful:
1. **Optimizing for User or System Goals**: The "wasted" resources are often allocated for a greater purpose, like ensuring fairness or reliability, which contribute to the overall effectiveness of the system in real-world use. The trade-off is often considered worthwhile because it improves the long-term functionality or user experience.
   
2. **Hidden Benefits**: The perceived "waste" might not be wasteful in the traditional sense. For example, keeping resources idle for a brief period can allow the system to quickly handle spikes in demand, avoid latency issues, or recover from unexpected workloads, which in the end benefits both users and system performance.
   
3. **Preventing Failures**: In many cases, a small "waste" of resources can prevent more significant issues, like system crashes or slowdowns. It's a trade-off for ensuring that the system stays stable, which ultimately improves efficiency in the long term by reducing downtime or the need for troubleshooting.

### 1.3 What is the main difficulty that a programmer must overcome in writing an operating system for a real-time environment?
The main difficulty is ensuring predictable and deterministic response times. Real-time systems require tasks to be completed within strict deadlines, and the operating system must prioritize tasks accordingly. This involves:
- Efficient scheduling algorithms.
- Minimizing latency and jitter.
- Handling interrupts and I/O operations without causing delays.

### 1.4 Should the operating system include applications such as web browsers and mail programs? Argue both sides.
**Yes, it should include them:**
- **Convenience**: Pre-installed applications provide a ready-to-use system for users.
- **Integration**: Applications can be tightly integrated with the OS for better performance and security.
- **Consistency**: Ensures a uniform user experience across devices.

**No, it should not include them:**
- **Bloatware**: Including unnecessary applications can bloat the OS, consuming resources.
- **Flexibility**: Users may prefer alternative applications, and pre-installed apps limit choice.
- **Security Risks**: More applications increase the attack surface for potential vulnerabilities.

### 1.5 How does the distinction between kernel mode and user mode function as a rudimentary form of protection (security)?
- **Kernel Mode**: The OS runs in kernel mode, allowing direct access to hardware and critical system resources.
- **User Mode**: Applications run in user mode, with restricted access to hardware and sensitive areas of the system.

This separation prevents user applications from interfering with the OS or other applications, ensuring system stability and security.

### 1.6 Which of the following instructions should be privileged?
In an operating system, privileged instructions are those that require a higher level of control and can only be executed by the operating system or kernel in a protected mode (i.e., with higher privileges). These instructions generally involve managing hardware resources or controlling system behavior in a way that, if misused, could lead to system instability, security vulnerabilities, or crashes.

#### Privileged Instructions:
- **I/O Operations**: Instructions that interact with hardware devices, such as reading from or writing to disk, interacting with peripherals, or modifying memory-mapped device registers.
- **Changing the Mode of the CPU** (e.g., switching from user mode to kernel mode).
- **Memory Management Instructions** (e.g., setting page tables).
- **Timer Management** (e.g., setting the system clock or interrupt timer).
- **Disabling Interrupts**: Instructions that disable or mask interrupts.
- **Managing System Calls**: Instructions related to invoking system calls or switching context between user and kernel modes.

#### Non-privileged Instructions (user-level instructions):
- Arithmetic operations (e.g., addition, subtraction)
- Logical operations (e.g., AND, OR)
- Basic control flow instructions (e.g., jump, branch)

### 1.7 Describe two difficulties that could arise from placing the OS in a memory partition that cannot be modified.
1. **Limited Flexibility**: The OS cannot dynamically adjust its memory usage, making it difficult to handle varying workloads or new features.
2. **Performance Bottlenecks**: If the OS cannot modify its own memory, it may struggle to optimize performance or respond to system events efficiently.

### 1.8 What are two possible uses of multiple modes of operation in CPUs?
1. **Enhanced Security**: Additional modes can provide finer-grained access control, isolating critical processes from less trusted ones.
2. **Specialized Operations**: Modes can be designed for specific tasks, such as virtualization or real-time processing, improving efficiency.

### 1.9 How could timers be used to compute the current time?
Timers can be used to track elapsed time by counting clock ticks. For example:
- A system timer increments at a fixed frequency (e.g., 1,000 ticks per second).
- The OS records the number of ticks since a known start time (e.g., system boot).
- By multiplying the tick count by the interval between ticks, the OS can calculate the current time.

### 1.10 Give two reasons why caches are useful. What problems do they solve? What problems do they cause?
#### Reasons caches are useful:
1. **Speed**: Caches provide faster access to frequently used data, reducing latency.
2. **Efficiency**: They reduce the load on slower storage devices (e.g., disks) by serving data from faster memory.

#### Problems they solve:
- Slow access times for data stored in main memory or secondary storage.
- High latency in fetching data from remote or slow devices.

#### Problems they cause:
- **Cache Coherence**: Ensuring consistency between cache and main memory.
- **Cache Pollution**: Storing unnecessary data, reducing effective cache size.

#### Why not make caches as large as the device they cache?
- **Cost**: Larger caches are more expensive.
- **Diminishing Returns**: Beyond a certain size, the performance gains do not justify the cost.
