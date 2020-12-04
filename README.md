# computer_architecture_ex2

### 1st Step
#### 1.

##### specbzip:
**cache line size** 64B\
**dcache**: 64kB, 2 way set associative\
**icache**: 32kB, 2 way set associative\

##### spechmmer:
**cache line size** 64B\
**dcache**: 64kB, 2 way set associative\
**icache**: 32kB, 2 way set associative\

##### speclibm:
**cache line size** 64B\
**dcache**: 64kB, 2 way set associative\
**icache**: 32kB, 2 way set associative\

##### specmcf:
**cache line size** 64B\
**dcache**: 64kB, 2 way set associative\
**icache**: 32kB, 2 way set associative\

##### specsjeng:
**cache line size** 64B\
**dcache**: 64kB, 2 way set associative\
**icache**: 32kB, 2 way set associative\

#### 2.

##### specbzip:
**simulated ms**: 83.847\
**cpi**: 1.676947\
**L1 dCache miss rate**: 0.014289\
**L1 iCache miss rate**: 0.000075\
**L2 cache miss rate**: 0.294749\

##### spechmmer:
**simulated ms**: 59.410\
**cpi**: 1.188197\
**L1 dCache miss rate**: 0.001692\
**L1 iCache miss rate**: 0.000204\
**L2 cache miss rate**: 0.079948\

##### speclibm:
**simulated ms**: 174.779\
**cpi**: 3.495573\
**L1 dCache miss rate**: 0.060971\
**L1 iCache miss rate**: 0.000098\
**L2 cache miss rate**: 0.999927\

##### specmcf:
**simulated ms**: 55.471\
**cpi**: 1.109419\
**L1 dCache miss rate**: 0.002038\
**L1 iCache miss rate**: 0.000037\
**L2 cache miss rate**: 0.727788\

##### specsjeng:
**simulated ms**: 513.819\
**cpi**: 10.276385\
**L1 dCache miss rate**: 0.121829\
**L1 iCache miss rate**: 0.000020\
**L2 cache miss rate**: 0.999979\

#### 3.

The simulated seconds do not scale with the clock frequency. This was also apparent on the first lab where we run our code with a wider variety of frequencies. The reason is that some stages of the execution of a command, do not depend only on the cpu frequency. A couple of those stages are reading and writing on the memory. The memory transfers rates are not tied to the cpu frequency, which means there can be delays which are independent from the rest of the system.

### 2nd Step
#### 1.

#### 2.

### 3rd Step
