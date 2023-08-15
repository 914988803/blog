---
title: gff3与gtf文件的相互转换
date: 2023-05-18
tags: -生信文件操作
      -生信
      -笔记
categories: 生信
---
## 1.安装gffread：
```bash
conda install -c bioconda gffread
```

## 2.gff转gtf 
```bash
gffread gencode.v19.annotation.gff3 -T -o gencode.v19.gtf
```
## 3.gtf转gff
``` bash
gffread gencode.vM13.annotation.gtf -o gencode.vM13.annotation.gff3
```
