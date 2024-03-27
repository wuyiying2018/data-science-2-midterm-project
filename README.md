# data-science-2-midterm-project

## Models

non-linear
- MARS
- GAM

linear
- lasso
- Elastic net
ctrl1 <- trainControl(method = "cv", number = 10)
tuneGrid = expand.grid(alpha = seq(0, 1, length = 21),
                                       lambda = exp(seq(-25, 5, length = 100))),
# lasso & elastic net
lambda = exp(seq(-25, 5, length = 100))
- pls

classification
According to CDC, most patients appear to recover from acute COVID-19 illness within 4 weeks, which is 28 days. Classify outcome `recovery_time` into < 28 days: normal, >= 28 days: long.

- LDA
- QDA
ctrl2 <- trainControl(method = "repeatedcv", repeats = 5,
                     summaryFunction = twoClassSummary,
                     classProbs = TRUE)


set.seed(666)

data malnipulation

# remove id
data <- subset(dat, select = -id)

# set study A/B to 0/1
data$study <- ifelse(data$study == "A", 0, 1)


set.seed(666)
data_split <- initial_split(data, prop = 0.8)

# training data
training_data <- training(data_split)

# test data
testing_data <- testing(data_split)

# matrix of predictors
x <- model.matrix(recovery_time ~ ., training_data) [ ,-1]
y <- training_data$recovery_time

ctrl1 <- trainControl(method = "cv", number = 10)



