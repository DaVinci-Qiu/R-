
##

进入目录
setwd("C:\Users\lbzzj\Desktop\R.workspace")

#图形参数

##

使用opar来制定这些选项，除非再次被修改否者将一直有效
dose <- c(20, 30, 40, 45, 60)

drugA <- c(16, 20, 27, 40, 60)

drugB <- c(15, 18, 25, 31, 40)

opar <- par(no.readonly = TRUE)

par(lty = 2, pch = 17)

plot(dose, drugA, type = "b")

par(opar)

plot(dose, drugA, type = "b", lty = 3, lwd = 3, pch = 15, cex = 2)



