> [!WARNING]
> Just to remind myself, SSB includes(MIB(includes SIB1))

> [!IMPORTANT]
> I think many units involed in this part, I just want to remind myself and for quick reference
> RE: Resource elements
> REG: Resource Elements group, it equals to 1 RB(12 REs) *&* 1 OFDM symbol. So it is a 2 dimensional "mark".
> CCE: Control Channel Element, it contains 6 REGs.
> AL: Aggregation level, it contains the corresponding(1/2/4/8/16) CCEs.

> [!IMPORTANT]
> SIB1 will periodically transmitted whether UE wants or not.(True broacast in my opinion).

# MIB
what: Master information block
why: Transmitted by PBCH, need to camp on a cell, UE need to (at least) decode MIB and SIB1

_When I fist time encounter MIB, I start from the field of MIB, and I have no clues about it. But when I have a bigger picture, I think its design is straightforward and neat_

## The field of MIB 
MIB ::= SEQUENCE {

    systemFrameNumber                   BIT STRING (SIZE (6)),

    subCarrierSpacingCommon             ENUMERATED {scs15or60, scs30or120},

    ssb-SubcarrierOffset                INTEGER (0..15),

    dmrs-TypeA-Position                 ENUMERATED {pos2, pos3},

    pdcch-ConfigSIB1                   INTEGER (0..255),

    cellBarred                          ENUMERATED {barred, notBarred},

    intraFreqReselection                ENUMERATED {allowed, notAllowed},

    spare                               BIT STRING (SIZE (1))

}

systemFrameNumber: SFN

subCarrierSpacingCommon: It is the SCS of SIB1. There are many SCS in many scenes, it quit confused me (until now I edit this post :) ). but the [author](https://www.sharetechnote.com/html/5G/5G_Mib_Sib.html) summarize them as follow.\
![image](https://github.com/ZepherL1/5G/assets/157103546/3a89bfa2-c00e-44ae-885e-b33bd69f92f0) I try to illustrate by [image](https://www.sharetechnote.com/html/5G/5G_CommonSearchSpace_Type0_PDCCH.html) below:\
![image](https://github.com/ZepherL1/5G/assets/157103546/af6f3ad8-67ac-4bed-b141-0fae62a3cdc3)


ssb-SubcarrierOffset: k_ssb. Recall from [post](https://github.com/ZepherL1/5G/blob/main/SSB(PBCH).md). So basically, subCarrierSpacingCommon and ssb-SubcarrierOffset tells the location of SSB.

dmrs-TypeA-Position: Indicates Position of (first) DL DM-RS. Why is typeA? ofc there is typeB, the difference is that the DMRS location(time location) in PDSCH. 

*pdcchConfigSIB1*: this field tells the story of SIB1, [this](https://www.sharetechnote.com/html/5G/5G_CommonSearchSpace_Type0_PDCCH.html) tells the exact details(time domain & frequency domain) of PDCCH. 

cellBarred: Tell if the UE in THE cell

# SIB
There are 21 types of SIB defined in 3GPP. I will focus on the special one: *SIB1*
## SIB1
No matter what types of SIB, the details(real info) is carried by PDSCH. How can UE get and decode the corresponding SIB info? The DCI for SIB is carried by CORESET0 (I think it can be equal to PDCCH in SIB1 case). The time & freq location of CORESET0 is defined by [*pdcchConfigSIB1*](##the-field-of-mib).

### COREST0
CORESET refers to COntrol REsourceSET, which is a set of resources(time & freq), which used to carry SIB1 for PDSCH. The parameters can not be like other CORESET, so the paramters should be preset. The [author](https://www.sharetechnote.com/html/5G/5G_ResourceAllocationUnit.html) summarize them as follow :\
![image](https://github.com/ZepherL1/5G/assets/157103546/7001ab76-c1c1-44bc-8b41-56af5b638d09)

As previous described, the freq & time domain allocation is defined by MIB (inside PBCH).

### Search space
Another thing need to mention is that search space is whithin CORESET, where UE should monitor and detect PDCCH/DCI. In short, the useful(right) info is inside THE specific search space.

