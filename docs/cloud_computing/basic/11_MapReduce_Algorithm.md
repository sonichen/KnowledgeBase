# MapReduce Algorithm Design

Programmers must specify: 

- **map** (k, v) → [<k2, v2>] 

- **reduce** (k2, [v2]) → [<k3, v3>] 

- all values with the same key are reduced together 

Optionally also: 

- **combine** (k, [v]) → <k, v> 

- **partition** (k, # of partitions) 

The execution framework handles everything else…

Eveything:

- Scheduling : assigns workers to map and reduce tasks 
- Data distribution :moves process to data 
- Synchronization : gathers, sorts, and shuffles intermediate data 
- Errors and faults :detects worker failures and restarts

## Pairs &Stripes

这个文章说的很清楚：https://www.cnblogs.com/koalaer/archive/2012/04/18/MapReduce_paris_stripes.html



## Secondary sorting