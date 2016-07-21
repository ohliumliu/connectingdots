### A list of tools for data scraping
#### HTML
* Python pakage request for handling http requests
 ```python
 import requests
 req = requests.get("url")
 ```
* Python package BeautifulSoup (bs4) for parsing html and get DOM tree
 ```python
 from bs4 import BeautifulSoup
 page = req.content # in bytes, for binary as well as text data. JSON also has a built in method .json()
 # or
 page = req.text # in unicode

 # generate bs4 object
 soup = BeautifulSoup(page, 'html.parser')
 
 # clean up
 soup.prettify()
 
 # find element
 soup.find_all("p") #=> a set consisting of all <p></p>. find also takes css properties as a hash, for example, {"class": "table"}
                    #=> These is also a select method that uses pure css selectors.
 
 # find attribute
[t["class"] for t in soup.find_all("table") if t.has_attr("class")]
```
* Display
  Use HTML package to show selected portion of the page

  ```python
  from IPython.core.display import HTML
  list_html = str(soup.find("ul", {"class": "info"})) # convert the output of find (a soup tag) to str
  HTML(list_html) # show html
  ```
* Get data
 Use get_text to get the content of a tag
* [pattern module](http://www.clips.ua.ac.be/pattern)
Code example
```python
    url = 'http://www.govtrack.us/data/congress/113/votes/2013'
    reg = requests.get(url)
    elements = web.Element(req.text).by_tag('a')
```
#### Pandas
 * Constructor:
 ```python
   import pandas as pd
   df = pd.DataFrame(data, columns = col-name, index = index-name) # data is an array
   df = pd.DataFrame(dict, index=index-name) # dict is a hash with keys being the col-name
 ```
 * More on [Pandas](pandas.md)
