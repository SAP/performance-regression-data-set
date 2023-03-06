# Statistics for the Time Series

## time series with most elements

    max_len: 13552 id: 1155 example: ['1', '2021-09-01 12:09:26', '515218', '66.31652396172285']

## counters about unit and category

### unit

units top 50 of 16

    ('ms', 31491427)
    ('s', 4678140)
    ('TPS', 591103)
    ('us', 573517)
    ('count', 214038)
    ('DMLs', 145852)
    ('actions/(sec*threads)', 116662)
    ('SAPS', 76073)
    ('items per second', 71250)
    ('commits', 45763)
    ('RPS', 41027)
    ('logwrites', 38873)
    ('statements', 30310)
    ('trans/min', 21935)
    ('LPS', 8560)
    ('percent', 2496)

### category

category top 100 of 82

    ('elapsed time', 16349310)
    ('cpu time', 6826601)
    ('cpu service time', 5028076)
    ('elapsed time avg', 2133000)
    ('cpu service time avg', 2021761)
    ('elapsed time / query', 1386776)
    ('throughput', 443919)
    ('average commit duration', 443919)
    ('elapsed time/query', 286521)
    ('runtime', 241750)
    ('TPS', 199357)
    ('execution time', 162174)
    ('parallelism', 156821)
    ('blocking time', 122260)
    ('elapsed time (cpu normalized)', 109296)
    ('cpu time/query', 107810)
    ('avg_commit_duration', 92963)
    ('avg. dialogue step time', 76073)
    ('avg. dia db req. time', 76073)
    ('avg. up2 db req. time', 76073)
    ('avg. upd db req. time', 76073)
    ('total dialogue steps per minute', 76073)
    ('items per second', 71250)
    ('avg_propagation_delay', 66848)
    ('elapsed time / iteration', 55433)
    ('tps ratio', 52173)
    ('sum of cpu time from all processes', 50227)
    ('write actions', 49998)
    ('search actions', 49998)
    ('time', 48982)
    ('avg. dia wait req. time', 45763)
    ('commit rate', 45763)
    ('avg. upd wait req. time', 45763)
    ('avg dml count', 45763)
    ('avg. up2 wait req. time', 45763)
    ('max dml count', 45763)
    ('response time', 45763)
    ('total dml count', 45763)
    ('sum of lookup time from all processes', 45661)
    ('avg. lookup time', 45661)
    ('average runtime', 44616)
    ('avg cpu time', 41278)
    ('avg elapsed time', 41278)
    ('rps', 41027)
    ('elapsed_time_by_kernel', 41027)
    ('log write rate', 38873)
    ('i/o time', 37200)
    ('capture statement count', 30310)
    ('testjoinrepeated', 26765)
    ('testjoinsimple', 26765)
    ('testjoinstringsimple', 26765)
    ('testjoinstringrepeated', 26764)
    ('tpmc', 21935)
    ('cpu service milliseconds per request', 18368)
    ('query cpu runtime', 17306)
    ('total lock wait time', 17126)
    ('merge actions', 16666)
    ('total number of updates', 14986)
    ('query runtime', 14728)
    ('stopwatch', 14613)
    ('sum of average execution time from all processes', 14415)
    ('total cpu time', 13866)
    ('min elapsed time delta', 13866)
    ('total elapsed total time', 13866)
    ('cou time', 8798)
    ('atr_update_retry_count', 8563)
    ('atr_delete_retry_count', 8563)
    ('atr_total_retry_count', 8563)
    ('atr_elapsed_time_by_mon', 8563)
    ('atr_cpu_by_mon', 8563)
    ('min dml count', 8563)
    ('atr_insert_retry_count', 8563)
    ('atr_elapsed_time', 8560)
    ('lps', 8560)
    ('numcollisions', 7979)
    ('elapsed time per insert query', 7643)
    ('input dictionaries creation time', 7285)
    ('rates table build time', 7285)
    ('conversion time', 7285)
    ('compilation time', 7205)
    ('sum of scan time from all processes', 4566)
    ('cpu utilization', 2496)

## matrix (unit x category) with frequency

Pivot by columns (unit,category) in metadata.csv.
Or look at matrix csv files that have values:

- single: count each series as 1
- len: count the length of each series
