# turris-honeypod-statistics
Statistical work based on data from turris honeypods

We are trying to proof, that most common user name used in attacks is independent of country, from witch the attack came from.

In this project I use 3 libraries: pandas, researchpy and scipy.stats

**Warning:**
The newest pandas does not work properly. I used version 1.5.3

Let's make our assumptions:

- H_0: Variables are independent
- H_A Variables are dependent

We will use chi square independence test.

Firstly let's find the most common name:
```
anonymous
```

Now we will create a bitmap for each entry if the most common name was used. Let's see how many times was or was not used for each country. (True = was used, Fakse = was not used)

```
                      most_common_user_name              
most_common_user_name                 False  True     All
country                                                  
AR                                       73     0      73
AT                                        3     5       8
AU                                       12     2      14
BD                                        5     0       5
BE                                       10  1068    1078
BO                                       25     0      25
BR                                     1574   107    1681
BY                                     1535   513    2048
CA                                        0    30      30
CH                                      111     0     111
CK                                        1     0       1
CN                                    45408  3469   48877
CU                                        1     0       1
CZ                                       85     0      85
DE                                     1160   117    1277
EE                                        0     1       1
ES                                      960    62    1022
FR                                      246    36     282
GB                                     1708   174    1882
GH                                      854    62     916
HK                                     1830   171    2001
HU                                        1     1       2
ID                                      969    61    1030
IN                                     3129   193    3322
IQ                                        3     0       3
IR                                        3     1       4
IT                                       40     1      41
JP                                       33     0      33
KE                                       40     0      40
KG                                       36     4      40
KR                                     5620   436    6056
KZ                                        5     1       6
ME                                        4     0       4
MN                                        1     0       1
MX                                     1728   124    1852
NG                                     1597   117    1714
NL                                      884    98     982
NO                                        0     1       1
PH                                       17     0      17
PK                                      897    63     960
PL                                        0     3       3
PT                                       28     0      28
RO                                        1     2       3
RU                                     5731   915    6646
SC                                        0     1       1
SE                                        0     3       3
SG                                       56    16      72
SK                                        0     2       2
SY                                        1     0       1
TH                                     1749   124    1873
TJ                                        5     1       6
TR                                      880    62     942
TW                                     5369   373    5742
UA                                        2     4       6
US                                     1380   231    1611
UZ                                       20     3      23
VN                                     5111   371    5482
ZA                                       30     0      30
All                                   90971  9029  100000
```

Now let's use scipy.stats and see what chi2 test will give us:

