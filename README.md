# World Map Population Data Visualization

## Objective

Using real global population data provided by <https://datahub.io/core/population> students will learn how to use large data sets to create visualizations to better recognize patterns, trends, and correlations.

## Getting Started

### Install packages

If you haven't already, you will need to install the following packages:

* pygal - `pip3 install pygal`
* pygal world map - `pip3 install pygal_maps_world`
* json - `pip3 install json`
* lxml - `pip3 install lxml`

### Import packages

1.  Create a folder called `world-pop-project`
2.  Create 2 files called `main.py` and `data.json`
3.  At the very top of `main.py` import your packages:

```
import json
import lxml
from pygal.maps.world import World
from pygal.maps.world import COUNTRIES
```

### Save and load population data from `data.json`

1.  In `data.json` copy and paste the data from: https://gist.github.com/mellaniesoriano/901fe8f86eb8441f50a42963930d1b28
2.  In `main.py`, create a variable called `filename` and set it's value to `"data.json"`
3.  Open the file using the following method:

```
with open(filename) as dataset:
  pop_data = json.load(dataset)
```

### Get the country codes from Pygal

1.  Create a function called `get_country_code` with one parameter called `country_name`
2.  Inside the function create a `for loop` that will loop through `COUNTRIES.items()`. Your loop should have 2 iterator variables called `code` that will get the keys and `name` that will get the values.
3.  Inside of your `for loop` check to see if `country_name` equals the `name` value
4.  If `name` equals `country_name` return `code`
5.  return `None` if the country name was not found

* Note: Be careful with indentation. Python is very sensitive about indentation.

Example structure:

```
def get_country_code(???):
  for ???, ??? in ???.items():
    if ??? == ???:
      return ???
  return ???
```

### Create your own dictionary

1.  Create a variable called `cc_populations` and assign it to an empty dictionary.
2.  Create a `for loop` with a variable called `pop_dict` that loops through `pop_data`
3.  Inside your for loop create the following:
    * variable called `country_name` and set it's value to `pop_dict['Country Name']`.
    * variable called `population` and set it's value to `pop_dict['Value']`
    * variable called `code` and set it's value to the `get_country_code` function you created earlier and give it the argument `country_name`
4.  Inside of your loop create an `if` statement that checks if `code` exists. If it exists assign `cc_population[code]` to `population`

Example structure:

```
??? = {}

for ??? in ???
  ??? = pop_dict[???]
  ??? = pop_dict[???]
  ??? = get_country_code(???)
  if ???:
    ???[code] = ???
```

### Create 3 levels of population groups

1.  Create 3 variables called `pop_lvl_1`, `pop_lvl_2`, and `pop_lvl_3` and assign each variable to an empty dictionary
2.  Create a `for loop` that will loop through the `cc_populations` dictionary you created previously. You should have 2 iterator variables called `code` that will get the keys and `pop` that will get the population value
3.  Create a conditional statement that checks if `pop` is less than 10,000,000 assign `pop_lvl_1[code]` to the `pop`
4.  Create a conditional statement that checks if `pop` is less than 1,000,000,000 assign `pop_lvl_2[code]` to the `pop`
5.  Create a conditional statement that will set `pop_lvl_3[code]` to `pop`
    Example structure:

```
???, ???, ??? = {}, {}, {}

for ???, ??? in ???.items():
  if ??? < ???:
    ???[code] = ???
  elif ??? < ???:
    ???[code] = ???
  else:
    ???[code] = ???
```

### Create your map

1.  Create a variable called `worldmap_chart` and set it's value to World()
2.  Using `worldmap_chart` give it a title of `'2016 World Population by Country'`
3.  Add the values of each subgroup to your chart
4.  Use `render_in_browser()` with `worldmap_chart` so that when you run your code it will render in the browser.
