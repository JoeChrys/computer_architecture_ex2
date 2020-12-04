# Computer Architecture

## Lab 2
22/11/2020\
Ilia Zarka 9289\
Iosif Chrysostomou 9130

---

### 1st Step
#### 1. System parameters

We run the benchmarks on this step with a **cache line size** of `64B`, a 2 way set associative **data cache** with a size of `64kB`, a 2 way set associative **instruction cache** with a size of `32kB` and an 8 way set associative **L2 cache** with a size of `2MB`.

#### 2. Simulation statistics

##### specbzip:
**simulated ms**: 83.847\
**cpi**: 1.676947\
**L1 dCache miss rate**: 0.014289\
**L1 iCache miss rate**: 0.000075\
**L2 cache miss rate**: 0.294749

##### spechmmer:
**simulated ms**: 59.410\
**cpi**: 1.188197\
**L1 dCache miss rate**: 0.001692\
**L1 iCache miss rate**: 0.000204\
**L2 cache miss rate**: 0.079948

##### speclibm:
**simulated ms**: 174.779\
**cpi**: 3.495573\
**L1 dCache miss rate**: 0.060971\
**L1 iCache miss rate**: 0.000098\
**L2 cache miss rate**: 0.999927

##### specmcf:
**simulated ms**: 55.471\
**cpi**: 1.109419\
**L1 dCache miss rate**: 0.002038\
**L1 iCache miss rate**: 0.000037\
**L2 cache miss rate**: 0.727788

##### specsjeng:
**simulated ms**: 513.819\
**cpi**: 10.276385\
**L1 dCache miss rate**: 0.121829\
**L1 iCache miss rate**: 0.000020\
**L2 cache miss rate**: 0.999979

#### 3. Different clock domains

In both cases, the system runs at `2GHz` (system.clk_domain). This clock is used to synchronize everything on the motherboard. The cpu_clk_domain clock refers to the cpu clock. That clock is by default, multiple of the system clock. So a second cpu, would run at a multiple of `1GHz`.

The simulated seconds do not scale with the clock frequency. This was also apparent on the first lab where we run our code with a wider variety of frequencies. The reason is that some stages of the execution of a command, do not depend only on the cpu frequency. A couple of those stages are reading and writing on the memory. The memory transfers rates are not tied to the cpu frequency, which means there can be delays which are independent from the rest of the system.

### 2nd Step
#### 1. Optimizing for Speclibm
The performance of the particular benchmarks seems to rely heavily on cache block size, which is demonstated by the following graphs.
#### 2.

### 3rd Step

For calculating the cost, we had a few key criteria in our minds.

* First, the cost of every memory level scales linearly with its size.
* Then, the higher level memories with the same characteristics (size, associativity etc) are cheaper to manufacture. In this case, we assumed that the L2 cache is 20% cheaper than the L1 cache.
* Increasing the associativity should also increase the cost, but not linearly. As we saw in the lectures, increasing the associativity, has diminishing returns. More specifically, more than an 8 way associative memory, shows very little improvements in performance. We made an educated guess and chose a logarithmic increase in the overall cost from the increase in assosiativity.
* Lastly, cash line size should also play a role in the final cost. We choose to multiply the above cost with the line size, because it affects both memory levels, and it increases the complexity of the hole cpu.

So we came up with the following formula:\

cost = (l1iSize * log(l1iAssociativity) + l1dSize * log(l1dAssociativity) + 0.8 * l2Size * log2(l2Associativity)) * log(CLSize)
