

```R
library(reshape2)
library(ggplot2)

data <- read.table('so',header = T)
#head(data)

data_m <- melt(data, id.vars=c('gene'))
#head(data_m)

p <- ggplot(data_m, aes(x = variable, y = gene))
p <- p + geom_tile(aes(fill = value))
p <- p + scale_fill_gradient(low='white',high='red')

ggsave(p, filename="heatmap.pdf", width=30,height=90, units=c("cm"),colormodel="srgb")
```


```R
library(pheatmap)
data <- read.table('so',header = T,row.names = 1)
pheatmap(data, cellwidth = 30, cellheight = 25,cluster_rows=FALSE, cluster_cols=FALSE, filename="pheatmap_101.pdf")
```
