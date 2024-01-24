# Resource Allocation
_This part is specificed for the details of resource allocation. Majorly, this is for frequency allocation_

## Types of RA
There are 3 types of RA. Illustrated below
1. Type0 : allocation method is bitmap, which means that it could be non-continuous
2. Type1 : allocation method is set by start RB and number of RBs, so it is continuous.
3. Dynamic: which means that it is specified by a field in DCI.

> [!NOTE]
> If the DCI 1_0, UE should assume that allocation type is *1*.

### Type 0
Previous described, the bitmap is used in this type of allocation, so we need to map the RB(s) into RBG(G for group). The PDSCH and PUSCH only allocated in unit of RBG.
How to decide how many number of RBs in _One_ RBG? According to 38.214- 5.1.2 and 6.1.2, it depends on the bandwidth part size as well as _Configuration_. _Configuration_ is decided by rbg_size parameter in PDSCH. so in conclusion, the number of RBs in _ONE_ RBG depends on bandwidth part size and rbg_size.
> [!NOTE]
> Although the name rbg_size sounds like a size or number of somthing, but in PDSCH config, it is a numerate of {config1 or config2}

![image](https://github.com/ZepherL1/5G/assets/157103546/77b716d5-c114-4981-9625-dcebfce210f9)

Above img is a neat summary of RBG, which is from [link](https://www.sharetechnote.com/html/5G/5G_ResourceAllocationType.html#Allocation_Type_0)

### Type 1
This type is for continous configuration. This introduce first time the _RIV(resource indicator value)_. RIV includes start as well as number of RB just in *one single number*. 

How to represent two "number" in one single value? This could be found below

![image](https://github.com/ZepherL1/5G/assets/157103546/81adf67a-56d0-4bbb-acab-87919c7b6493)

This is also summarized by the author of link above.

### Dynamic
In a word, weather type0 or type 1 could be configure by DIC at each time of transmission.
