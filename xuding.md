#this a practice for spline for ggplot2
xdata1 <- read.csv('/home/ying/xuding1.csv',header = F)
ndata1 <- na.omit(xdata1)
xdata2 <- read.csv('/home/ying/xuding2.csv',header = F)
ndata2 <- na.omit(xdata2)

smooth.spline2 <- function(formula, data, ...) { 
    mat <- model.frame(formula, data) 
    smooth.spline(mat[, 2], mat[, 1]) 
} 

predictdf.smooth.spline <- function(model, xseq, se, level) { 
    pred <- predict(model, xseq) 
    data.frame(x = xseq, y = pred$y) 
} 


p <- qplot(V1,V2,data = ndata1,color=I('blue'),alpha=I(1/1000),main = 'BioSeNPs')
p <- p + labs(x='Wavenumber(nm)',y='Absorbance') + theme(plot.title = element_text(hjust = 0.5))
p <- p + geom_smooth(method = "smooth.spline2", se= F,color=I('blue'))

plot(p)

p1 <- qplot(V1,V2,data = ndata2,color=I('black'),alpha=I(1/1000),main = 'CheBioSeNPs')
p1 <- p1 + labs(x='Wavenumber(nm)',y='Absorbance') + theme(plot.title = element_text(hjust = 0.5))
p1 <- p1 + geom_smooth(method = "smooth.spline2", se= F,color=I('black'))

plot(p1)
