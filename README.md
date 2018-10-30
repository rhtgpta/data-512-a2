# Bias in Data
Name: Rohit Gupta  
Date: 28 October, 2018  
Email: rgupta91 [at] uw.edu  

## Goal
The goal of the project is to investigate bias in Wikipedia (English) articles by looking at the articles related to the politicians of each country. I am interested in two different metrics:
* Metric I : How many politician articles for a country relative to its population?
* Metric II: How many of those articles are high-quality for a country? 

The original assignment statement can be found at the following location:  
https://wiki.communitydata.cc/Human_Centered_Data_Science_(Fall_2018)/Assignments#A2:_Bias_in_data

The top 10 countries at the extremes for both the metrics are found out, and the results are displayed below. 

**Top 10 countries (Metric I):**    

| Country                        | Population | # Articles | # Articles / Pop (Pct) |
|--------------------------------|------------|------------|------------------------|
| Tuvalu                         | 10000      | 55         | 0.55                   |
| Nauru                          | 10000      | 53         | 0.53                   |
| San Marino                     | 30000      | 82         | 0.273333               |
| Monaco                         | 40000      | 40         | 0.1                    |
| Liechtenstein                  | 40000      | 29         | 0.0725                 |
| Tonga                          | 100000     | 63         | 0.063                  |
| Marshall Islands               | 60000      | 37         | 0.061667               |
| Iceland                        | 400000     | 206        | 0.0515                 |
| Andorra                        | 80000      | 34         | 0.0425                 |
| Federated States of Micronesia | 100000     | 38         | 0.038                  |  

**Bottom 10 countries (Metric I):**    

| Country      | Population | # Articles | # Articles / Pop (Pct) |
|--------------|------------|------------|------------------------|
| India        | 1371300000 | 986        | 0.000072               |
| Indonesia    | 265200000  | 214        | 0.000081               |
| China        | 1393800000 | 1135       | 0.000081               |
| Uzbekistan   | 32900000   | 29         | 0.000088               |
| Ethiopia     | 107500000  | 105        | 0.000098               |
| Zambia       | 17700000   | 25         | 0.000141               |
| Korea, North | 25600000   | 39         | 0.000152               |
| Thailand     | 66200000   | 112        | 0.000169               |
| Bangladesh   | 166400000  | 323        | 0.000194               |
| Mozambique   | 30500000   | 60         | 0.000197               |


**Top 10 countries (Metric II):** 

| Country                  | Population | # Articles | # HQ Articles | HQ Articles / Articles |
|--------------------------|------------|------------|---------------|------------------------|
| Korea, North             | 25600000   | 39         | 7             | 17.948718              |
| Saudi Arabia             | 33400000   | 119        | 16            | 13.445378              |
| Central African Republic | 4700000    | 68         | 8             | 11.764706              |
| Romania                  | 19500000   | 348        | 40            | 11.494253              |
| Mauritania               | 4500000    | 52         | 5             | 9.615385               |
| Bhutan                   | 800000     | 33         | 3             | 9.090909               |
| Tuvalu                   | 10000      | 55         | 5             | 9.090909               |
| Dominica                 | 70000      | 12         | 1             | 8.333333               |
| United States            | 328000000  | 1092       | 82            | 7.509158               |
| Benin                    | 11500000   | 94         | 7             | 7.446809               |

**Bottom 10 countries (Metric II):**   
  
The bottom 10 countries all have 0 high-quality articles, and there are 39 countries in total with 0 HQ articles. These are:  
  
Andorra, Angola, Antigua and Barbuda, Bahamas, Barbados, Belgium, Belize, Cameroon, Cape Verde, Comoros, Costa Rica, Djibouti, Federated States of Micronesia, Finland, Guyana, Kazakhstan, Kiribati, Lesotho, Liechtenstein, Macedonia, Malta, Marshall Islands, Moldova, Monaco, Mozambique, Nauru, Nepal, San Marino, Sao Tome and Principe, Seychelles, Slovakia, Solomon Islands, Switzerland, Tunisia, Turkmenistan, Uganda, Zambia  

## Data Sources
To complete the analysis, the following data sources were used:

