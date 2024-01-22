# SSB 
~~SSB and PBCH is quite confusing me before, there are many similarities of them, but down to the earth, there are totally 2 things:~~\
~~1. SSB consists of PSS (Primiary Synchronization Signal) and Secondary SSS (Secondary Synchronization Signal)as well as PBCH block, 3 of all, calls  SSB~~\
~~2. PBCH is a channel, in my opinion I think it is a resource block for info(such as SSB)~~\
## Allocation of SSB
### Frequency domain allocation
As described in my [Frequency](https://github.com/ZepherL1/5G/blob/main/Frequency.md), the two key parameters are  K_ssb and $N_{CRB}^{SSB}$(remember they are in different unit).\
![image](https://github.com/ZepherL1/5G/assets/157103546/8bdb6fe6-79cb-45e7-826c-5b7ea688a092)\
**Note**
1. SS/PBCH block consists of 240 contiguous subcarriers (20 RBs)
2. There are two ways(situation) to allocate the frequecy domain of SSB: NSA/ENDC and SA

#### NSA(TO BE STUDIED)
#### SA
The frequency location descibed in 38.104-5.4.3.2.x. (_note: the GSCN is corresponding to the central(120th RE) location of SSB_).\
I summarize the process:
1. Try to locate(transmit) the SSB on the raster.
2. With the desired location, we got the GSCN(as well as SS_REF), we can get the SSB start(RB0) location with reference to PointA.
3. Meanwhile, we can get $N_{CRB}^{SSB}$ and k_ssb.

### Time domain allocation
#### Time domain allocation in one slot
The time domain allocation of SSB is defined in 38.211 7.4.3.1-1.\
![image](https://github.com/ZepherL1/5G/assets/157103546/2ec71129-8cf6-4792-a38b-93695f76a56c)\
(_Note that the position of PBCH DM-RS varies with v and the value v changes depending on Physical Cell ID._)\
![image](https://github.com/ZepherL1/5G/assets/157103546/dca08c62-c79b-4727-b882-f28b768b6ac7)\
Above img is from [link](https://www.sharetechnote.com/html/5G/5G_FrameStructure.html#SS_PBCH_FrequencyDomainResourceAllocation)\
#### Time domain allocation in RF
In [post](https://www.sharetechnote.com/html/5G/5G_FrameStructure.html#SS_PBCH_FrequencyDomainResourceAllocation), the author summarize the different cases allocations. It's noted that in 38.213-4.1 cell search part, the SSB only exists in the first half part of each RF.
