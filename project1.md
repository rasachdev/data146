# Project 1

1. A package place which contains a ton of modules. A library is not too different from a packaage except that it contains a number of different packages. In order to use it you have to first install the package and then import it into your workspace. ```import numpy as np``` or ```import pandas as pd``` are examples we have used in class. 

2. A data frame is like a chart with mulitple rows and columns of information that can be sifted through. The pandas library is useful for working with data frames. you can use the ```pd.read_csv``` . Example:
```
path_to_data = 'gapminder.tsv'
data = pd.read_csv(path_to_data, sep='\t')
data
``` 
This shows how to read a file and improt it into the work session. You must have the ```gapminder.tsv``` in the root directory. Specificying an arguement within the ```read_()``` function is important because in the example about the data is a ```.tsv```, so it needs to be separated by a tab. 
Example of data frame I created from the code snippet above:

![](gapminderpic.PNG)
The number of rows and columns can be determined by ```data.shape``` and ```data.size```

3. 
