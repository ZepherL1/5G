# Frenquency
## Channel raster
### ARFCN
The fundimental of frequency is kHZ. The different of ARFCN and GSCN lies in the different _presentation_ of frequency(in kHZ).\
The mapping of frequency(F<sub>REF</sub>) and ARFCN number(N<sub>REF</sub>) is F<sub>REF</sub> = F<sub>REF-Offs</sub> + ΔF<sub>Global</sub>(N<sub>REF</sub>-N<sub>REF-Offs</sub>).with the ARFCN number(N<sub>REF</sub>), the channel raster is deifned by 
![image](https://github.com/ZepherL1/5G/assets/157103546/b2243b88-28cd-4cfa-beff-aa8f5a00d0e7)
### GSCN
The mapping of frequency and GSCN is in a different way(just in different mapping way).\
![image](https://github.com/ZepherL1/5G/assets/157103546/b607cfd6-5ebf-42a2-8e06-972e1eafaf83)
By the selection of N and M, we will get different GSCN. with the GSCN, we can find out the operating band.\
(_note: if the operating band is fixed(in other words, ARFCN fall in the range of **THE** operating band, GSCN must selected from corresponding range value_)
![image](https://github.com/ZepherL1/5G/assets/157103546/c5572c36-cf1d-4645-b6d7-f33627b88711)
### Why GSCN and ARFCN
The main idea is to faster cell search. Cause the granuity of GSCN is bigger(rougher) than ARFCN.

## Frequency domain location
### Reference subcarrier spacing(sub 6g and mmWave)
![image](https://github.com/ZepherL1/5G/assets/157103546/d55542a6-8c52-4354-adf1-9a7924fff76d)
The difference lies in the subcarrier spacing(SCS). In sub6G, the SCS is 15kHZ while mmWave is 60kHZ(Just the granuity of band).PRB0 presents the reference point (**PointA** if I make no mistakes)\
#### Why we need point A?
In 5G, there is a new concept, **Bandwidth part(BWP)**, which means there are many BWP in one band, for different purposes. In order to seperate and flexible arrange these BWPs, there are 2 ways: \
1. the parameter _offsetToPointA_ defines the the lowest subcarrier spacing resource block(RB) offsets to the Point A. This RB is used for UE to cell search.
2. Parameter _absoluteFrequencyPointA_ for all other cases where _absoluteFrequencyPointA_ represents the frequency-location of point A expressed as in ARFCN.\
In SSB, the following pic shows the two parameters: K_ssb and $N_{CRB}^{SSB}$, to decide the position of SSB in band.
![image](https://github.com/ZepherL1/5G/assets/157103546/8bdb6fe6-79cb-45e7-826c-5b7ea688a092)
