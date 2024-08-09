#创建新的变量
##
mydata <- data.frame(x1 = c(2, 2, 6, 4),
                     x2 = c(3, 4, 2, 8)) 

mydata <- transform(mydata, 
                    sumx = x1 + x2,
                    meanx = (x1 + x2)/2)

#变量的重编码
##
leadership$age[leadership$age == 99] <- NA 

leadership$agecat[leadership$age > 75] <- "Elder"
leadership$agecat[leadership$age > 55 &
                  leadership$age <= 75] <- "Middle Aged"
                  
leadership$agecat[leadership$age < 55] <- "Young"

更加紧凑

leadership <- within(leadership,{

                      agecat <- NA
                      
                      agecat[age > 75] <- "Elder"
                      
                      agecat[age >=55 & age < 75] <- "Middle Aged"
                      
                      agecat[age < 55] <- "Young"
                      
})


#变量的重新命名
##

交互式编辑器

fix(leadership)

以编程的方式命名

names(leadership)[2] <- "testDate"

names(leadership)[6:10] <- c("item1", "item2", "item3", "item4", "item4")

使用包plyr命名

library(plyr)

leadership <- rename(leadership,

                     c(manager = "managerID", date = "testDate")
                     
                     )
                    

#缺失值处理
##

y <- c(1, 2, 3, NA)

检测缺失值，会布尔值

is.na(y)

is.na(leadership[,6:10])

重编码缺失值

leadership$age[leadership$age == 99] <- NA

在计算中避免缺失值

x <- c(1, 2, NA, 3)

y <- sum(x, na.rm = TRUE)

删除具有缺失值的观测

newdata <- na.omit(leadership)

mydates <- as.Date(c("2007-06-22", "2004-02-13"))

mydates

#日期
##

strDates <- c("01/05/1965", "08/16/1975")

dates <-as.Date(strDates, "%m/%d/%y")

dates

myformat <- "%m/%d/%y"

leadership$testDate <- as.Date(leadership$testDate, myformat)

返回当天的日期

Sys.Date()

#返回当前的日期和时间
date()

today <-Sys.Date()

format(today, format = "%B %d %Y")

format(today, format = "%A")

#自1970年以来的天数
startdate <- as.Date("2004-02-13")

enddate <- as.Date("2011-01-22")

days <- enddate-startdate



#使用diffitime()来计算时间间隔，并以星期、天、时、分和秒来表示。
today <-Sys.Date()

dob <- as.Date("1956-10-12")

difftime(today, dob, units = "weeks")

#将日期转化为字符串变量
starDates <- as.character(dates)

#数据类型得转化和判断
##
#判断
a <- c(1, 2, 3)
a
is.numeric(a)
is.vector(a)

#转化
a <- as.character(a)
a
is.numeric(a)

is.character(a)

#排序
##
按照年龄排序

newdata <- leadership[order(leadership$age)]


按照性别排序（先F后M）,然后在按照年龄递减排序
attach(leadership)

newdata <- leadership[order(gender, -age),]

detach(leadership)






