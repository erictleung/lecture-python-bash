# Homework

Submit source code and write-up (including program output) through Sakai.

## Background

A bunch of your friends really like wine, specifically Portuguese wine. One
night you all are up all night debating on what physicohemical aspects of wine
(like pH or acidity) make good wine. Being the sleuth you are, you find out
that there happens to be [a study and dataset][wine] looking at just this!

You are conveniently learning Python and bash scripting, and figured this may
be a good opportunity to provide some evidence for what may be contributing to
good wine.

[wine]: http://archive.ics.uci.edu/ml/datasets/Wine+Qualityhttp://archive.ics.uci.edu/ml/datasets/Wine+Quality


## Problem

The study you reference looked at both red and white wine and you want to find
out what makes good red and white wine. You wish to conduct a very simple
analysis.


## Instruction

Create a bash script to automate the entirety of your data acquisition and
analysis to faithfully reproduce your analysis. Your analysis will contain
Python scripts as well.


**Download Data**

Use wget or cURL to help [download the data][data].

| Wine Type | File Name               |
|-----------|-------------------------|
| Red       | `winequality-red.csv`   |
| White     | `winequality-white.csv` |

Download these data into a directory named `download`.

**Hint**: Use `mkdir -p` to create a directory if it doesn't exist yet.

[data]: http://archive.ics.uci.edu/ml/machine-learning-databases/wine-quality/


**Convert Data**

You like to deal with comma-separated files (CSVs). Unfortunately, you find out
that the data comes in a "semi-colon" separated file.

Use `sed` to convert these "semi-colon" separated files into a comma-separated
files.

Save these converted data into the directory `data`.


**Subset Data**

For your analysis you only want a couple physicochemical variables to check.
There are a total of 12 variables, but you're only interested in:

- Citric acid
- Chlorides
- pH
- Alcohol
- Quality (your outcome)

In addition to these variables, you want only the good wine and the bad quality
wine. Create four datasets, each with the threshold of 5 as being the cutoff
for good wine.

| File Name             | Quality Threshold | Description             |
|-----------------------|-------------------|-------------------------|
| `red_wine_poor.csv`   | <= 5              | Poor quality red wine   |
| `red_wine_good.csv`   | > 5               | Good quality red wine   |
| `white_wine_poor.csv` | <= 5              | Poor quality white wine |
| `white_wine_good.csv` | > 5               | Good quality white wine |

Put there four files into the `data` directory.


**Compare Low and High Quality**

Let's use Python to help us figure out what makes wine good or not.

Create a Python function to read in data from a given path and calculate the
average value of a given variable name.

```python
# Example use
avg_chloride_results = calculate_avg_value(data, "chlorides")
```

You want to be lazy and automate as much as possible. So let's create a Python
function that takes in an array of the file names and returns a dictionary.

The dictionary will have four keys equal to just the file names they come from
e.g.  the key of `white_wine_good.csv` will be `white_wine_good`. The values of
each key will be another dictionary with each key being the average value of
one of the four variables we're interested in:

- Citric acid
- Chlorides
- pH
- Alcohol

```python
wine_paths = ["white_wine_good.csv", ...]
avg_values = find_average_wines(wine_paths)
```


**Save Results**


Write a Python function to save your dictionary of results to four separate
files. Save your dictionaries as JavaScript Object Notation (JSON) files.

Use the built-in `json` Python package. Here's a hint on using it.

```python
import json

your_dictionary = {"some_date" : "date"}
f = open('destFile.txt', 'w+')
f.write(json.dumps(your_dictionary))
f.close()
```

Save your four results into a directory `results`.


**Challenge**

You want to automate everything as much as possible, so you want to create a
Makefile to make everything.


```shell
# Run the entire analysis
make all

# Remove all downloaded and intermediate files from data/, download/, results/
make clean
```


## Homework File Structure

To make things organized, please use the following structure for your data
analysis.

```
.
|-- analyze_wine.py
|-- analysis.sh
|-- data/
|-- results/
`-- download/
```


## Deliverables

- A single bash script to automate your analysis
- A Python script to calculate the average citric acid, chlorides, pH, and
  alcohol values of good and poor quality red and white wine.
