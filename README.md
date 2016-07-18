# Deep-Learning

##Import databricks file
dataPath = "/FileStore/tables/rnxx88hf1468830017337/to_dummyvars.csv"
health = sqlContext.read.format("com.databricks.spark.csv")\
  .option("header","true")\
  .option("inferSchema", "true")\
  .load(dataPath)
  

#Convert to pandas
import pandas as pd
df = health.toPandas()
#Convert to numpy
df1 = df.values


#Convert to keras format
from keras.models import Sequential
from keras.layers import Dense
from keras.utils.np_utils import to_categorical
X = df1[:,:-1].astype(float)
Y = to_categorical(df1[:,-1:].astype(int))



#Model building
# create model
model = Sequential()
model.add(Dense(512, input_dim=13, init='uniform', activation='relu'))
model.add(Dense(100, init='uniform', activation='relu'))
model.add(Dense(2, init='uniform', activation='softmax'))
# Compile model
model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])


# Fit the model
model.fit(X, Y, nb_epoch=10, batch_size=10)

# evaluate the model
scores = model.evaluate(X, Y)
print("%s: %.2f%%" % (model.metrics_names[1], scores[1]*100))
