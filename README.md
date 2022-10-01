# User_defined_function_in_R

#1)User define function for normallization of matrix
#Create a function to print the sum of squares of numbers in sequence
#Set the directory path
setwd("E:/Samiksha/M.Sc_Bioinformatics/SEM_3/Cancer_Genomics/Cancer_genomics_practical")

#Read the .csv data file
data<-read.csv("cancer.csv")
data

data1<-read.csv("cancer.csv", row.names = 1)
data1

#User define function of normalization by passing the argument
Function1 <- function(data1) {  
  for(i in 1:ncol(data1)) {     
    mat[,i]=(data1[,i]/sum(data1[,i]))*1000000  
    return(mat)
   
  }
}         
#Calling a function
Function1(data1)

pdf('Matrix_Normalization.pdf',width = 10,height = 10)

dev.off()






#2)User define function for z-score and hitmap
library(matrixStats)
library(ComplexHeatmap)

setwd("E:/Samiksha/M.Sc_Bioinformatics/SEM_3/Cancer_Genomics/Cancer_genomics_practical")

#Read the .csv data file
#data<-read.csv("cancer.csv")
#data

data1<-read.csv("cancer.csv", row.names = 1)
data1

mat=readRDS('log2cpm_matrix.rds')

function2=function(mat){
  for(i in 1:nrow(mat)){
    vec<-as.numeric(mat[i, ])
    zs[i, 1:ncol(zs)]<- (vec-mean(vec))/sd(vec)
  }
  
  
  z_score[is.na(z_score)]=0
  ZS_matrix = as.matrix(z_score)
  return(Heatmap(ZS_matrix))
}
function2(data)

pdf('ZScore_fun.pdf',width = 10,height = 10)

plot(1:5,pch=20)

dev.off()



