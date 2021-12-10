[![Creative Commons License: CC BY 4.0](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0/)

# References

__The Full Story of 1000 Cores: An Examination of Concurrency Control on Real(ly) Large Multi-Socket Hardware__
```
...
```

__Archived measurements__ (identical to this repo): https://tudatalib.ulb.tu-darmstadt.de/handle/tudatalib/3299
```
@misc{artefactMeasurements,
  url = { https://tudatalib.ulb.tu-darmstadt.de/handle/tudatalib/3299 },
  author = { Bang, Tiemo and May, Norman and Petrov, Ilia and Binnig, Carsten },
  publisher = { Technical University of Darmstadt },
  year = { 2021 },
  copyright = { Creative Commons Attribution 4.0 },
  title = { The Full Story of 1000 Cores: An Examination of Concurrency Control on Real(ly) Large Multi-Socket Hardware — Measurements, Logs, Plots }
}
```

__Source code of used DBMS prototype (optimised DBx1000)__: https://github.com/DataManagementLab/DBx1000

# General Structure

In the following data collection, we provide for all experiments discussed in "__The Tale of 1000 Cores: An Evaluation of Concurrency Control on Real(ly) Large Multi-Socket Hardware__"[1] and "__The Full Story of 1000 Cores: An Examination of Concurrency Control on Real(ly) Large Multi-Socket Hardware__"[2]:
- The configuration (".conf") and scripts (".sh") for the experimental setup, raw logs ("log.out", ".log"), profiling output ("\*.perf.\*"), and extracted measurements (".results.csv") compressed into measurements.zip;
- accumulated measurements ("result.csv") and resulting plots (".svg", ".tex", ".html").

The data collection is first organized as the experiments appear in the paper and
second by hardware platforms (HPE, Power8, and Power9) and a directory for combined plots.
Moreover, along the directories for tha hardware platforms there is a directory ("__comparison__") containing plots comparing their performance.

[1] Tiemo Bang, Norman May, Ilia Petrov, and Carsten Binnig. 2020. The Tale of 1000 Cores: An Evaluation of Concurrency Control on Real(ly) Large Multi-Socket Hardware. In International Workshop on Data Management on New Hardware (DAMON’20), June 15, 2020, Portland, OR, USA. ACM, New York, NY, USA, 9 pages. https://doi.org/10.1145/3399666.3399910

[2] Tiemo Bang, Norman May, Ilia Petrov, and Carsten Binnig. 2022. The Full Story of 1000 Cores: An Examination of Concurrency Control on Real(ly) Large Multi-Socket Hardware. *publication outstanding*

# Memory latency and bandwidth by NUMA (Section 2, Table 2)

[section_2_memory_latency_and_bandwidth](section_2_memory_latency_and_bandwidth) contains the raw data from the measurements of memory latency and bandwidth made with HCMT

# Simulation vs. Real Hardware
All following measurements were only executed on the HPE hardware platform.

---
## A First Look: Simulation vs. Reality (Section 3.1)

The following measurements contain the initial rerun of the original prototype on real hardware, Fig. 4 and Fig. 5.

[section_3-1_plain_original_results_high_conflict_4_warehouses](section_3-1_plain_original_results_high_conflict_4_warehouses) contains the measurements for high conflict workload with 4 warehouses, Fig. 4a and Fig. 5a.

[section_3-1_plain_original_results_low_conflict_1024_warehouses](section_3-1_plain_original_results_low_conflict_1024_warehouses) contains the measurements for high conflict workload with 4 warehouses, Fig. 4b and Fig. 5b.

---
## A Second Look: Hidden Secrets (Section 3.2)

### Hardware Assistance: The Good? (Section 3.2.1)

[section_3-2-1_hardware_timestamp_allocation](section_3-2-1_hardware_timestamp_allocation) contains the measurements when using hardware assisted timestamp allocation in the low conflict workload with 1024 warehouses, Fig. 6 and Fig. 7a.
For the speedup the measurements of original rerun with low conflict workload were used, i.e., [section_3-1_plain_original_results_low_conflict_1024_warehouses](plain_original_results_low_conflict_1024_warehouses).

### Data Sice: The Bad? (Section 3.2.2)

[section_3-2-2_data_size](section_3-2-2_data_size) contains the measurements for the full data size of TPC-C in the low conflict workload with 1024 warehouses, Fig. 7b and Fig. 8.
For the speedup in Fig. 8 the measurements of Section 3.2.1 were used, i.e., [section_3-2-1_hardware_timestamp_allocation](section_3-2-1_hardware_timestamp_allocation)

### Inserts: Facing Reality (Section 3.2.3)

[section_3-2-3_inserts](section_3-2-3_inserts) contains the measurement when including inserts in the TPC-C transactions in the low conflict workload with 1024 warehouses.

---
## Effect of State of the Art Optimisations (Section 3.3)

### Overview of Optimisations (Section 3.3.1)

[section_3-3-1_optimisations_overview_high_conflict_4_warehouses](section_3-3-1_optimisations_overview_high_conflict_4_warehouses) contains the measurements when consecutively applying our optimisations for the high conflict workload with 4 warehouses, Fig. 10a.

[section_3-3-1_optimisations_overview_low_conflict_1568_warehouses](section_3-3-1_optimisations_overview_high_conflict_1568_warehouses) contains the measurements when consecutively applying our optimisations for the low conflict workload with 1568 warehouses, Fig. 10b.

### Results after Optimisations (Section 3.3.2)

[section_3-3-2_optimised_high_conflict_1568_warehouses](section_3-3-2_optimised_high_conflict_1568_warehouses) contains the measurements when all optimisations are applied for the high conflict workload with 4 warehouses, Fig. 11a and Fig. 12a.

[section_3-3-2_optimised_low_conflict_1568_warehouses](section_3-3-2_optimised_low_conflict_1568_warehouses) contains the measurements when all optimisations are applied for the low conflict workload with 1568 warehouses, Fig. 11b and Fig. 12b.

# Broadening the Evaluation (Section 4)

## Intel-based vs. IBM Power 8/9 Platforms (Section 4.1)

[section_4-1_intel-based_vs_power_high_conflict_4_warehouses](section_4-1_intel-based_vs_power_high_conflict_4_warehouses) contains the measurements comparing the scalability of the three hardware platforms (HPE, Power8, Power9) for the high conflict optimisations, Fig. 13 and Fig. 14.

__[Time Breakdowns](section_4-1_intel-based_vs_power_high_conflict_4_warehouses/time_breakdown.md)__

[section_4-1_intel-based_vs_power_low_conflict_1568_warehouses](section_4-1_intel-based_vs_power_low_conflict_1568_warehouses) contains the measurements comparing the scalability of the three hardware platforms (HPE, Power8, Power9) for the low conflict optimisations, Fig. 15 and Fig. 16.
Power9 has measurements with __replicated internal__ data structures and for the __original__ implementation without this additional optimisation as well as plots comparing these.

__[Time Breakdowns](section_4-1_intel-based_vs_power_low_conflict_1568_warehouses/time_breakdown.md)__

The measurements for HPE correspond to those of Section 3.3.2 ([section_3-3-2_optimised_low_conflict_1568_warehouses](section_3-3-2_optimised_low_conflict_1568_warehouses), [section_3-3-2_optimised_high_conflict_1568_warehouses](section_3-3-2_optimised_high_conflict_1568_warehouses)).

---
## Zooming into Hardware Aspects (Section 4.2)

### Simultaneous Multithreading (Section 4.2.1)

[section_4-2-1_simultaneous_multithreading_low_conflict_1568_warehouses](section_4-2-1_simultaneous_multithreading_low_conflict_1568_warehouses) contains the measurements detailing the benefit of SMT on all hadware platforms for the low conflict workload, Fig. 17.
The measurements of the limited SMT of the Intel processor in the HPE platform are omitted from Fig. 17.

[section_4-2-1_simultaneous_multithreading_high_conflict_4_warehouses](section_4-2-1_simultaneous_multithreading_high_conflict_4_warehouses) contains the measurements detailing the benefit of SMT on all hadware platforms for the high conflict workload, Fig. 18.

### Non-uniform Memory Access (4.2.2)

[section_4-2-2_non-uniform_memory_access_isolated_effect](section_4-2-2_non-uniform_memory_access_isolated_effect) contains the measurements for the NUMA effect when operating across the distinct NUMA distances of the hardware platforms, Fig. 19.

[section_4-2-2_non-uniform_memory_access_workload-imposed_effect](section_4-2-2_non-uniform_memory_access_workload-imposed_effect) contains the measurements for the NUMA effect imposed by the workload (TPC-C remote transactions), Fig. 20.

[z_extra_non-uniform_memory_access_workload-imposed_effect_all_distances](z_extra_non-uniform_memory_access_workload-imposed_effect_all_distances) contains extra measurements for additional NUMA distances.

---
## The Full TPC-C Benchmark (Section 4.3)
The following measurements concern the performance for the full TPC-C transaction mix beyond the commonly used narrow transaction mix of only *NewOrder* and *Payment*.

### Full TPC-C under High Conflict

[section_4-3-1_full_TPC-C_high_conflict_4_warehouses](section_4-3-1_full_TPC-C_high_conflict_4_warehouses)
contains the measurements with the full TPC-C transaction mix under high conflict, Fig. 21 and Fig. 22.

__[Time Breakdowns](section_4-3-1_full_TPC-C_high_conflict_4_warehouses/time_breakdown.md)__

### Full TPC-C under Low Conflict

[section_4-3-1_full_TPC-C_low_conflict_1568_warehouses](section_4-3-1_full_TPC-C_low_conflict_1568_warehouses) contains the measurements with the full TPC-C transaction mix under low conflict, Fig. 23 and Fig. 24.

Power9 has measurements with __replicated internal__ data structures and for the __original__ implementation without this additional optimisation as well as plots comparing these.

__[Time Breakdowns](section_4-3-1_full_TPC-C_low_conflict_1568_warehouses/time_breakdown.md)__

The comparison of effect of the full TPC-C transaction mix vs. the narrow mix across the hardware platforms is located in [section_4-3-1_full_TPC-C_low_conflict_1568_warehouses/comparison_full_TPC-C_vs_narrow_TPC-C_all_hardware](section_4-3-1_full_TPC-C_low_conflict_1568_warehouses/comparison_full_TPC-C_vs_narrow_TPC-C_all_hardware),
especially the [detailed throughput comparison](section_4-3-1_full_TPC-C_low_conflict_1568_warehouses/comparison_full_TPC-C_vs_narrow_TPC-C_all_hardware/throughput-heatmap-comparison.svg).

Similarly, there are comparisons of the full vs. narrow mix for the individual hardware platforms [HPE: section_4-3-1_full_TPC-C_low_conflict_1568_warehouses/comparison_full_TPC-C_vs_narrow_TPC-C_hpe](section_4-3-1_full_TPC-C_low_conflict_1568_warehouses/comparison_full_TPC-C_vs_narrow_TPC-C_hpe), [Power8: section_4-3-1_full_TPC-C_low_conflict_1568_warehouses/comparison_full_TPC-C_vs_narrow_TPC-C_power8](section_4-3-1_full_TPC-C_low_conflict_1568_warehouses/comparison_full_TPC-C_vs_narrow_TPC-C_power8), and [Power9: section_4-3-1_full_TPC-C_low_conflict_1568_warehouses/comparison_full_TPC-C_vs_narrow_TPC-C_power9](section_4-3-1_full_TPC-C_low_conflict_1568_warehouses/comparison_full_TPC-C_vs_narrow_TPC-C_power9).

# Extra measurements

## Full TPC-C with Remote Transactions under Low Conflict

[z_extra_full_TPC-C_with_remote_transactions_low_conflict_1568_warehouses](z_extra_full_TPC-C_with_remote_transactions_low_conflict_1568_warehouses)

## Scalability for a Range of Warehouses with narrow TPC-C

[z_extra_scaling_for_range_of_warehouses](z_extra_scaling_for_range_of_warehouses)

## Scalability for a Range of Warehouses with full TPC-C

[z_extra_scaling_for_range_of_warehouses_with_full_TPC-C](z_extra_scaling_for_range_of_warehouses_with_full_TPC-C)

## Scalability for a Range of Warehouses with Range of Remote Transactions

[z_extra_scaling_for_range_of_warehouses_with_range_of_remote_transactions](z_extra_scaling_for_range_of_warehouses_with_range_of_remote_transactions)
