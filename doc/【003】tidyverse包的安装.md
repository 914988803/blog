---
title: tidyverse包的安装
date: 2023-05-18
tags: -生信
      -R
categories: 生信
---

## 1.安装相关依赖

```bash
sudo apt-get install libfreetype6-dev libpng-dev libtiff5-dev libjpeg-dev libharfbuzz-dev libfribidi-dev libgtk-3-dev fontconfig ibxml2-dev libcurl4-openssl-dev libssl-dev libgmp3-dev libxml2-dev
```

## 2.安装R中的依赖

```R
install.packages(c("ggplot2", "dplyr", "tidyr", "readr", "purrr", "tibble", "stringr", "forcats", "lubridate", "data.table"))
```
