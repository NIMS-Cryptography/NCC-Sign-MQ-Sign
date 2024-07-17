# NCC-Sign and MQ-Sign

This includes supporting documents of NCC-Sign and MQ-Sign and its implementation codes. They are submitted to 'Korean Post-Quantum Cryptography Competition' (www.kpqc.or.kr).

## How to use
Both NCC-Sign and MQ-Sign are compiled according to the rules described in the Makefile. To compile each source code, use the following command.

```
make
```

To clean up generated files, use the following comamnd.

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

## MQ-Sign (v2.1)

<details>
<summary> Learn more </summary>

Due to memory limitations, KAT response file of MQ-Sign only serves 1 test case. To verify that a KAT response with 100 test cases matches, check the cheksum values.


MQ-Sign KAT checksum

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

</details>



### Past updates(v2.0)

<details> 

<summary> Learn more </summary>

NCC-Sign and MQ-Sign version update(v2.0) are released for **KpqC competition Round 2**.

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