### Population Data
The population data used for the analysis comes from [here](https://www.dropbox.com/s/5u7sy1xt7g0oi2c/WPDS_2018_data.csv?dl=0).
Columns in the population data include:
* Geography: Country name
* Population mid-2018 (millions): population size (in millions)  

The licensing information cannot be obtained as it is saved as a csv file on Dropbox.

### Wikipedia page data
The data with information about politician articles for different countries can be found at the following link (Figshare):
https://figshare.com/articles/Untitled_Item/5513449

The above link contains the following documentation:  
>This project contains data on most English-language Wikipedia articles within the category "Category:Politicians by nationality" and subcategories, along with the code used to generate that data. Both are released under the CC-BY-SA 4.0 license.  
>
>Data  
>The data was extracted via the Wikimedia API using the associated code. It is formatted as a CSV and saved as page_data.csv in the "data" directory. Columns are:
>
>1. "country", containing the sanitised country name, extracted from the category name;
>2. "page", containing the unsanitised page title.
>3. "last_edit", containing the edit ID of the last edit to the page.
>
>Country codes are inconsistent. Where possible, they have been modified to match the country names found in http://www.prb.org/DataFinder/Topic/Rankings.aspx?ind=14 - but the PRB dataset contains nations not found in Wikipedia, and vice versa.
>
>The actual recursion only went 2 levels deep into the category tree: someone listed as an Antiguan politician, say, is included - someone exclusively listed as an Antiguan politician who was assassinated is not.

As stated in the documentation above, the data is released under the [CC-BY-SA 4.0 license](https://creativecommons.org/licenses/by-sa/4.0/).  

### Page Ratings (Wikipedia ORES)
The ratings for the different articles are fetched from the ORES API provided by Wikimedia.  
More info can be gleaned at the following link:  
https://www.mediawiki.org/wiki/ORES  
  
ORES API Documentation:   
https://ores.wikimedia.org/v3/#!/scoring/get_v3_scores_context  
As per ORES documentation under article quality, the categories are defined as follows (ordered from best to worst):

    FA - Featured article
    GA - Good article
    B - B-class article
    C - C-class article
    Start - Start-class article
    Stub - Stub-class article

Articles are tagged as High Quality if the category falls under FA or GA.
Wikimedia content is hosted under the [Attribution-ShareAlike 3.0 Unported (CC BY-SA 3.0) license](https://creativecommons.org/licenses/by-sa/3.0/).  

## Resources
The analysis is compiled using iPython Jupyter notebook, running Python 3.4.  
Documentation for Python: https://docs.python.org/3.4/  
Documentation for Jupyter Notebooks: http://jupyter-notebook.readthedocs.io/en/latest/   

If you are new to python notebooks, the process can be greatly simplified by installing [Anaconda](https://www.anaconda.com/download/).

The packages that were imported during the courses are as follows:
* Pandas [Documentation](https://pandas.pydata.org/pandas-docs/stable/)
* Numpy [Documentation](https://docs.scipy.org/doc/)
* Requests [Documentation](http://docs.python-requests.org/en/master/)

The packages can be installed through anaconda or [pip](https://pip.pypa.io/en/stable/).

## Files Created
The raw data files that were required for the analysis (apart from the ORES API data) are saved under the raw_data directory. The final dataset before the analysis is also saved in the main directory under the filename final_dataframe.csv  

Snapshot of the final dataframe:  

| country | article_name                       | revision_id | article_quality | population |
|---------|------------------------------------|-------------|-----------------|------------|
| Zambia  | Template:ZambiaProvincialMinisters | 235107991   | NaN             | 17700000   |
| Zambia  | Gladys Lundwe                      | 757566606   | Stub            | 17700000   |
| Zambia  | Mwamba Luchembe                    | 764848643   | Stub            | 17700000   |
| Zambia  | Thandiwe Banda                     | 768166426   | Start           | 17700000   |
| Zambia  | Sylvester Chisembele               | 776082926   | C               | 17700000   |

Data considerations:
* Data for 105 Revision IDs couldn't be obtained from the ORES API, which is ~0.22% of the total data.
* ~4.5% of the data didn't match due to missing country information in the population dataset. The countries that are missing can be found in the notebook file.

## Reflection
The analysis was a good exercise that helped me hone my skills for detecting potential sources of bias in a dataset. I have tried to list all the documentation and license information wherever possible and also informed about caveats (if any) to help with reproducibility.  

The immense amount of variation in the number of politician articles per 100 people can be attributed to a lot of factors, but a common theme that stands out is that the countries with a lower population seem to score higher in the said metric, and vice-versa. That makes sense given the fact that the number of politicians required to hold important offices might not increase in a direct proportion with the population.
  
The metric indicating the proportion of high-quality articles is more interesting though. North Korea and Saudi Arabia share the 1st and 2nd spot respectively, which is quite interesting, to say the least. My initial hypothesis is that these countries have a political structure that is frequently a hot topic of discussion among political think-tanks resulting in a lot of editors, and hence a higher overall quality.  
  
Lastly, it would also be interesting to see the effect of language for each country, as we are only looking at the English Wikipedia articles. Countries with dominant non-English speaking populations would have a lower proportion of high-quality articles which can be a potential source of bias.    
  
## License
The assignment code is released under the MIT License. The details can be found in the License file.

