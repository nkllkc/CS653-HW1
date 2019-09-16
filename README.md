# CS653-HW1

## 1. Computational complexity

Output of running the _fmm2d.c_:

```console
L = 4
Npar = 1000 * 4^(0) = 1000
===== Max potential difference = 4.972490e-06 =====
===== Total FMM vs. direct energies & error = -1.101546e+05 -1.101546e+05 -2.055468e-08 =====
===== FMM & direct CPU times = 4.754000e-02 3.081600e-02 =====

L = 5
Npar = 1000 * 4^(1) = 4000
===== Max potential difference = 4.960206e-06 =====
===== Total FMM vs. direct energies & error = -1.101546e+05 -1.101546e+05 -2.738719e-08 =====
===== FMM & direct CPU times = 9.298200e-02 2.616900e-02 =====

L = 6
Npar = 1000 * 4^(2) = 16000
===== Max potential difference = 4.957777e-06 =====
===== Total FMM vs. direct energies & error = -1.101546e+05 -1.101546e+05 -2.603903e-08 =====
===== FMM & direct CPU times = 2.713620e-01 2.614500e-02 =====

L = 7
Npar = 1000 * 4^(3) = 64000
===== Max potential difference = 4.956997e-06 =====
===== Total FMM vs. direct energies & error = -1.101546e+05 -1.101546e+05 -2.695153e-08 =====
===== FMM & direct CPU times = 1.014456e+00 2.635400e-02 =====
```

### Plots
![Plot of FMM](plots/1a_plot_fmm.jpg)
![Plot of Direct](plots/1a_plot_direct.jpg)

### The Fitting Parametars Values
|   |FMM|Direct|
|---|---|---|
|**p**| 0.9153 | 0.03798 |
|**C**| 4.037e-05 | -0.03664 |

### Fitted Plots
![Plot of FMM](plots/1a_fit_fmm.jpg)
![Plot of Direct](plots/1a_fit_direct.jpg)

### Output of MATLAB's Fitting Tool

```console
Fit for FMM:
    General model:
     f(x) = c*power(x,p)
     Coefficients (with 95% confidence bounds):
       c =   4.037e-05  (-5.409e-05, 0.0001348)
       p =      0.9153  (0.7018, 1.129)
    
    Goodness of fit:
      SSE: 0.0009753
      R-square: 0.9984
      Adjusted R-square: 0.9976
      RMSE: 0.02208
    

Fit for Direct:
    General model:
     f(x) = c*power(x,p)
     Coefficients (with 95% confidence bounds):
       c =     0.03797  (0.006751, 0.06918)
       p =     -0.0366  (-0.1285, 0.05531)

    Goodness of fit:
      SSE: 6.531e-06
      R-square: 0.5879
      Adjusted R-square: 0.3819
      RMSE: 0.001807
```

### Explanation

    TODO(nikola):

##  2. Flop/s Performance

The modified source code is [here](src/fmm2d.c).

Output is:
```console
L = 6
Npar = 1000 * 4^(2) = 16000
===== Gflop/s for FMM = 4.893305e-01 =====
===== Gflop/s for Direct = 7.389793e-01 =====
===== Max potential difference = 4.957777e-06 =====
===== Total FMM vs. direct energies & error = -1.101546e+05 -1.101546e+05 -2.603903e-08 =====
===== FMM & direct CPU times = 2.893460e-01 2.704000e-02 =====
```

The machine information:
```console
Architecture:        x86_64
CPU op-mode(s):      32-bit, 64-bit
Byte Order:          Little Endian
CPU(s):              12
On-line CPU(s) list: 0-11
Thread(s) per core:  2
Core(s) per socket:  6
Socket(s):           1
NUMA node(s):        1
Vendor ID:           GenuineIntel
CPU family:          6
Model:               158
Model name:          Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz
Stepping:            10
CPU MHz:             800.044
CPU max MHz:         4600.0000
CPU min MHz:         800.0000
BogoMIPS:            6384.00
Virtualization:      VT-x
L1d cache:           32K
L1i cache:           32K
L2 cache:            256K
L3 cache:            12288K
NUMA node0 CPU(s):   0-11
Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d
```
