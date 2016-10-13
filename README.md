# Terror.theater data analysis ✈︎ 📈
 
An analysis from the particpatory theater play "Terror" where the audience takes a vote at the end.

Data is taken from the offical website [terror.theater](http://terror.theater/)

## Approach

### Data aquisition
The data (`buehnen.json`) was downloaded and the `latitude`, `longitude` were extracted. Furthermore
the results of the votes were extracted from the popup text (stored as `votes_free`, `votes_jail`, `ratio_free`).

### Data extraction
There were some entries for which no data could be extracted because the website only listed the thaters but they
did not have their first show yet. Those were filtered out.

### Data augmentation
The data was converted to csv, manually augmented with the city's population and mayor's party. This data was taken from the German Wikipedia.
The data was stored in `results_with_population_and_party.csv`.

### Analysis
The new csv file was loaded with pandas. The correlations between the columns were calculated to see if there are any. Furthermore
some linear regression plots were drawn with seaborn and the mean `ratio_free` with regards to the mayor's party was calculated.


## Results

### Correlations
| votes_free | ratio_free | longitude | latitude  | votes_jail | population |           |
|------------|------------|-----------|-----------|------------|------------|-----------|
| votes_free | 1          | 0.150329  | -0.199568 | -0.130975  | 0.966563   | 0.282945  |
| ratio_free | 0.150329   | 1         | -0.209398 | 0.184821   | -0.030439  | -0.286043 |
| longitude  | -0.199568  | -0.209398 | 1         | 0.26962    | -0.08986   | 0.27443   |
| latitude   | -0.130975  | 0.184821  | 0.26962   | 1          | -0.145993  | 0.022033  |
| votes_jail | 0.966563   | -0.030439 | -0.08986  | -0.145993  | 1          | 0.400844  |
| population | 0.282945   | -0.286043 | 0.27443   | 0.022033   | 0.400844   | 1         |


### Mean vote by mayor's party

|party | mean ratio_free|
|------|----------------|
|cdu   | 0.592157456117 |
|spd   | 0.58564370924  |
|fdp   | 0.5137142291   |
|gruen | 0.6669691379   |

### Plots

#### By latitude
![Plot of the linear regression by latitude](/latitude.png?raw=true)

#### By longitude
![Plot of the linear regression by longitude](/longitude.png?raw=true)

#### By population
![Plot of the linear regression by population](/population.png?raw=true)

#### By population (only cities with fewer then 1 Million inhabitants)
![Plot of the linear regression by population (small cities)](/population_small_cities.png?raw=true)


### Conclusion
There do not seem to be any exciting correlations unfortunately. 😐

If you find any [https://twitter.com/notknut](let me know on twitter) or open an issue here.
