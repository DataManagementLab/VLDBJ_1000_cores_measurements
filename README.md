## General Structure

In the following data collection, we provide for all experiments discussed in __[paper](paper)__: __1.__ The configuration (".conf") and scripts (".sh") for the experimental setup, raw logs ("log.out", ".log"), and extracted measurements (".results.csv") compressed into measurements.zip; __2.__ accumulated measurements ("result.csv") and resulting plots (".svg", ".tex").

The data collection is first organized as the experiments appear in the paper and
second by hardware platforms (HPE, Power8, and Power9).

## Memory latency and bandwidth by NUMA (Section 2, Table 2)

[section_2_memory_latency_and_bandwidth](section_2_memory_latency_and_bandwidth) contains the raw data from the measurements of memory latency and bandwidth made with HCMT

# Simulation vs. Real Hardware
All following measurements were only executed on the HPE hardware platform.

## A First Look: Simulation vs. Reality (Section 3.1)

The following measurements contain the initial rerun of the original prototype on real hardware, Fig. 4 and Fig. 5.

[section_3-1_plain_original_results_high_conflict_4_warehouses](plain_original_results_high_conflict_4_warehouses) contains the measurements for high conflict workload with 4 warehouses, Fig. 4a and Fig. 5a.

[section_3-1_plain_original_results_low_conflict_1024_warehouses](plain_original_results_low_conflict_1024_warehouses) contains the measurements for high conflict workload with 4 warehouses, Fig. 4b and Fig. 5b.

## A Second Look: Hidden Secrets (Section 3.2)

### Hardware Assistance: The Good? (Section 3.2.1)

[section_3-2-1_hardware_timestamp_allocation](section_3-2-1_hardware_timestamp_allocation) contains the measurements when using hardware assisted timestamp allocation in the low conflict workload with 1024 warehouses, Fig. 6 and Fig. 7a.
For the speedup the measurements of original rerun with low conflict workload were used, i.e., [section_3-1_plain_original_results_low_conflict_1024_warehouses](plain_original_results_low_conflict_1024_warehouses).

### Data Sice: The Bad? (Section 3.2.2)

[section_3-2-2_data_size](section_3-2-2_data_size) contains the measurements for the full data size of TPC-C in the low conflict workload with 1024 warehouses, Fig. 7b and Fig. 8.
For the speedup in Fig. 8 the measurements of Section 3.2.1 were used, i.e., [section_3-2-1_hardware_timestamp_allocation](section_3-2-1_hardware_timestamp_allocation)

### Inserts: Facing Reality (Section 3.2.3)

[section_3-2-3_inserts](section_3-2-3_inserts) contains the measurement when including inserts in the TPC-C transactions in the low conflict workload with 1024 warehouses.

## Effect of State of the Art Optimisations (Section 3.3)

### Overview of Optimisations (Section 3.3.1)

[section_3-3-1_optimisations_overview_high_conflict_4_warehouses](section_3-3-1_optimisations_overview_high_conflict_4_warehouses) contains the measurements when consecutively applying our optimisations for the high conflict workload with 4 warehouses, Fig. 10a.

[section_3-3-1_optimisations_overview_low_conflict_1568_warehouses](section_3-3-1_optimisations_overview_high_conflict_1568_warehouses) contains the measurements when consecutively applying our optimisations for the low conflict workload with 1568 warehouses, Fig. 10b.

### Results after Optimisations (Section 3.3.2)

[section_3-3-2_optimised_high_conflict_1568_warehouses](section_3-3-2_optimised_high_conflict_1568_warehouses) contains the measurements when all optimisations are applied for the high conflict workload with 4 warehouses, Fig. 11a and Fig. 12a.

[section_3-3-2_optimised_low_conflict_1568_warehouses](section_3-3-2_optimised_low_conflict_1568_warehouses) contains the measurements when all optimisations are applied for the low conflict workload with 1568 warehouses, Fig. 11b and Fig. 12b.