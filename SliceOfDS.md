# Slice of Data Science 3/24/2021 - Clare Heinbaugh
Clare is sophomore and 1693 scholar at William and Mary. Her presentation in the Slice of Data Science lesson was on transfer learning, stacked generalization, and Keras. Throuhgout the meeting, Clare used many examples of her own work with many of these topics. 

The first topic gone over was Neural networks. Neural networks are one type of machine learning model that is used to classify data. Ina neural network there is a hidden layer, input layer, and output layer. The example Clare used was a neural network on spotify that could predict the genre of a song. The way to build network is that each row is an observation and expand it into a vector and apply weights and updating weights to predict power of model better. If you want to know how good model, you want to do a train-test-split. That way you can see how accurate it is by applying data you didn't train the data on. 

Neural networks inckude inlear algebra
kera = pythin library  that does linear algebra. does vectorized operations
Input passes through hidden layer

Convolutional Neural networks. Example of putting tomato into a vector because its made up of color bands. Identify important features of the image and apply weights to the features. Cold also split by the colors like in the photo of hte tomato split it b reg green and blue. the top box didnt have any red

Tranfer Learning - used to allow us to take wights trained to recognixe images and apply them to our own problem. Apply them and use them to new images. 
Example she used: predict road quality from satelite imagery. Used model to fit satelite images to the actual road qualityt from the app. 
Decided to train 3 dfferent tranfer learning model from Keras. She used her own classifier
advantages of useing pre-trained model: faster bc using weights tha have been pre-treaned for other images. If you used weights that are pretty clode to what you want them to be, you already have ana dvantage to solving the problem. Using weights already made
If data set is copletely different, Use Strtgey 1 because youll apply weights bc not many images are weights: Strategy 1: train the enitre model
Strateg 2: trainging some laters and leave the othes frozen
Strategy 3: freeeze the convultion vase
overfittign: very good at predinding trainging but bad at testing because its so well trained to the trainging data

Stacked Generalization
way to imporve model bc you take inut from many models that use many features and vote on the label for the image. You can also learn to trust a specific model and trust that outcome. 
Use predictons into inputs as model that predicts
Developers Student Club - Join to impoelemet your own script. Use Keras model to predict cancer cells
Use dropouts to prevent overfitting

DataAugmentation - manupultae images to hepl model be better at recognizing things. Like if you have pictures of horse always facing left, you should change it to face right in order to made sure the model has seen it before. It helps the model overall. 

Overall, I thought the talk was really informative. I got good insight on different future topics I am likely to learn in future Data Science classes. There is 
