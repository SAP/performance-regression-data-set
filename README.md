# Performance Regression Data Set

[![REUSE status](https://api.reuse.software/badge/github.com/SAP/performance-regression-data-set)](https://api.reuse.software/info/github.com/SAP/performance-regression-data-set)

A table of contents is provided by github directly (click on the
![list](https://raw.githubusercontent.com/primer/octicons/6933ac32f87a2cb5efda4fb74b39d1e6199134ce/icons/list-unordered-24.svg)
icon in front of README.md)

This repository provides data sets on performance measurements to support
research on performance regression detection.

Available data sets:

1) small
    - A small data set from SAP HANA internal testing to explore the data format


## On (automated) performance regression detection

Assume we have a software under test SUT that provides an important
functionality F. SUT may evolve over time. Starting with a version v_1, each
change may lead to a new version v_n.

Objective: Detect if a change increases the execution time of F and therefore
results in a performance regression.

In a practical scenario, we want to detect changes that have a negative impact
on performance before they are delivered to customers. A typical way to achieve
this are change-based performance measurements. Simplified, for each new version
v_(n+1), we determine the execution time t_(n+1) of F and compare it to t_n for
version v_n. This approach results in a series of time measurements.

### Time Series of Measurements

A series of measurements consists of n data points for m <= n different
versions. There is one measurement for each version if n == m, but there may be
multiple measurements for at least one version if n > m.

We typically measure execution time (in units like milliseconds, seconds, minutes
or hours), but we can also measure memory usage, cpu usage, network traffic,
latency or any other metric.

A time series is ordered by time or provides information to be ordered by time.

### Problem

Detecting whether a regression occurred sounds first like a trivial problem: We
can just compare the new value v_n at t_(m+1) against the old value t_o at t_m.
We report a regression if t_n > t_o.

However, this approach may not be applicable in practice. We will iterate over
several practical issues.

> Performance measurements must handle deviations.

We rarely measure deterministic execution in practice. Think about dynamic cpu
frequency scaling, caches, thread scheduling, shared resource access, system
load, cpu internal caches, branch prediction, memory prefect, or any other
random interaction of the system under tests with the software under test. We
may even use different systems for performance measurements if the required time
to execute them of too long on a single machine.
Given these examples, it is unreasonable to assume perfect deterministic
execution. Therefore, we cannot apply the comparison in a strict mathematical
sense.

We could argue that, given enough time, we could do an infinite amount of
measurements to calculate a statistical stable value. However, we may not have
infinite time and resources in practice.

Therefore, we must utilize a significant threshold ts in an absolute way or
relative way. For example, we only detect a regression if t_n - t_o > ts
(absolute) or if t_n / t_o > ts (relative).

> It is unclear how large a difference must be to be considered a regression.

Do we accept t_n = 500 seconds compared to t_o = 490 seconds? This decision
depends on the context and cannot be answered in general.

> A trend may hide regressions.

Assume a linear increasing time series where each change is below our threshold.
We will not report any change as a regression, but over time performance may
have decreased by several factors. Should we compare each new value against all
old values?

> Changes in the software may influence the performance by purpose.

We may anticipate and accept an increase in execution time. How does our
detection approach now adapt to the change in our time series data?

> The reality does not produce clean time series.

We may think about time series that represent smooth lines if plotted. However,
practical results may have a lot of noise for a wide range of reasons. See the
examples section.

> False positives and false negatives should be avoided.

False positives result in human intervention. Humans will lose trust if there
are too many false positives and if they spent too much time on manual analysis,
then we could skip the automatic analysis at all.

False negatives represent performance regressions which may be costly if they
are delivered to the customer or must be corrected in later development stages.

> In summary, we want an automated approach that is robust, adaptive, cheap, and
> has a high precision and recall.

The priority for each attribute may vary depending on the use case.

### Examples

Each figure represents a chart where the x-axis is time and the y-axis is some
value. The charts do not contain units as they are not relevant for the
examples.

The first example is the most simple, a stable time series that represents maybe
some functionality that never changed over the whole observation period.

![example_example_stable](pics/examples/classification/example_stable.png
"Stable performance measurements")

The second chart is also rather simple as it clearly represents a regression
that occurred about in the mid of the measurements. However, already here we
could ask whether that one value after the first fifth may already have been a
regression.

![example_regression](pics/examples/classification/example_regression.png
"A regression")

The next charts show practical measurements where no regression occurred, but
the time series look different to the first example of a stable time series.

The following chart shows symptoms that can be classified as build dependent.
Based on how the software is build, we get different performance characteristics
although nothing in the implementation has changed.

![example_build-dependent](pics/examples/classification/example_build-dependent.png
"Build dependent performance measurements")

The next chart shows spikes. They occur due to external influence on the
performance measurements.

![example_spikes](pics/examples/classification/example_spikes.png
"Spikes that are not regressions")

The last chart shows an example with a rather high deviation. Although the time
series itself is not stable, the deviations are stable. Overall, there are no
performance regressions.

![example_high_deviation](pics/examples/classification/example_high_deviation.png
"Large deviations")

## How to use the data sets

Each data set contains specific files that describe the data format.

You are free to use the data sets according to the license declared by this
repository. You can refer to a specific data set either via the name that is
used here or just refer to the whole repository.

Examples for online reference:

- performance regression data set from SAP,
  https://github.com/SAP/performance-regression-data-set
- [performance regression data set from SAP](https://github.com/SAP/performance-regression-data-set)

Examples for citations

- Thomas Bach, Pal Lv, Minh Le. "Performance Regression Data Set"
  - Venue will be added if it exists.
- Biblatex via CITATION.cff file (rendered in github)

Please inform use via issue or email if you use this data set so we can provide
links to your work.
