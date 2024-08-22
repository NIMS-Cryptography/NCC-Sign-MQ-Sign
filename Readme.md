# NCC-Sign and MQ-Sign

This includes supporting documents of NCC-Sign and MQ-Sign and its implementation codes. They are submitted to 'Korean Post-Quantum Cryptography Competition' (www.kpqc.or.kr).

## How to use
Both NCC-Sign and MQ-Sign are compiled according to the rules described in the Makefile. To compile each source code, use the following command.

```
make
```

To clean up generated files, use the following command.

```
clean
```

If you only want to compile for a specific security level, use one of the following commands. 

```
make PQCgenKAT_sign1
make PQCgenKAT_sign3
make PQCgenKAT_sign5
make test/test_speed1
make test/test_speed3
make test/test_speed5
```

## NCC-Sign (v2.1)

- Fixed SUPERCOP checksum issue in the AVX2 optimized version.
- Bug in the rejection process has been fixed.
- Applied some suggestions and patches from [Prof. D. J. Bernstein](https://groups.google.com/g/kpqc-bulletin/c/dcpwJ1bU5pQ/m/h-9dAUGpBgAJ).
- Improved the reference source code structure for better performance.
- Reimplemented some parts using AVX2 assembly.
- Released Cortex-M4 optimized version.

Due to the bug fix in t0, the KAT value has changed from before. For the revised KAT, see NCC-Sign/KAT(SHAKE) or NCC-Sign(AES).

### NCC-Sign Performances

- Measured on Intel® Core i7-1360P and each value is the median of 10,000 times measure and represents clock cycles.
- In case of Cortex-M4, NUCLEO-L4R5ZI used.

| Scheme                    | Algorithm | Lv.1    | Lv.3        | Lv.5      |
| :-----------------------: | :-------: | ------: | ----------: | --------: |
| (ref) NCC-Sign-T          | Keygen    | 127,415 | 162,315     | 259,499   |
| (ref) NCC-Sign-T          | Sign      | 250,128 | 421,926		| 704,288	|
| (ref) NCC-Sign-T          | Verify    | 128,538 | 155,346     | 252,686   |
| (AVX2) NCC-Sign-T         | KeyGen    | 54,902  | 67,432		| 109,402   |
| (AVX2) NCC-Sign-T         | Sign      | 89,207  | 165,766		| 261,423   |
| (AVX2) NCC-Sign-T         | Verify    | 65,626  | 79,388		| 128,612   |
| (Cortex-M4) NCC-Sign-T    | KeyGen    | 1,045k  | 1,359k      | 2,045k    |
| (Cortex-M4) NCC-Sign-T    | Sign      | 2,775k  | 4,256k      | 6,552k    |
| (Cortex-M4) NCC-Sign-T    | Verify    | 1,322k  | 1,669k      | 2,568k    |


## MQ-Sign (v2.1)

- Made Crypto API identical to the NIST PQC standard.
- Changes to Makefile rules allow for more concise compilation.
- By modifying the calculation process, performance is slightly improved.
- Removed some legacy parts of the public key, partially reducing the PK size.
- Applied some suggestions and patches from [Prof. D. J. Bernstein](https://groups.google.com/g/kpqc-bulletin/c/dcpwJ1bU5pQ/m/A98n7TuiAAAJ).


Due to the git upload limitations, KAT response file of MQ-Sign only serves 1 test case. <br>
To verify that a KAT response with 100 test cases matches, please check the cheksum values. <br>
Additionally, with changes to the API, the KAT require has become the same as the NIST PQC standard req. KAT has changed accordingly.

### MQ-Sign Performances

- Measured on Intel Xeon(R) Gold 6234 processor and each value is the median of 10,000 times (100 times for Keygen) measure and represents clock cycles.

| Scheme                | Algorithm | Lv.1          | Lv.3          | Lv.5          |
| :-------------------: | :-------: | ------------: | ------------: | ------------: |
| (ref) MQ-Sign_s-RR    | Keygen    | 121,645,666   | 434,302,517   | 978,413,002   |
| (ref) MQ-Sign_m-RR    | Keygen    | 120,615,145   | 430,588,245   | 969,699,032   |
| (ref) MQ-Sign_o-RR    | Keygen    | 117,670,429   | 416,383,251   | 941,885,381   |
| (ref) MQ-Sign_s-RR    | Sign      | 871,306       | 1,754,967     | 3,031,335     |
| (ref) MQ-Sign_s-RR    | Verify    | 760,114       | 1,357,774     | 2,196,068     |
| (ref) MQ-Sign-LR      | Keygen    | 89,401,545    | 312,936,150   | 701,261,588   |
| (ref) MQ-Sign-LR      | Sign      | 451,262       | 1,004,830     | 1,395,664     |
| (ref) MQ-Sign-LR      | Verify    | 774,652       | 1,414,666     | 2,202,376     |
| (AVX2) MQ-Sign_s-RR   | Keygen    | 8,574,372     | 34,464,908    | 99,201,093    |
| (AVX2) MQ-Sign_m-RR   | Keygen    | 7,595,005     | 31,538,016    | 90,031,140    |
| (AVX2) MQ-Sign_o-RR   | Keygen    | 5,718,159     | 25,427,415    | 75,055,554    |
| (AVX2) MQ-Sign_s-RR   | Sign      | 89,716        | 267,562       | 537,135       |
| (AVX2) MQ-Sign_s-RR   | Verify    | 50,868        | 175,518       | 356,881       |
| (AVX2) MQ-Sign-LR     | Keygen    | 5,451,597     | 25,605,484    | 67,485,424    |
| (AVX2) MQ-Sign-LR     | Sign      | 65,300        | 168,684       | 360,636       |
| (AVX2) MQ-Sign-LR     | Verify    | 51,744        | 191,986       | 381,019       |

### MQ-Sign KAT checksum

- The checksum may differ depending on the newline (LF, CRLF, CR), and the provided checksum is based on LF.

| Type                      | sha256sum                                                        |
| ------------------------: | :--------------------------------------------------------------- |
| KAT require               | 81ff60e3ef698751e5572f0bb7f831f069605229c220ee1cf27a92572d6ebc7e |
| MQRR-s-256\_72\_46        | 05e586440083ac8f1166e701abd99fc60bf903fe11178737c17119a8969aa3e9 |
| MQRR-s-256\_112\_72       | f3183b373a1fc7a3437acda1b18d2b013dd041c526ff35cd43eef8c42b70fade |
| MQRR-s-256\_148\_96       | 7683aabfaf6132ac40388bab6bb35f3506f815ec8ddd662ad5a7e71f8f93815f |
| MQRR-m-256\_72\_46        | 7fcee3651ba5ac9bd4b8e48cf81c82865e16efdf772199dd3f7cc19b08f5cbca |
| MQRR-m-256\_112\_72       | 2696c1486bc17995fbf64d7c37ebcebf37e8c040f8e8bfe022858dfb84cfbe9a |
| MQRR-m-256\_148\_96       | 411472fd49405c2af5e6069527f5d1b854a56926e6998e9984fcf84028e36748 |
| MQRR-o-256\_72\_46        | c2a68f069a8943beab52c8df72b704f601d66c0ec9d089b0fbdc84621024973d |
| MQRR-o-256\_112\_72       | 5e2043975de0e20f5fd4939d0c99d912bca6ca4d69b2561587b6d2e067ecda32 |
| MQRR-o-256\_148\_96       | 281ef17073d429e85c453a96d60308fb5242ce6b6d23988196fe226ae58f63e4 |
| MQLR-256\_72\_46          | 91b3f015358fe86320daf6db29e90907a56d0a2b441ef2902f043cd129abc366 |
| MQLR-256\_112\_72         | 8fdd18905959063a9765cb8776320f13f6391e37b88f8f8e6e5a135ea6bdcf03 |
| MQLR-256\_148\_96         | 50868df7c4656bcadcc5de5f41672750da6d0e50cf69bcbb2f3c86c40bd38b82 |



### Past updates(v2.0)

<details> 

<summary> Learn more </summary>

NCC-Sign and MQ-Sign version update(v2.0) are released for **KpqC competition Round 2**. <br>
Performaces are mesured on Intel Xeon(R) Gold 6234 processor.

#### NCC-Sign (v2.0)

- NCC-Sign-Trinomial(NCC-Sign-T) version released.
- Performance measurement results of NCC-Sign-T.

| Scheme                    | Algorithm | Lv.1    | Lv.3        | Lv.5      |
| :-----------------------: | :-------: | ------: | ----------: | --------: |
| (ref) NCC-Sign-T          | Keygen    | 240,496 | 324,140     | 488,168   |
| (ref) NCC-Sign-T          | Sign      | 616,746 | 1,245,144   | 1,781,784 |
| (ref) NCC-Sign-T          | Verify    | 339,698 | 460,808     | 722,320   |
| (AVX2) NCC-Sign-T         | KeyGen    | 164,184 | 218,772     | 335,440   |
| (AVX2) NCC-Sign-T         | Sign      | 290,396 | 553,728     | 838,432   |
| (AVX2) NCC-Sign-T         | Verify    | 158,138 | 200,242     | 340,382   |


#### MQ-Sign (v2.0)

- MQ-Sign-LR version released.
- Performance measurement results of MQ-Sign-RR.

| Scheme                | Algorithm | Lv.1          | Lv.3          | Lv.5          |
| :-------------------: | :-------: | ------------: | ------------: | ------------: |
| (ref) MQ-Sign_s-RR    | Keygen    | 122,046,651   | 438,023,770   | 994,466,810   |
| (ref) MQ-Sign_s-RR    | Sign      | 861,724       | 1,752,258     | 3,053,560     |
| (ref) MQ-Sign_s-RR    | Verify    | 755,522       | 1,339,244     | 2,218,340     |
| (ref) MQ-Sign-LR      | Keygen    | 89,401,545    | 312,936,150   | 701,261,588   |
| (ref) MQ-Sign-LR      | Sign      | 451,262       | 1,004,830     | 2,026,304     |
| (ref) MQ-Sign-LR      | Verify    | 774,652       | 1,414,666     | 2,202,376     |
| (AVX2) MQ-Sign_s-RR   | Keygen    | 9,454,708     | 40,250,626    | 102,775,550   |
| (AVX2) MQ-Sign_m-RR   | Keygen    | 8,291,246     | 36,168,836    | 91,291,653    |
| (AVX2) MQ-Sign_o-RR   | Keygen    | 6,633,743     | 30,024,722    | 77,684,841    |
| (AVX2) MQ-Sign_s-RR   | Sign      | 90,480        | 268,866       | 524,030       |
| (AVX2) MQ-Sign_s-RR   | Verify    | 50,460        | 185,086       | 363,611       |
| (AVX2) MQ-Sign-LR     | Keygen    | 5,451,597     | 25,605,484    | 67,485,424    |
| (AVX2) MQ-Sign-LR     | Sign      | 65,300        | 168,684       | 360,636       |
| (AVX2) MQ-Sign-LR     | Verify    | 51,744        | 191,986       | 381,019       |



</details>


### Past updates(v1.0)

<details>

<summary> Learn more </summary>

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