```
Chi2ContingencyResult(statistic=12532.20948102368, pvalue=0.0, dof=116, expected_freq=array([[6.64088300e+01, 6.59117000e+00, 7.30000000e+01],
       [7.27768000e+00, 7.22320000e-01, 8.00000000e+00],
       [1.27359400e+01, 1.26406000e+00, 1.40000000e+01],
       [4.54855000e+00, 4.51450000e-01, 5.00000000e+00],
       [9.80667380e+02, 9.73326200e+01, 1.07800000e+03],
       [2.27427500e+01, 2.25725000e+00, 2.50000000e+01],
       [1.52922251e+03, 1.51777490e+02, 1.68100000e+03],
       [1.86308608e+03, 1.84913920e+02, 2.04800000e+03],
       [2.72913000e+01, 2.70870000e+00, 3.00000000e+01],
       [1.00977810e+02, 1.00221900e+01, 1.11000000e+02],
       [9.09710000e-01, 9.02900000e-02, 1.00000000e+00],
       [4.44638957e+04, 4.41310433e+03, 4.88770000e+04],
       [9.09710000e-01, 9.02900000e-02, 1.00000000e+00],
       [7.73253500e+01, 7.67465000e+00, 8.50000000e+01],
       [1.16169967e+03, 1.15300330e+02, 1.27700000e+03],
       [9.09710000e-01, 9.02900000e-02, 1.00000000e+00],
       [9.29723620e+02, 9.22763800e+01, 1.02200000e+03],
       [2.56538220e+02, 2.54617800e+01, 2.82000000e+02],
       [1.71207422e+03, 1.69925780e+02, 1.88200000e+03],
       [8.33294360e+02, 8.27056400e+01, 9.16000000e+02],
       [1.82032971e+03, 1.80670290e+02, 2.00100000e+03],
       [1.81942000e+00, 1.80580000e-01, 2.00000000e+00],
       [9.37001300e+02, 9.29987000e+01, 1.03000000e+03],
       [3.02205662e+03, 2.99943380e+02, 3.32200000e+03],
       [2.72913000e+00, 2.70870000e-01, 3.00000000e+00],
       [3.63884000e+00, 3.61160000e-01, 4.00000000e+00],
       [3.72981100e+01, 3.70189000e+00, 4.10000000e+01],
       [3.00204300e+01, 2.97957000e+00, 3.30000000e+01],
       [3.63884000e+01, 3.61160000e+00, 4.00000000e+01],
       [3.63884000e+01, 3.61160000e+00, 4.00000000e+01],
       [5.50920376e+03, 5.46796240e+02, 6.05600000e+03],
       [5.45826000e+00, 5.41740000e-01, 6.00000000e+00],
       [3.63884000e+00, 3.61160000e-01, 4.00000000e+00],
       [9.09710000e-01, 9.02900000e-02, 1.00000000e+00],
       [1.68478292e+03, 1.67217080e+02, 1.85200000e+03],
       [1.55924294e+03, 1.54757060e+02, 1.71400000e+03],
       [8.93335220e+02, 8.86647800e+01, 9.82000000e+02],
       [9.09710000e-01, 9.02900000e-02, 1.00000000e+00],
       [1.54650700e+01, 1.53493000e+00, 1.70000000e+01],
       [8.73321600e+02, 8.66784000e+01, 9.60000000e+02],
       [2.72913000e+00, 2.70870000e-01, 3.00000000e+00],
       [2.54718800e+01, 2.52812000e+00, 2.80000000e+01],
       [2.72913000e+00, 2.70870000e-01, 3.00000000e+00],
       [6.04593266e+03, 6.00067340e+02, 6.64600000e+03],
       [9.09710000e-01, 9.02900000e-02, 1.00000000e+00],
       [2.72913000e+00, 2.70870000e-01, 3.00000000e+00],
       [6.54991200e+01, 6.50088000e+00, 7.20000000e+01],
       [1.81942000e+00, 1.80580000e-01, 2.00000000e+00],
       [9.09710000e-01, 9.02900000e-02, 1.00000000e+00],
       [1.70388683e+03, 1.69113170e+02, 1.87300000e+03],
       [5.45826000e+00, 5.41740000e-01, 6.00000000e+00],
       [8.56946820e+02, 8.50531800e+01, 9.42000000e+02],
       [5.22355482e+03, 5.18445180e+02, 5.74200000e+03],
       [5.45826000e+00, 5.41740000e-01, 6.00000000e+00],
       [1.46554281e+03, 1.45457190e+02, 1.61100000e+03],
       [2.09233300e+01, 2.07667000e+00, 2.30000000e+01],
       [4.98703022e+03, 4.94969780e+02, 5.48200000e+03],
       [2.72913000e+01, 2.70870000e+00, 3.00000000e+01],
       [9.09710000e+04, 9.02900000e+03, 1.00000000e+05]]))
```

The results are there, but are quite difficult to read. The only reason why I decided to also run the test with this library is because researchpy does not return degrees of freedom (see dof)

Now let's call the same test with library researchpy. This will give us much more readable results.

Firstly let's once again see the count for each country, but this time in percents:

