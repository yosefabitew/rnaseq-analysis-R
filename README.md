# rnaseq-analysis-R-using-DESeq2

setwd("/your/working/directory")
tissue=c("JejM")
outlier= c("None")#c("22B11108","24B11010")                 
trial="2a"
outputPrefix <- "atac_DESeq2"

###library----
library(dplyr)
library(pander)
library(DESeq2)
library(apeglm)
library(qvalue)
library(ggplot2)
library(reshape2)
library(pheatmap)
library(refGenome)
library(PoiClaClu)
library(genefilter)
library(RColorBrewer)
library(ReportingTools)
library(variancePartition)


directory <- "/Path/for/your/count/files"
sampleFiles <- grep("counts",list.files(directory),value=TRUE)
anno <- read.table('.annotated.gene.txt', header = F, sep = '\t')
pheno <- readxl::read_excel('pheno.xlsx')
sampleCondition <- pheno$condition
sampleTable <- data.frame(sampleName = sampleFiles,
                          fileName = sampleFiles,
                          condition = sampleCondition)


