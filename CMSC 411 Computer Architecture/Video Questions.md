# QUESTION 1

1.  Record a short 5 minute video answering the four questions below.
    
    Video Specifications:
    
    -Your video should only be 5 minutes long or less.
    
    -You can work out the specifics before you record the video and just explain what you did in the video
    
    **-You should introduce yourself in the video and your face should be visible at the beginning.**
    
Hello professor, my name is John Hair and I am a computer engineering student with a minor in Chinese here at UMBC. 

### QUESTION 2

1.  Why bother improving the bus architecture of a processor?

A bus is a shared communication link which uses one set of wires to connect multiple subsystems. They allow for versatility when adding new devices or moving current ones and allow for low cost since its just a single set of wires. However, this requires a dependence on these buses to quickly carry signals around the processor in order to perform processes. Without improvements to the bus architecture, the processor would not be able to interact with other parts of the system, slowing it down. However, using methods like multiplexing the address and data line can help to speed up transactions, or increasing the data bus width, which would redce the amount of bus cycles for transfers of multiple words, which increases bandwidth. 

### QUESTION 3

1.   Priotizing reads over writes in cache is considered an optimization, why is this so? What does optimizing reads over writes get you?

The main indication of cache performance is using the equation for average memory access time, or AMAT, which is hit time plus the miss rate times the miss penalty time. In order to improve the miss penalty time of this equation, we can use multilevel caches and prioritize reads over writes. Reducing the miss penalty time of cache access would lead to a smaller AMAT value, meaning a more optimal access time.

### QUESTION 4

1.  Why did computer designes move to a multiprocessor system instead of focusing on improving the processors themselves?

There are multiple reasons designers started to move to a multiprocessor system instead of focusing on improving individual processors. One reason is that no processor will ever be perfect. A huge optimizer for processors was the use of instruction level parallelism, which meant pipelining and speculative execution of instructions. However, you will never have an ideal processor, because branch prediction and perfect memory liasing does not exist. The solution to this is to include multiple processors to act like cores to one main processor for the system, following the multiple instruction streams, multiple data streams, or MIMD, model. This also includes advantages of increased throughput and reliability, since you have more processors that can do more work in a unit of time and have multiple cores that act as failsafes.

### QUESTION 5

1.  What is the difference between pipelining and scoreboarding?

A big difference between pipelining and scoreboarding is that pipelining is static scheduling, meaning that each instruction must be completed before the next instruction completes, meaning that stalls must be put in place to avoid hazards. Scoreboarding, however is dynamically scheduled, meaning that the execution stage is performed out of order. Although the execution is out of order, issuing is still performed in order. Another difference is their stages: Pipelining for MIPS has five stages: instruction fetch, instruction decode, execution, memory access, and write back while scoreboarding has four: issue, read operands, execution, and write result. 