```
                      most_common_user_name              
most_common_user_name                 False  True     All
country                                                  
AR                                     0.07  0.00    0.07
AT                                     0.00  0.00    0.01
AU                                     0.01  0.00    0.01
BD                                     0.00  0.00    0.00
BE                                     0.01  1.07    1.08
BO                                     0.02  0.00    0.02
BR                                     1.57  0.11    1.68
BY                                     1.54  0.51    2.05
CA                                     0.00  0.03    0.03
CH                                     0.11  0.00    0.11
CK                                     0.00  0.00    0.00
CN                                    45.41  3.47   48.88
CU                                     0.00  0.00    0.00
CZ                                     0.08  0.00    0.08
DE                                     1.16  0.12    1.28
EE                                     0.00  0.00    0.00
ES                                     0.96  0.06    1.02
FR                                     0.25  0.04    0.28
GB                                     1.71  0.17    1.88
GH                                     0.85  0.06    0.92
HK                                     1.83  0.17    2.00
HU                                     0.00  0.00    0.00
ID                                     0.97  0.06    1.03
IN                                     3.13  0.19    3.32
IQ                                     0.00  0.00    0.00
IR                                     0.00  0.00    0.00
IT                                     0.04  0.00    0.04
JP                                     0.03  0.00    0.03
KE                                     0.04  0.00    0.04
KG                                     0.04  0.00    0.04
KR                                     5.62  0.44    6.06
KZ                                     0.00  0.00    0.01
ME                                     0.00  0.00    0.00
MN                                     0.00  0.00    0.00
MX                                     1.73  0.12    1.85
NG                                     1.60  0.12    1.71
NL                                     0.88  0.10    0.98
NO                                     0.00  0.00    0.00
PH                                     0.02  0.00    0.02
PK                                     0.90  0.06    0.96
PL                                     0.00  0.00    0.00
PT                                     0.03  0.00    0.03
RO                                     0.00  0.00    0.00
RU                                     5.73  0.92    6.65
SC                                     0.00  0.00    0.00
SE                                     0.00  0.00    0.00
SG                                     0.06  0.02    0.07
SK                                     0.00  0.00    0.00
SY                                     0.00  0.00    0.00
TH                                     1.75  0.12    1.87
TJ                                     0.00  0.00    0.01
TR                                     0.88  0.06    0.94
TW                                     5.37  0.37    5.74
UA                                     0.00  0.00    0.01
US                                     1.38  0.23    1.61
UZ                                     0.02  0.00    0.02
VN                                     5.11  0.37    5.48
ZA                                     0.03  0.00    0.03
All                                   90.97  9.03  100.00
```

And the results are:

```
                 Chi-square test     results
0  Pearson Chi-square ( 57.0) =   12532.2095
1                     p-value =       0.0000
2                  Cramer's V =       0.3540
```

This would mean that variables are dependent (as p-value is less than 0.05). But sadly we cross a problem:

```
                      most_common_user_name            
most_common_user_name                 False       True 
country                                                
AR                                 66.40883     6.59117
AT                                  7.27768     0.72232
AU                                 12.73594     1.26406
BD                                  4.54855     0.45145
BE                                980.66738    97.33262
BO                                 22.74275     2.25725
BR                               1529.22251   151.77749
BY                               1863.08608   184.91392
CA                                 27.29130     2.70870
CH                                100.97781    10.02219
CK                                  0.90971     0.09029
CN                              44463.89567  4413.10433
CU                                  0.90971     0.09029
CZ                                 77.32535     7.67465
DE                               1161.69967   115.30033
EE                                  0.90971     0.09029
ES                                929.72362    92.27638
FR                                256.53822    25.46178
GB                               1712.07422   169.92578
GH                                833.29436    82.70564
HK                               1820.32971   180.67029
HU                                  1.81942     0.18058
ID                                937.00130    92.99870
IN                               3022.05662   299.94338
IQ                                  2.72913     0.27087
IR                                  3.63884     0.36116
IT                                 37.29811     3.70189
JP                                 30.02043     2.97957
KE                                 36.38840     3.61160
KG                                 36.38840     3.61160
KR                               5509.20376   546.79624
KZ                                  5.45826     0.54174
ME                                  3.63884     0.36116
MN                                  0.90971     0.09029
MX                               1684.78292   167.21708
NG                               1559.24294   154.75706
NL                                893.33522    88.66478
NO                                  0.90971     0.09029
PH                                 15.46507     1.53493
PK                                873.32160    86.67840
PL                                  2.72913     0.27087
PT                                 25.47188     2.52812
RO                                  2.72913     0.27087
RU                               6045.93266   600.06734
SC                                  0.90971     0.09029
SE                                  2.72913     0.27087
SG                                 65.49912     6.50088
SK                                  1.81942     0.18058
SY                                  0.90971     0.09029
TH                               1703.88683   169.11317
TJ                                  5.45826     0.54174
TR                                856.94682    85.05318
TW                               5223.55482   518.44518
UA                                  5.45826     0.54174
US                               1465.54281   145.45719
UZ                                 20.92333     2.07667
VN                               4987.03022   494.96978
ZA                                 27.29130     2.70870
```

Assumption for chi2 test of independence is that expected values are >5. Thus this test is unreliable.
