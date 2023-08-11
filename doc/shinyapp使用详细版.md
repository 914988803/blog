---
title: shinyapp的安装与使用
date: 2023-05-18
tags: - docker
      -笔记
categories: docker
---

```bash
docker run -d --name shinyapp -p 3838:3838 \
  -v /docker/shinyapp/:/srv/shiny-server/ \
  -v /docker/shinyapp/shinylog/:/var/log/shiny-server/ \
  rocker/shiny-verse
```

## 1.上述为在docker中安装shinyapp的教程

## 2.接下来使用docker ps 列出shinyapp的ID

```
docker ps
9cc2d5672e4f   rocker/shiny-verse              "/init"                   6 minutes ago    Up 6 minutes                 0.0.0.0:3838->3838/tcp, :::3838->3838/tcp
```

### 3.进入shinyapp并添加veen图的包

```
sudo docker exec -it f99b6668fa90 bash
```

```bash
sudo docker exec -it f99b6668fa90 bash
R
options(repos = c(CRAN = "https://mirrors.tuna.tsinghua.edu.cn/CRAN/"))
install.packages("VennDiagram")
install.packages("grid")
install.packages("ggsci")
install.packages("plotly")
##########
install.packages("shiny")
install.packages("shinydashboard")
install.packages("ggplot2")
install.packages("stringr")
install.packages("tidyr")
install.packages("shinythemes")
install.packages("BiocManager")
library(BiocManager)
BiocManager::install("clusterProfiler")
BiocManager::install("DESeq2")

###########install.packages("plotly")########
install.packages(c("ggplot2", "ggthemes", "scales", "viridis"))
install.packages("devtools")
devtools::install_github("ropensci/plotly")
install.packages("devtools", type = "win.binary")  #win install

#安装R包
q()
exit
docker restart <container-id>
```

## 3.5 rocker/shinyapp的R包的安装

首先，更改为镜像站

```
options(repos = c(CRAN = "https://mirrors.tuna.tsinghua.edu.cn/CRAN/"))
```

### 3.5.1  shinydashboard

```R
install.packages("shinydashboard")
```

### 3.5.2 DESeq2

```R
install.packages("BiocManager")
library(BiocManager)
BiocManager::install("DESeq2")
```

## 4.添加veen图的包

vi /docker/shinyapp/veen.R

```bash
library(shiny)
library(VennDiagram)

ui <- fluidPage(
  titlePanel("Venn Diagram Maker"),

  sidebarLayout(
    sidebarPanel(
      numericInput("A", "Set A:", value = 10, min = 0),
      numericInput("B", "Set B:", value = 10, min = 0),
      numericInput("C", "Intersection:", value = 5, min = 0)
    ),

    mainPanel(plotOutput("vennPlot"))
  )
)

server <- function(input, output) {
  output$vennPlot <- renderPlot({
    venn.plot <- draw.pairwise.venn(
      area1 = input$A,
      area2 = input$B,
      cross.area = input$C,
      category = c("Set A", "Set B"),
      fill = c("red", "blue")
    )

    grid.draw(venn.plot)
  })
}

shinyApp(ui = ui, server = server)
```

