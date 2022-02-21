CodeCarbon wasn't ready until the training was over so we only did an additional 10h run to measure with and then we can extrapolate to the whole training.

This set of records captures the startup time and 2499 iterations in 2 records per gpu, since there was also an intermediary checkpoint saved half-way and we flush the CC 
records on each checkpoint saving.

The training had 168000 iterations. Therefore multiply the reported data by 67. This would be quite approximate since we were using 16 nodes when doing 
the ramp up, then 64 and only the last 3 weeks 128 nodes.

Caveat emptor: I'm not sure whether CC-reports overlap since each report is per gpu and I think they may be measuring the same thing, other than the gpu itself. 
So this requires research.

Each csv file contains a report for a single gpu.



