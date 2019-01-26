
## Exercises


```R
library(tidyverse)
```


```R
library(rvest)
```

1. Visit the following web page: [https://web.archive.org/web/20181024132313/http://www.stevetheump.com/Payrolls.htm](https://web.archive.org/web/20181024132313/http://www.stevetheump.com/Payrolls.htm)

    Notice there are several tables. Say we are interested in comparing the payrolls of teams across the years. The next few exercises take us through the steps needed to do this.

    Start by applying what you learned to read in the website into an object called `h`.


```R
url <- "https://web.archive.org/web/20181024132313/http://www.stevetheump.com/Payrolls.htm"
```


```R
h <- read_html(url)
```

2. Note that, although not very useful, we can actually see the content of the page by typing: `html_text(h)`

    The next step is to extract the tables. For this, we can use the `html_nodes` function. We learned that tables in html are associated with the `table` node.  Use the `html_nodes` function and the `table` node to extract the first table. Store it in an object `nodes`.




```R
nodes <- html_nodes(h,'table')
```

3. The `html_nodes` function returns a list of objects of class `xml_node`. We can see the content of each one using, for example, the `html_text` function. You can see the content for an arbitrarily picked component like this: `html_text(nodes[[8]])`

    If the content of this object is an html table, we can use the `html_table` function to convert it to a data frame. Use the `html_table` function to convert the 8th entry of `nodes` into a table.



```R
html_table(nodes[[8]]) %>% head(2)
```


<table>
<thead><tr><th scope=col>Team</th><th scope=col>Payroll</th><th scope=col>Averge</th><th scope=col>Median</th></tr></thead>
<tbody>
	<tr><td>New York Yankees     </td><td>$ 197,962,289        </td><td>$ 6,186,321          </td><td>$ 1,937,500          </td></tr>
	<tr><td>Philadelphia Phillies</td><td>$ 174,538,938        </td><td>$ 5,817,964          </td><td>$ 1,875,000          </td></tr>
</tbody>
</table>



4. Repeat the above for the first 4 components of `nodes`. Which of the following are payroll tables:

    A. All them.
    
    B. 1
    
    C. 2
    
    __D__. 2-4



```R
html_table(nodes[[1]]) %>% head(2)
```


<table>
<thead><tr><th scope=col>X1</th><th scope=col>X2</th></tr></thead>
<tbody>
	<tr><td>NA                                                                    </td><td>Salary Stats 1967-2019
Top ML Player Salaries / Baseball's Luxury Tax</td></tr>
</tbody>
</table>




```R
html_table(nodes[[2]]) %>% head(2)
```


<table>
<thead><tr><th scope=col>RANK</th><th scope=col>TEAM</th><th scope=col>Payroll</th></tr></thead>
<tbody>
	<tr><td>1                   </td><td>Boston Red Sox      </td><td>$235.65M            </td></tr>
	<tr><td>2                   </td><td>San Francisco Giants</td><td>$208.51M            </td></tr>
</tbody>
</table>




```R
html_table(nodes[[3]]) %>% head(2)
```


<table>
<thead><tr><th scope=col>X1</th><th scope=col>X2</th><th scope=col>X3</th><th scope=col>X4</th><th scope=col>X5</th></tr></thead>
<tbody>
	<tr><td>Rank               </td><td>Team               </td><td>25 Man             </td><td>Disabled List      </td><td>Total Payroll      </td></tr>
	<tr><td>1                  </td><td>Los Angeles Dodgers</td><td>$155,887,854       </td><td>$37,354,166        </td><td>$242,065,828       </td></tr>
</tbody>
</table>




```R
html_table(nodes[[4]]) %>% head(2)
```


<table>
<thead><tr><th scope=col>Rank</th><th scope=col>Team</th><th scope=col>Opening Day</th><th scope=col>Avg Salary</th><th scope=col>Median</th></tr></thead>
<tbody>
	<tr><td>1            </td><td>Dodgers      </td><td>$ 223,352,402</td><td>$ 7,445,080  </td><td>$ 5,166,666  </td></tr>
	<tr><td>2            </td><td>Yankees      </td><td>$ 213,472,857</td><td>$ 7,361,133  </td><td>$ 3,300,000  </td></tr>
</tbody>
</table>



5. Repeat the above for the first __last__ 3 components of `nodes`. Which of the following is true:

    __A__. The last entry in `nodes` shows the average across all teams through time, not payroll per team.
    
    B. All three are payroll per team tables.
    
    C. All three are like the first entry, not a payroll table.
    
    D. All of the above.



```R
html_table(nodes[[length(nodes)]])  %>% head(2)
```


<table>
<thead><tr><th scope=col>X1</th><th scope=col>X2</th><th scope=col>X3</th><th scope=col>X4</th></tr></thead>
<tbody>
	<tr><td>Year    </td><td>Minimum </td><td>Average </td><td>% Chg   </td></tr>
	<tr><td>2019    </td><td>$555,000</td><td>        </td><td>-       </td></tr>
</tbody>
</table>




```R
html_table(nodes[[length(nodes)-1]]) %>% head(2)
```


<table>
<thead><tr><th scope=col>X1</th><th scope=col>X2</th><th scope=col>X3</th></tr></thead>
<tbody>
	<tr><td>Team       </td><td>Payroll    </td><td>Average    </td></tr>
	<tr><td>NY Yankees </td><td>$92,538,260</td><td>$3,190,974 </td></tr>
</tbody>
</table>




```R
html_table(nodes[[length(nodes)-2]]) %>% head(2)
```


<table>
<thead><tr><th scope=col>X1</th><th scope=col>X2</th><th scope=col>X3</th></tr></thead>
<tbody>
	<tr><td>Team        </td><td>Payroll     </td><td>Average     </td></tr>
	<tr><td>NY Yankees  </td><td>$109,791,893</td><td>$3,541,674  </td></tr>
</tbody>
</table>



6. We have learned that the first and last entries of `nodes` are not payroll tables. Redefine `nodes` so that these two are removed.



```R
del <- c(1,length(nodes))
```


```R
nodes <- nodes[-del]
```

7. We saw in the previous analysis that the first table node is not actually a table. This happens sometimes in html because tables are used to make text look a certain way, as opposed to storing numeric values. 

    Remove the first component and then use `sapply` and `html_table` to covert each node in `nodes` into a table. Note that in this case, `sapply` will return a list of tables. You can also use `lapply` to assure that a list is applied.


```R
nodes_tables <- nodes %>% lapply(html_table)
```


```R
nodes_tables[14]
```


<ol>
	<li><table>
<thead><tr><th scope=col>X1</th><th scope=col>X2</th><th scope=col>X3</th></tr></thead>
<tbody>
	<tr><td>Team                 </td><td>Payroll              </td><td>Average              </td></tr>
	<tr><td>1.                   </td><td>New York Yankees     </td><td>$205,938,439         </td></tr>
	<tr><td>2.                   </td><td>Boston Red Sox       </td><td>$121,311,945         </td></tr>
	<tr><td>3.                   </td><td>New York Mets        </td><td>$104,770,139         </td></tr>
	<tr><td>4.                   </td><td>Philadelphia Phillies</td><td>$95,337,908          </td></tr>
	<tr><td>5.                   </td><td>Los Angeles Angels   </td><td>$95,017,822          </td></tr>
	<tr><td>6.                   </td><td>St. Louis Cardinals  </td><td>$93,319,842          </td></tr>
	<tr><td>7.                   </td><td>San Francisco Giants </td><td>$89,487,842          </td></tr>
	<tr><td>8.                   </td><td>Chicago Cubs         </td><td>$87,210,933          </td></tr>
	<tr><td>9.                   </td><td>Seattle Mariners     </td><td>$85,883,333          </td></tr>
	<tr><td>10.                  </td><td>Atlanta Braves       </td><td>$85,148,582          </td></tr>
	<tr><td>11.                  </td><td>Los Angeles Dodgers  </td><td>$81,029,500          </td></tr>
	<tr><td>12.                  </td><td>Houston Astros       </td><td>$76,779,022          </td></tr>
	<tr><td>13.                  </td><td>Chicago White Sox    </td><td>$75,228,000          </td></tr>
	<tr><td>14.                  </td><td>Baltimore Orioles    </td><td>$74,570,539          </td></tr>
	<tr><td>15.                  </td><td>Detroit Tigers       </td><td>$68,998,183          </td></tr>
	<tr><td>16.                  </td><td>Arizona Diamondbacks </td><td>$63,015,834          </td></tr>
	<tr><td>17.                  </td><td>San Diego Padres     </td><td>$62,888,192          </td></tr>
	<tr><td>18.                  </td><td>Florida Marlins      </td><td>$60,375,961          </td></tr>
	<tr><td>19.                  </td><td>Cincinnati Reds      </td><td>$59,658,275          </td></tr>
	<tr><td>20.                  </td><td>Minnesota Twins      </td><td>$56,615,000          </td></tr>
	<tr><td>21.                  </td><td>Oakland Athletics    </td><td>$55,869,262          </td></tr>
	<tr><td>22.                  </td><td>Texas Rangers        </td><td>$55,307,258          </td></tr>
	<tr><td>23.                  </td><td>Washington Nationals </td><td>$48,581,500          </td></tr>
	<tr><td>24.                  </td><td>Colorado Rockies     </td><td>$47,789,000          </td></tr>
	<tr><td>25.                  </td><td>Toronto Blue Jays    </td><td>$45,336,500          </td></tr>
	<tr><td>26.                  </td><td>Cleveland Indians    </td><td>$41,830,400          </td></tr>
	<tr><td>27.                  </td><td>Milwaukee Brewers    </td><td>$40,234,833          </td></tr>
	<tr><td>28.                  </td><td>Pittsburgh Pirates   </td><td>$38,138,000          </td></tr>
	<tr><td>29.                  </td><td>Kansas City Royals   </td><td>$36,881,000          </td></tr>
	<tr><td>30.                  </td><td>Tampa Bay Devil Rays </td><td>$29,893,567          </td></tr>
</tbody>
</table>
</li>
</ol>



8. Look through the resulting tables. Are they all the same? Could we just join them with `bind_rows`? 

    No, because table header names for the teams are different.
    The table headers for the tables 10-13 and 15-20 match and are called 'X1'.


```R
bind_rows(nodes_tables[13:14]) %>% head
bind_rows(nodes_tables[13:14]) %>% tail
```


<table>
<thead><tr><th scope=col>X1</th><th scope=col>X2</th><th scope=col>X3</th></tr></thead>
<tbody>
	<tr><td>Team              </td><td>Payroll           </td><td>NA                </td></tr>
	<tr><td>New York Yankees  </td><td>$ 194,663,079     </td><td>NA                </td></tr>
	<tr><td>Boston Red Sox    </td><td>$ 120,099,824     </td><td>NA                </td></tr>
	<tr><td>Los Angeles Angels</td><td>$ 103,472,000     </td><td>NA                </td></tr>
	<tr><td>Chicago White Sox </td><td>$ 102,750,667     </td><td>NA                </td></tr>
	<tr><td>New York Mets     </td><td>$ 101,084,963     </td><td>NA                </td></tr>
</tbody>
</table>




<table>
<thead><tr><th></th><th scope=col>X1</th><th scope=col>X2</th><th scope=col>X3</th></tr></thead>
<tbody>
	<tr><th scope=row>57</th><td>25.                 </td><td>Toronto Blue Jays   </td><td>$45,336,500         </td></tr>
	<tr><th scope=row>58</th><td>26.                 </td><td>Cleveland Indians   </td><td>$41,830,400         </td></tr>
	<tr><th scope=row>59</th><td>27.                 </td><td>Milwaukee Brewers   </td><td>$40,234,833         </td></tr>
	<tr><th scope=row>60</th><td>28.                 </td><td>Pittsburgh Pirates  </td><td>$38,138,000         </td></tr>
	<tr><th scope=row>61</th><td>29.                 </td><td>Kansas City Royals  </td><td>$36,881,000         </td></tr>
	<tr><th scope=row>62</th><td>30.                 </td><td>Tampa Bay Devil Rays</td><td>$29,893,567         </td></tr>
</tbody>
</table>



9. Create two tables, call them `tab_1` and `tab_2` using entries 10 and 19.


```R
tab_1 <- nodes_tables[[10]]; tab_1 %>% head
tab_2 <- nodes_tables[[19]]; tab_2 %>% head
```


<table>
<thead><tr><th scope=col>X1</th><th scope=col>X2</th><th scope=col>X3</th></tr></thead>
<tbody>
	<tr><td>Team         </td><td>Payroll      </td><td>Average      </td></tr>
	<tr><td>N.Y. Yankees </td><td>$201,449,289 </td><td>$7,748,050   </td></tr>
	<tr><td>New York Mets</td><td>135,773,988  </td><td>4,849,071    </td></tr>
	<tr><td>Chicago Cubs </td><td>135,050,000  </td><td>5,402,000    </td></tr>
	<tr><td>Boston       </td><td>122,696,000  </td><td>4,089,867    </td></tr>
	<tr><td>Detroit      </td><td>115,085,145  </td><td>4,110,184    </td></tr>
</tbody>
</table>




<table>
<thead><tr><th scope=col>X1</th><th scope=col>X2</th><th scope=col>X3</th></tr></thead>
<tbody>
	<tr><td>Team       </td><td>Payroll    </td><td>Average    </td></tr>
	<tr><td>NY Yankees </td><td>$92,538,260</td><td>$3,190,974 </td></tr>
	<tr><td>Los Angeles</td><td>$88,124,286</td><td>$3,263,862 </td></tr>
	<tr><td>Atlanta    </td><td>$84,537,836</td><td>$2,817,928 </td></tr>
	<tr><td>Baltimore  </td><td>$81,447,435</td><td>$2,808,532 </td></tr>
	<tr><td>Arizona    </td><td>$81,027,833</td><td>$2,893,851 </td></tr>
</tbody>
</table>



10. Use a `full_join` function to combine these two tables. Before you do this you will have to fix the missing header problem. You will also need to make the names match.
 


```R
header_names <- tab_1 %>% filter(X1=="Team")
```


```R
names(tab_1) <- header_names
names(tab_2) <- header_names
```


```R
full_join(tab_1,tab_2,by = "Team") %>% arrange(Team)
```


<table>
<thead><tr><th scope=col>Team</th><th scope=col>Payroll.x</th><th scope=col>Average.x</th><th scope=col>Payroll.y</th><th scope=col>Average.y</th></tr></thead>
<tbody>
	<tr><td>Anaheim            </td><td>NA                 </td><td>NA                 </td><td>$51,464,167        </td><td>$1,715,472         </td></tr>
	<tr><td>Arizona            </td><td>73,571,667         </td><td>2,724,877          </td><td>$81,027,833        </td><td>$2,893,851         </td></tr>
	<tr><td>Atlanta            </td><td>96,726,167         </td><td>3,335,385          </td><td>$84,537,836        </td><td>$2,817,928         </td></tr>
	<tr><td>Baltimore          </td><td>67,101,667         </td><td>2,580,833          </td><td>$81,447,435        </td><td>$2,808,532         </td></tr>
	<tr><td>Boston             </td><td>122,696,000        </td><td>4,089,867          </td><td>$77,940,333        </td><td>$2,598,011         </td></tr>
	<tr><td>Chicago Cubs       </td><td>135,050,000        </td><td>5,402,000          </td><td>$60,539,333        </td><td>$2,017,978         </td></tr>
	<tr><td>Chicago White Sox  </td><td>96,068,500         </td><td>3,694,942          </td><td>$31,133,500        </td><td>$1,073,569         </td></tr>
	<tr><td>Cincinnati         </td><td>70,968,500         </td><td>2,957,021          </td><td>$46,867,200        </td><td>$1,735,822         </td></tr>
	<tr><td>Cleveland          </td><td>81,625,567         </td><td>3,023,169          </td><td>$75,880,871        </td><td>$2,918,495         </td></tr>
	<tr><td>Colorado           </td><td>75,201,000         </td><td>2,785,222          </td><td>$61,111,190        </td><td>$2,182,543         </td></tr>
	<tr><td>Detroit            </td><td>115,085,145        </td><td>4,110,184          </td><td>$58,265,167        </td><td>$2,157,969         </td></tr>
	<tr><td>Florida            </td><td>36,814,000         </td><td>1,314,786          </td><td>$20,072,000        </td><td>$692,138           </td></tr>
	<tr><td>Houston            </td><td>102,996,415        </td><td>3,814,682          </td><td>$51,289,111        </td><td>$1,899,597         </td></tr>
	<tr><td>Kansas City        </td><td>70,908,333         </td><td>2,727,244          </td><td>$23,433,000        </td><td>$836,893           </td></tr>
	<tr><td>Los Angeles        </td><td>NA                 </td><td>NA                 </td><td>$88,124,286        </td><td>$3,263,862         </td></tr>
	<tr><td>Los Angeles Angels </td><td>113,709,000        </td><td>4,061,036          </td><td>NA                 </td><td>NA                 </td></tr>
	<tr><td>Los Angeles Dodgers</td><td>100,458,101        </td><td>4,018,324          </td><td>NA                 </td><td>NA                 </td></tr>
	<tr><td>Milwaukee          </td><td>80,257,502         </td><td>3,086,827          </td><td>$36,505,333        </td><td>$1,140,792         </td></tr>
	<tr><td>Minnesota          </td><td>65,299,267         </td><td>2,251,699          </td><td>$16,519,500        </td><td>$635,365           </td></tr>
	<tr><td>Montreal           </td><td>NA                 </td><td>NA                 </td><td>$34,807,833        </td><td>$1,200,270         </td></tr>
	<tr><td>N.Y. Yankees       </td><td>$201,449,289       </td><td>$7,748,050         </td><td>NA                 </td><td>NA                 </td></tr>
	<tr><td>New York Mets      </td><td>135,773,988        </td><td>4,849,071          </td><td>NA                 </td><td>NA                 </td></tr>
	<tr><td>NY Mets            </td><td>NA                 </td><td>NA                 </td><td>$79,509,776        </td><td>$3,180,391         </td></tr>
	<tr><td>NY Yankees         </td><td>NA                 </td><td>NA                 </td><td>$92,538,260        </td><td>$3,190,974         </td></tr>
	<tr><td>Oakland            </td><td>62,310,000         </td><td>2,225,357          </td><td>$31,971,333        </td><td>$1,184,123         </td></tr>
	<tr><td>Philadelphia       </td><td>113,004,048        </td><td>4,185,335          </td><td>$47,308,000        </td><td>$1,631,310         </td></tr>
	<tr><td>Pittsburgh         </td><td>48,743,000         </td><td>1,874,731          </td><td>$28,928,333        </td><td>$1,112,628         </td></tr>
	<tr><td>San Diego          </td><td>42,796,700         </td><td>1,528,454          </td><td>$54,821,000        </td><td>$1,827,367         </td></tr>
	<tr><td>San Francisco      </td><td>82,161,450         </td><td>3,043,017          </td><td>$53,737,826        </td><td>$2,066,839         </td></tr>
	<tr><td>Seattle            </td><td>98,904,167         </td><td>3,532,292          </td><td>$58,915,000        </td><td>$2,265,962         </td></tr>
	<tr><td>St. Louis          </td><td>88,528,411         </td><td>3,278,830          </td><td>$61,453,863        </td><td>$2,276,069         </td></tr>
	<tr><td>Tampa Bay          </td><td>63,313,035         </td><td>2,183,208          </td><td>$62,765,129        </td><td>$2,024,682         </td></tr>
	<tr><td>Team               </td><td>Payroll            </td><td>Average            </td><td>Payroll            </td><td>Average            </td></tr>
	<tr><td>Texas              </td><td>68,646,023         </td><td>2,367,104          </td><td>$70,795,921        </td><td>$2,722,920         </td></tr>
	<tr><td>Toronto            </td><td>80,993,657         </td><td>2,892,631          </td><td>$46,238,333        </td><td>$1,778,397         </td></tr>
	<tr><td>Washington         </td><td>59,328,000         </td><td>2,045,793          </td><td>NA                 </td><td>NA                 </td></tr>
</tbody>
</table>



11. After joining the tables, you see several NAs. This is because some teams are in one table and not the other. Use the `anti_join` function to get a better idea of why this is happening.


```R
tab_12 <- anti_join(tab_1,tab_2,by = "Team")
tab_21 <- anti_join(tab_2,tab_1,by = "Team")
bind_rows(tab_12,tab_21) %>% arrange(Team)
```


<table>
<thead><tr><th scope=col>Team</th><th scope=col>Payroll</th><th scope=col>Average</th></tr></thead>
<tbody>
	<tr><td>Anaheim            </td><td>$51,464,167        </td><td>$1,715,472         </td></tr>
	<tr><td>Los Angeles        </td><td>$88,124,286        </td><td>$3,263,862         </td></tr>
	<tr><td>Los Angeles Angels </td><td>113,709,000        </td><td>4,061,036          </td></tr>
	<tr><td>Los Angeles Dodgers</td><td>100,458,101        </td><td>4,018,324          </td></tr>
	<tr><td>Montreal           </td><td>$34,807,833        </td><td>$1,200,270         </td></tr>
	<tr><td>N.Y. Yankees       </td><td>$201,449,289       </td><td>$7,748,050         </td></tr>
	<tr><td>New York Mets      </td><td>135,773,988        </td><td>4,849,071          </td></tr>
	<tr><td>NY Mets            </td><td>$79,509,776        </td><td>$3,180,391         </td></tr>
	<tr><td>NY Yankees         </td><td>$92,538,260        </td><td>$3,190,974         </td></tr>
	<tr><td>Washington         </td><td>59,328,000         </td><td>2,045,793          </td></tr>
</tbody>
</table>



12. We see see that one of the problem is that Yankees are listed as both _N.Y. Yankees_ and _NY Yankees_. In the next section, we will learn efficient approaches to fixing problems like this. Here we can do it "by hand" as follows:

    `tab_1 <- mutate(tab_1, Team = ifelse(Team == "N.Y. Yankees", "NY Yankees", Team))`

    Now join the tables and show only Oakland and the Yankees and the payroll columns.


```R
tab_1 <- mutate(tab_1, Team = ifelse(Team=="N.Y. Yankees", "NY Yankees", Team))
```


```R
full_join(tab_1,tab_2,by = "Team") %>% filter(Team %in% c('Oakland','NY Yankees')) %>% select(Team,Payroll.x,Payroll.y)
```


<table>
<thead><tr><th scope=col>Team</th><th scope=col>Payroll.x</th><th scope=col>Payroll.y</th></tr></thead>
<tbody>
	<tr><td>NY Yankees  </td><td>$201,449,289</td><td>$92,538,260 </td></tr>
	<tr><td>Oakland     </td><td>62,310,000  </td><td>$31,971,333 </td></tr>
</tbody>
</table>



13. Advanced: extract the titles of the movies that won Best Picture from this website: [https://m.imdb.com/chart/bestpicture/](https://m.imdb.com/chart/bestpicture/)


```R
url <- "https://m.imdb.com/chart/bestpicture/"
```


```R
h <- read_html(url)
```


```R
nodes <- html_nodes(h,'h4.best-picture-item-title')
```


```R
html_text(nodes[[1]]) %>% str_split('\n') %>% .[[1]] %>% .[1]
```


' The Shape of Water'



```R
nodes %>% lapply(html_text) %>% str_replace('\n.*\n','')
```


<ol class=list-inline>
	<li>' The Shape of Water'</li>
	<li>' Moonlight'</li>
	<li>' Spotlight'</li>
	<li>' Birdman or (The Unexpected Virtue of Ignorance)'</li>
	<li>' 12 Years a Slave'</li>
	<li>' Argo'</li>
	<li>' The Artist'</li>
	<li>' The King\'s Speech'</li>
	<li>' The Hurt Locker'</li>
	<li>' Slumdog Millionaire'</li>
	<li>' No Country for Old Men'</li>
	<li>' The Departed'</li>
	<li>' Crash'</li>
	<li>' Million Dollar Baby'</li>
	<li>' The Lord of the Rings: The Return of the King'</li>
	<li>' Chicago'</li>
	<li>' A Beautiful Mind'</li>
	<li>' Gladiator'</li>
	<li>' American Beauty'</li>
	<li>' Shakespeare in Love'</li>
	<li>' Titanic'</li>
	<li>' The English Patient'</li>
	<li>' Braveheart'</li>
	<li>' Forrest Gump'</li>
	<li>' Schindler\'s List'</li>
	<li>' Unforgiven'</li>
	<li>' The Silence of the Lambs'</li>
	<li>' Dances with Wolves'</li>
	<li>' Driving Miss Daisy'</li>
	<li>' Rain Man'</li>
	<li>' The Last Emperor'</li>
	<li>' Platoon'</li>
	<li>' Out of Africa'</li>
	<li>' Amadeus'</li>
	<li>' Terms of Endearment'</li>
	<li>' Gandhi'</li>
	<li>' Chariots of Fire'</li>
	<li>' Ordinary People'</li>
	<li>' Kramer vs. Kramer'</li>
	<li>' The Deer Hunter'</li>
	<li>' Annie Hall'</li>
	<li>' Rocky'</li>
	<li>' One Flew Over the Cuckoo\'s Nest'</li>
	<li>' The Godfather: Part II'</li>
	<li>' The Sting'</li>
	<li>' The Godfather'</li>
	<li>' The French Connection'</li>
	<li>' Patton'</li>
	<li>' Midnight Cowboy'</li>
	<li>' Oliver!'</li>
	<li>' In the Heat of the Night'</li>
	<li>' A Man for All Seasons'</li>
	<li>' The Sound of Music'</li>
	<li>' My Fair Lady'</li>
	<li>' Tom Jones'</li>
	<li>' Lawrence of Arabia'</li>
	<li>' West Side Story'</li>
	<li>' The Apartment'</li>
	<li>' Ben-Hur'</li>
	<li>' Gigi'</li>
	<li>' The Bridge on the River Kwai'</li>
	<li>' Around the World in 80 Days'</li>
	<li>' Marty'</li>
	<li>' On the Waterfront'</li>
	<li>' From Here to Eternity'</li>
	<li>' The Greatest Show on Earth'</li>
	<li>' An American in Paris'</li>
	<li>' All About Eve'</li>
	<li>' All the King\'s Men'</li>
	<li>' Hamlet'</li>
	<li>' Gentleman\'s Agreement'</li>
	<li>' The Best Years of Our Lives'</li>
	<li>' The Lost Weekend'</li>
	<li>' Going My Way'</li>
	<li>' Casablanca'</li>
	<li>' Mrs. Miniver'</li>
	<li>' How Green Was My Valley'</li>
	<li>' Rebecca'</li>
	<li>' Gone with the Wind'</li>
	<li>' You Can\'t Take It with You'</li>
	<li>' The Life of Emile Zola'</li>
	<li>' The Great Ziegfeld'</li>
	<li>' Mutiny on the Bounty'</li>
	<li>' It Happened One Night'</li>
	<li>' Cavalcade'</li>
	<li>' Grand Hotel'</li>
	<li>' Cimarron'</li>
	<li>' All Quiet on the Western Front'</li>
	<li>' The Broadway Melody'</li>
	<li>' Wings'</li>
	<li>' Sunrise: A Song of Two Humans'</li>
</ol>




```R

```
