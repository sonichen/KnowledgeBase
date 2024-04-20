1.下载[TPC-H](https://www.tpc.org/tpc_documents_current_versions/current_specifications5.asp)

![image-20240418141947551](assets\image-20240418141947551.png)

2.解压文件后，进入dbgen文件夹，点击tpch.sln文件，用visual code打开

![image-20240418142059752](assets\image-20240418142059752.png)



点击，生成

![image-20240418142144557](assets\image-20240418142144557.png)

![image-20240418142136356](assets\image-20240418142136356.png)

成功

![image-20240418142205971](assets\image-20240418142205971.png)

此时生成了debug文件夹，把debug文件夹下的dbgen.exe复制到上一级目录下（也就是dbgen目录）

```
\TPC-H V3.0.1\dbgen> .\dbgen.exe -h
TPC-H Population Generator (Version 3.0.0 build 0)
Copyright Transaction Processing Performance Council 1994 - 2010
USAGE:
dbgen [-{vf}][-T {pcsoPSOL}]
        [-s <scale>][-C <procs>][-S <step>]
dbgen [-v] [-O m] [-s <scale>] [-U <updates>]

Basic Options
===========================
-C <n> -- separate data set into <n> chunks (requires -S, default: 1)
-f     -- force. Overwrite existing files
-h     -- display this message
-q     -- enable QUIET mode
-s <n> -- set Scale Factor (SF) to  <n> (default: 1)
-S <n> -- build the <n>th step of the data/update set (used with -C or -U)
-U <n> -- generate <n> update sets
-v     -- enable VERBOSE mode

Advanced Options
===========================
-b <s> -- load distributions for <s> (default: dists.dss)
-d <n> -- split deletes between <n> files (requires -U)
-i <n> -- split inserts between <n> files (requires -U)
-T c   -- generate cutomers ONLY
-T l   -- generate nation/region ONLY
-T L   -- generate lineitem ONLY
-T n   -- generate nation ONLY
-T o   -- generate orders/lineitem ONLY
-T O   -- generate orders ONLY
-T p   -- generate parts/partsupp ONLY
-T P   -- generate parts ONLY
-T r   -- generate region ONLY
-T s   -- generate suppliers ONLY
-T S   -- generate partsupp ONLY

To generate the SF=1 (1GB), validation database population, use:
        dbgen -vf -s 1

To generate updates for a SF=1 (1GB), use:
        dbgen -v -U 1 -s 1
```

生成数据集

```
.\dbgen.exe -vf -s 1
TPC-H Population Generator (Version 3.0.0)
Copyright Transaction Processing Performance Council 1994 - 2010
Generating data for suppliers table/
Preloading text ... 100%
done.
Generating data for customers tabledone.
Generating data for orders/lineitem tablesdone.
Generating data for part/partsupplier tablesdone.
Generating data for nation tabledone.
Generating data for region tabledone.
```

![image-20240418142407700](assets\image-20240418142407700.png)