# data-science-2-midterm-project

## Models

MARS

Elastic net

LDA

set.seed(666)

data malnipulation
```{r}
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
```
ctrl1 <- trainControl(method = "cv", number = 10)


