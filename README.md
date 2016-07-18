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

#Split into Train and Test
from sklearn.cross_validation import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, Y, test_size=0.33, random_state=42)

#Model building
# create model
model = Sequential()
model.add(Dense(512, input_dim=13, init='uniform', activation='relu'))
model.add(Dense(100, init='uniform', activation='relu'))
model.add(Dense(2, init='uniform', activation='softmax'))
# Compile model
model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])


# Fit the model
model.fit(X_train, y_train, nb_epoch=10, batch_size=10)

# evaluate the model
scores = model.evaluate(X_test, y_test)
print("%s: %.2f%%" % (model.metrics_names[1], scores[1]*100))
