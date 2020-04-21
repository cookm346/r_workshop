```r

#math
    2 + 3
    2 * 3
    2 - 3
    2 / 3
    2^3
    10 %% 6

#white space
    2+2
    2   +   2

#order of operations
    2 + 2 * 3
    (2 + 2) * 3

#assignment operator
    x <- 2
    x
    print(x)
    x + 3
    x^3
    x <- 3/2
    x

#integer sequences
    1:5
    0:5
    -10:10
    -100:100 #[]
    x <- 10:20
    x + 3

#concatenation
    x <- c(1, 2, 3, 4, 5)
    x
    x + 3

#relational operators
    2 > 3
    2 < 3
    2 >= 3
    2 <= 3
    2 == 3
    2 != 3
    (2 + 3) > (5 + 0)
    
    x > 3
    x == 3

#optional asignment operator
    x = 1:5
    
#logical operators
    TRUE & FALSE
    TRUE | FALSE
    
    (3 < 10) & (3 > 5)
    (3 < 10) | (3 > 5)
    
#comments
    x + 2 #r will ignore everything to right of #
    # x + 2

#semi-colons
    2 + 3; 2 * 3; 2 / 3


#multi line code
x *
    
    #esc
    #tab
    #up arrow
    #alt -
    
#subsetting and accessing elements of a vector
    
    x <- 10:20
    
    #with indices
    x[1]
    x[2]
    x[1:5]
    x[c(1, 3, 5, 7, 9)]
    x[-5]
    
    x[-5:6] #careful
    x[-(5:6)]
    
    1:10^2
    (1:10)^2
    
    #with boolean 
    x[x > 15]
    x[x != 15]

#changing elements of a vector
    #with indices
    x[1] <- 22
    x[4:7] <- 0
    x[-1] <- 10
    
    #with boolean values
    x[x == 0] <- 22
    x[x > 5] <- 0

#descriptive statistical/useful functions
    x <- 1:25
    
    length(x)
    unique(x)
    sum(x)
    min(x)
    max(x)
    mean(x)
    median(x)
    var(x)
    sd(x)
    quantile(x)
    summary(x)
    which(x > 5)

    (x - mean(x))^2
    
#missing values
    x <- c(1, 2, NA, NA, 5)
    length(x)
    mean(x)
    sd(x)
    
    mean(x, na.rm = TRUE)
    sd(x, na.rm = TRUE)
    
    is.na(x)
    x[!is.na(x)]
    
    mean(x[!is.na(x)])
    sd(x[!is.na(x)])
    
#assigning output to a variable
    x <- mean(x)
    
#random variable functions
    rnorm(5)
    rnorm(5)
    sample(1:6, 2, TRUE)
    runif(10, 0, 1)
    
#inferential statistical functions
    x <- rnorm(100)
    y <- rnorm(100)
    f <- factor(rep(c(0, 1), 50), labels = c("g1", "g2"))
    f <- gl(2, 50)
    
    x <- iris$Petal.Length
    y <- iris$Petal.Width
    f <- iris$Species
    
    cor(x, y)
    cor.test(x, y)
    t.test(x, y, var.equal = TRUE)
    summary(aov(y ~ f)) #specify data method also
    summary(lm(y ~ x))

#nested functions
    x <- rnorm(100)
    hist(x)
    hist(rnorm(100))
    length(unique(x))

#help
    ?mean
    ?rnorm

#ifelse
    x <- 1:10
    ifelse(x > 5, 1, 0)
    ifelse(x > median(x), 1, 0)

#if statements
    x <- -1
    if(x > 0){
        print("x is greater than 0")
    } else if (x == 0) {
        print("x is equal to 0")
    } else {
        print("x is less than 0")
    }


#other types of vectors
    c("a", "b", "hello")
    x <- factor(c(0, 0, 1, 1), labels = c("male", "female"))
    x <- factor(c("male", "male", "female", "female"))
    
#lists
    l <- list(rnorm(5), rnorm(5))
    l[1]
    
    l <- list(x = rnorm(5), y = rnorm(5))
    l$x

#functions with more than one argument
#arguments can be matched by position or name
    rnorm() #tab
    rnorm(10, 0, 1)
    rnorm(n = 10, mean = 0, sd = 1)
    rnorm(mean = 0, sd = 1, n = 10)
    
    #spacing revisited
    rnorm(100, 
          0, 
          1)

#histograms
    x <- rnorm(100)
    hist(x)
    
#scatterplots
    x <- rnorm(100)
    y <- rnorm(100)
    plot(x, y)

#creating functions
    adder <- function(x, y){
        return(x + y)
    }
    
    adder(3, 4)
    adder(x = 3, y = 4)
    adder(y = 4, x = 3)
    
    #x or y will not be changed or added in enviroment (local variable)

#empty vectors
    x <- rep(0, 10)
    x <- vector("numeric", 10)
    x <- array(0, 10)

#for loop and populating an empty vector
    for(i in 1:100){
        print(i^2)
    }

    x <- rep(0, 10)

    for(i in 1:10){
        x[i] <- i^2
    }
    
    x <- rep(0, 10)
    
    for(i in 1:10){
        x[i] <- mean(rnorm(100, 0, 1)) 
    }
    
    hist(x)
    mean(x)
    
    x > .1
    sum(x > 0.1) / length(x)

#matrices
    matrix(0, 4, 5)
    m <- matrix(1:20, 4, 5) #filled column-wise
    
#matrix math
    m + 1:4
    m - 1:4
    m * 1:4
    
    m %*% t(m)

#subsetting a matrix
    m[1, 1]
    m[2, 1]
    m[1:3, 2:3]
    m[2, ]
    m[ , 3]

#matrix functions
    nrow(m)
    ncol(m)
    dim(m)

#binding
    cbind(m, m)
    rbind(m, m)

#statistical matrix functions
    rowMeans(m)
    colMeans(m)

#apply
    apply(m, 1, mean) == rowMeans(m)
    mean(m[1, ])

    apply(m, 2, mean)
    apply(m, 2, sd)

#dataframes
    str(iris)
    summary(iris)
    head(iris)
    tail(iris)

    x <- c(1, 2, 3, "four")
    
    d <- data.frame(x1 = rnorm(100), x2 = rnorm(100))
    
    dimnames(d) <- list(paste("sub", 1:10), c("v1", "v2"))
    
    d$v2

#aggregate and apply
    aggregate(formula = Petal.Length ~ Species, data = iris, FUN = mean)
    
    
    s <- split(iris, iris$Species)
    sapply(s, function(x){colMeans(x[,1:4], na.rm=TRUE)})

#interaction variables
    f1 <- gl(3, 5)
    f2 <- gl(5, 3)
    f <- interaction(f1, f2)

#character vectors
    x <- c("hello", "my", "name", "is")
    
    colnames(m) <- c("var. 1", "var. 2")


#reading and writing files
    getwd()
    setwd("SOME/DIRECTORY")
    read.csv()
    read.csv("file", stringsAsFactors = FALSE)
    read.table()
    
    write.csv()

#example
    d <- read.csv(url("http://www.numbermunch.com/data.csv"))
    
    boxplot(Hap1 ~ Gender + Major, data = d)
    means <- aggregate(Hap1 ~ Major + Gender, data = d, FUN = mean)
    barplot(means[,3], names.arg = interaction(means[,1], means[,2]))
    
    summary(lm(Hap1 ~ Gender + Major, data = d))
    summary(aov(Hap1 ~ Gender + Major, data = d))

```
