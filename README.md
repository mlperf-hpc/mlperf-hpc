# MLPerf HPC

**DEPRECATED** - This repository is deprecated. The reference implementations
for MLPerf HPC benchmarks have moved to https://github.com/mlcommons/hpc.

This is a landing page for the MLPerf HPC working group and benchmark suite.
This material will eventually be moved into https://github.com/mlcommons.

## Overview

The HPC working group in [MLPerf](https://mlperf.org/) is working on ML
benchmarking on supercomputers. We are currently working on publishing a v0.5
HPC training benchmark suite. For an overview, please see
[these slides from the MLBench workshop at ISPASS 2020](https://docs.google.com/presentation/d/1ZXi9JHewwTj7-fLQLmd5oxYhRrdhxo95AfzKLeu20Jg/edit?usp=sharing).

Group chairs:
- Steven Farrell, Lawrence Berkeley National Laboratory
- Jacob Balma, Hewlett Packard Enterprise
- Abid Malik, Brookhaven National Laboratory

Deputy chairs:
- Murali Emani, Argonne National Laboratory
- Aristeidis Tsaris, Oak Ridge National Laboratory

To join the group, first join the general MLPerf group and then the HPC working
group as described here: https://mlperf.org/get-involved/

## Benchmarks

Reference implementations are at [benchmarks](benchmarks).

### Datasets

Instructions to acquire the datasets are given in the reference implementation READMEs.

### Rules

The MLPerf HPC v0.5 rules are based on the MLPerf Training v0.7 rules with
some adjustments.

The MLPerf Training rules are available at [training\_rules](https://github.com/mlperf-hpc/training_policies/blob/hpc-0.5.0/training_rules.adoc).

The MLPerf HPC specific rules are at [hpc\_training\_rules](https://github.com/mlperf-hpc/training_policies/blob/hpc-0.5.0/hpc_training_rules.adoc).

### Compliance

The MLPerf logging package implements logging and compliance-checking utilities
for MLPerf benchmarks. We have a temporary fork and hpc-0.5.0 branch in which we
are adding support for MLPerf-HPC v0.5 at
https://github.com/mlperf-hpc/logging/tree/hpc-0.5.0

To install and test compliance of your runs/submissions:
```
# Install the package into your python environment.
# A development install (-e) is recommended for now so you can pull new updates.
git clone -b hpc-0.5.0 https://github.com/mlperf-hpc/logging.git mlperf-logging
pip install [--user] -e mlperf-logging

# Test compliance of a specific mlperf hpc log file
python -m mlperf_logging.compliance_checker --ruleset hpc_0.5.0 $logFile

# Test a system description file (we just use the Training v0.7 rules)
python -m mlperf_logging.system_desc_checker $jsonFile training 0.7.0

# Test a full submission folder
python -m mlperf_logging.package_checker $submissionDir hpc 0.5.0
```
