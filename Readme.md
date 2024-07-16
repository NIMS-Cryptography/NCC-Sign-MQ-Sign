# NCC-Sign and MQ-Sign

This includes supporting documents of NCC-Sign and MQ-Sign and its implementation codes. They are submitted to 'Korean Post-Quantum Cryptography Competition' (www.kpqc.or.kr). Due to memory limitations, we upload KAT files of MQ-Sign at the security level 1.

 
### Past updates

<details> 

<summary> Learn more </summary>

#### Updates(v2.0)

NCC-Sign and MQ-Sign version update(v2.0) are released for KpqC competition Round 2.

Main updates from NCC-sign:

- NCC-Sign-Trinomial(NCC-Sign-T) version released.


Main updates from MQ-Sign:

- MQ-SignLR version released.


#### Updates(v1.0)


NCC-Sign and MQ-Sign version update(v1.0) are released.


The specifications of NCC-Sign has been modified as follows:

- We have added cost analysis on the Core-SVP model for all suggested parameter sets.

- We have added a new parameter set for the non-cyclotomic version and its reference implementation benchmarks.

- We have modified the parameter set for the cyclotomic trinomial case and have added a new parameter set for the use of NTT.

 
The specification of MQ-Sign has been modified as follows:

- We have removed SS and RS versions (recently cyptanalyzed by Trimoska et al. and Ikematsu et al.) of our four key generations from MQ-Sign leaving the two versions, MQ-Sign-RR and MQ-Sign-SR.

- We have added a binding technique so that a signature is identified with a unique public key and message to prevent potential attacks.

- We have updated the reference code and KAT files of MQ-Sign-SR.

</details>

