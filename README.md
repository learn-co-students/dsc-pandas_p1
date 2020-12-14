
# Let's Get Some Pandas Reps In!

![more_pandas](https://media.giphy.com/media/KyBX9ektgXWve/giphy.gif)

## What is Pandas?

Pandas will be one of the main tools we will use in data science.  The better you get at Pandas, the easier your life will be when we get to the machine learning algorithms in later phases. 

Pandas is a essential library that comes with Anaconda.  Pandas, as [the Anaconda docs](https://docs.anaconda.com/anaconda/packages/py3.7_osx-64/) tell us, offers us "High-performance, easy-to-use data structures and data analysis tools." It's something like "Excel for Python", but it's quite a bit more powerful.

Let's navigate to the Pandas website to view some of its benefits: [pandas](https://pandas.pydata.org/about/)

# Importing data and initial data exploration

Let's first import pandas as pd.

Now read in the heart dataset.

Pandas has many methods for reading different types of files! Note that here we have a .csv file.

Read about this dataset [here](https://www.kaggle.com/ronitf/heart-disease-uci).

Notice the name of the last column!

The output of the `.read_csv()` function is a pandas *DataFrame*, which has a familiar tabaular structure of rows and columns.

The .shape attribute of a dataframe shows how many rows and columns are in a dataframe.

Two main types of pandas objects are the DataFrame and the Series, the latter being in effect a single column––*plus index*––of the former.

But Pandas is built on top of NumPy, and we can always access the NumPy array underlying a DataFrame using `.values`.

What does .head( ) do? What do you learn about the dataset by using it here?

What about .tail( )? What about .info( ) and .describe( )?

## Individual Features/Columns

We can also inspect columns on their own.

What can we figure out / guess about the different columns?

Let's check the data type of one of our columns:

## Statistics

I can use methods like `.mean()`, `.min()`, `.max()` to calculate quick statistics.

I can also sort the values in a column by using `.sort_values()`

# Value Counts

How many different values does have slope have? What about sex? And target?

# Basic Manipulations

## Adding to a DataFrame

Here are two rows that our engineer accidentally left out of the .csv file, expressed as a Python dictionary:

How can we add this to the bottom of our dataset?

Let's add a new column to our dataset called "test". Set all of its values to 0.

I can also add columns whose values are functions of existing columns.

How could I add a column, called 'twice_age', that is double the age column?

## Filtering

We can use filtering techniques to see only certain rows of our data. If we wanted to see only the rows for patients 70 years of age or older, we can simply type:

Use '&' for "and" and '|' for "or".

## .loc( ) and .iloc( )

We can use .loc( ) to get, say, the first ten values of the age and trestbps columns:

.iloc() is used for selecting locations in the DataFrame **by number**:

# Pair Exercise: 

Here are three datasets from dataportals.org. 

With a partner, take 10 minutes, and choose one of these urls:
        
- Chicago Data Portal, [food inspections](https://data.cityofchicago.org/Health-Human-Services/Food-Inspections/4ijn-s7e5/data)
- Seattle Data Portal, [public employee wages](https://data.seattle.gov/City-Business/City-of-Seattle-Wage-Data/2khk-5ukd)
- San Francisco Data Portal, [mobile food facility](https://data.sfgov.org/Economy-and-Community/Mobile-Food-Facility-Permit/rqzj-sfat)

- Export the csv data onto your local computer, then start exploring the data. Here are some suggestions for how to proceed.

    1. Create a dataframe using pd.read_csv('path_to_your_file/file.csv'
    2. View the head and tail of the DataFrame. 
    3. Call .info to check the total number of rows/columns, view the datatypes, and see if certain columns have n/a values
    4. Run value_counts on a categorical variable.
    5. Filter the data based on a categorical or continuous variable using the df[df.feature == 'value'] syntax.
    6. Create a new column from an old column
    7. If you have time, create a visualization using matplotlib. 

![pair](https://media.giphy.com/media/FQVZk2elXU14Q/giphy.gif)

For the second half of the lecture, we will use the well-worn titanic dataset.

# Learn to interact and manipulate dataframe columns

Let's take a look at the head of the data frame and the shape, just to get a quick overview.

### Quick knowledge check
We always want to be aware of what a row represents. 

What does each row in the dataframe represent? 

Like most things code, there are several ways to view columns.

The first way is to look at the columns attribute of the dataframe.

A second way to see the columns is using the built in list() method:

Consider the situation where you want to rename a column in the dataframe. Let's say you are getting tired of remembering that SibSp refers to siblings and spouses. We can rename it like so:

Great. Now print out the head of the df

Looks like something did not register.  The column name is back to SibSp. 
A finicky thing about Pandas is the use of inplace.  
In order for the object to be transformed in memory, we need to assign the inplace paramater the value of True

We can also change multiple columns at once with a dictionary:

We can also interact directly with the .columns attribute


If we find a column is not useful, we can drop columns with the drop method.



# Pair Program:

Take 5 minutes with a partner to perform this activity.

We just renamed our columns to a useless series of letters. Luckily we saved our column names in the variable df_columns. Let's rename our columns using columns attribute.  To make things neater, we want the column names to all be lowercase.   You can perform this in any way you prefer, but a list comprehension can do it in one line.

Remember, list comprehensions look like this:
> [function(variable) for variable in iterable]

## Identify and deal with N/A values

NA (not available) values, are a constant annoyance.  They can mess up our code and our analysis.  One of the first steps of EDA you will perform is looking at whether your data has NA's.  

Apropo to the event it describes, the titanic dataset has many NA values. 

We can see that in a few ways, first using describe.

## Knowledge Check: From the above info() output, which columns have na's? How can you tell?


Your answer here  


Another way to see na's is with the **isna()** method

More usefully, we can sum the values which are na:

## Dealing with na's


One way to deal with na's is by dropping rows that have them:


Let's explore what happened there. Since we didn't include inplace=True, we can run the same code with some additions to see the difference:

# Knowledge check
How did drop na affect the dataframe?  Why did it remove so many rows?

Dropna without params reduced our data significantly, which is a very bad thing. Our model performance, when we get to modeling, will heavily rely on having enough data.

Let's add a parameter to dropna:

You will find that data preprocessing presents you with many paths to follow.  You have many choices you can make as to how to preprocess. 

For now let's make the choice to drop cabin, since it has so many nulls:

With age, let's be a bit more creative, and impute the mean. This is a common method.

##  Short Exercise: Turn of your camera and take 3 minutes:

Using the fillna() method, write code below to fill the na's in age with the mean of age.
