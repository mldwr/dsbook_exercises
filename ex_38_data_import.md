
## Exercises 

>1. Use the `read_csv` function to read each of the files that the following code saves in the `files` object: 
>
>    ```{r}
>    path <- system.file("extdata", package = "dslabs")
>    files <- list.files(path)
>    files
>    ```


```R
path <- system.file("extdata", package="dslabs")
```


```R
files <- list.files(path)
```


```R
files
```


<ol class=list-inline>
	<li>'fertility-two-countries-example.csv'</li>
	<li>'life-expectancy-and-fertility-two-countries-example.csv'</li>
	<li>'murders.csv'</li>
	<li>'olive.csv'</li>
	<li>'RD-Mortality-Report_2015-18-180531.pdf'</li>
</ol>




```R
library(tidyverse)
```

    ── Attaching packages ─────────────────────────────────────── tidyverse 1.2.1 ──
    ✔ ggplot2 3.1.0     ✔ purrr   0.2.5
    ✔ tibble  1.4.2     ✔ dplyr   0.7.6
    ✔ tidyr   0.8.1     ✔ stringr 1.3.1
    ✔ readr   1.1.1     ✔ forcats 0.3.0
    ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ✖ dplyr::filter() masks stats::filter()
    ✖ dplyr::lag()    masks stats::lag()



```R
fertility <- paste(path,'/',files[1]) %>% str_replace_all(" ","")
```


```R
life <- paste(path,'/',files[2]) %>% str_replace_all(" ","")
```


```R
murders <- paste(path,'/',files[3]) %>% str_replace_all(" ","")
```


```R
olive <- paste(path,'/',files[4]) %>% str_replace_all(" ","")
```


```R
mortality <- paste(path,'/',files[5]) %>% str_replace_all(" ","")
```


```R
read_csv(fertility)
```

    Parsed with column specification:
    cols(
      .default = col_double(),
      country = col_character()
    )
    See spec(...) for full column specifications.



<table>
<thead><tr><th scope=col>country</th><th scope=col>1960</th><th scope=col>1961</th><th scope=col>1962</th><th scope=col>1963</th><th scope=col>1964</th><th scope=col>1965</th><th scope=col>1966</th><th scope=col>1967</th><th scope=col>1968</th><th scope=col>⋯</th><th scope=col>2006</th><th scope=col>2007</th><th scope=col>2008</th><th scope=col>2009</th><th scope=col>2010</th><th scope=col>2011</th><th scope=col>2012</th><th scope=col>2013</th><th scope=col>2014</th><th scope=col>2015</th></tr></thead>
<tbody>
	<tr><td>Germany    </td><td>2.41       </td><td>2.44       </td><td>2.47       </td><td>2.49       </td><td>2.49       </td><td>2.48       </td><td>2.44       </td><td>2.37       </td><td>2.28       </td><td>⋯          </td><td>1.36       </td><td>1.36       </td><td>1.37       </td><td>1.38       </td><td>1.39       </td><td>1.40       </td><td>1.41       </td><td>1.42       </td><td>1.43       </td><td>1.44       </td></tr>
	<tr><td>South Korea</td><td>6.16       </td><td>5.99       </td><td>5.79       </td><td>5.57       </td><td>5.36       </td><td>5.16       </td><td>4.99       </td><td>4.85       </td><td>4.73       </td><td>⋯          </td><td>1.20       </td><td>1.21       </td><td>1.23       </td><td>1.25       </td><td>1.27       </td><td>1.29       </td><td>1.30       </td><td>1.32       </td><td>1.34       </td><td>1.36       </td></tr>
</tbody>
</table>




```R
read_csv(life)
```

    Parsed with column specification:
    cols(
      .default = col_double(),
      country = col_character()
    )
    See spec(...) for full column specifications.



<table>
<thead><tr><th scope=col>country</th><th scope=col>1960_fertility</th><th scope=col>1960_life_expectancy</th><th scope=col>1961_fertility</th><th scope=col>1961_life_expectancy</th><th scope=col>1962_fertility</th><th scope=col>1962_life_expectancy</th><th scope=col>1963_fertility</th><th scope=col>1963_life_expectancy</th><th scope=col>1964_fertility</th><th scope=col>⋯</th><th scope=col>2011_fertility</th><th scope=col>2011_life_expectancy</th><th scope=col>2012_fertility</th><th scope=col>2012_life_expectancy</th><th scope=col>2013_fertility</th><th scope=col>2013_life_expectancy</th><th scope=col>2014_fertility</th><th scope=col>2014_life_expectancy</th><th scope=col>2015_fertility</th><th scope=col>2015_life_expectancy</th></tr></thead>
<tbody>
	<tr><td>Germany    </td><td>2.41       </td><td>69.26      </td><td>2.44       </td><td>69.85      </td><td>2.47       </td><td>70.01      </td><td>2.49       </td><td>70.10      </td><td>2.49       </td><td>⋯          </td><td>1.40       </td><td>80.5       </td><td>1.41       </td><td>80.6       </td><td>1.42       </td><td>80.7       </td><td>1.43       </td><td>80.7       </td><td>1.44       </td><td>80.8       </td></tr>
	<tr><td>South Korea</td><td>6.16       </td><td>53.02      </td><td>5.99       </td><td>53.75      </td><td>5.79       </td><td>54.51      </td><td>5.57       </td><td>55.27      </td><td>5.36       </td><td>⋯          </td><td>1.29       </td><td>80.6       </td><td>1.30       </td><td>80.7       </td><td>1.32       </td><td>80.9       </td><td>1.34       </td><td>80.9       </td><td>1.36       </td><td>81.0       </td></tr>
</tbody>
</table>




```R
read_csv(murders)
```

    Parsed with column specification:
    cols(
      state = col_character(),
      abb = col_character(),
      region = col_character(),
      population = col_integer(),
      total = col_integer()
    )



<table>
<thead><tr><th scope=col>state</th><th scope=col>abb</th><th scope=col>region</th><th scope=col>population</th><th scope=col>total</th></tr></thead>
<tbody>
	<tr><td>Alabama             </td><td>AL                  </td><td>South               </td><td> 4779736            </td><td> 135                </td></tr>
	<tr><td>Alaska              </td><td>AK                  </td><td>West                </td><td>  710231            </td><td>  19                </td></tr>
	<tr><td>Arizona             </td><td>AZ                  </td><td>West                </td><td> 6392017            </td><td> 232                </td></tr>
	<tr><td>Arkansas            </td><td>AR                  </td><td>South               </td><td> 2915918            </td><td>  93                </td></tr>
	<tr><td>California          </td><td>CA                  </td><td>West                </td><td>37253956            </td><td>1257                </td></tr>
	<tr><td>Colorado            </td><td>CO                  </td><td>West                </td><td> 5029196            </td><td>  65                </td></tr>
	<tr><td>Connecticut         </td><td>CT                  </td><td>Northeast           </td><td> 3574097            </td><td>  97                </td></tr>
	<tr><td>Delaware            </td><td>DE                  </td><td>South               </td><td>  897934            </td><td>  38                </td></tr>
	<tr><td>District of Columbia</td><td>DC                  </td><td>South               </td><td>  601723            </td><td>  99                </td></tr>
	<tr><td>Florida             </td><td>FL                  </td><td>South               </td><td>19687653            </td><td> 669                </td></tr>
	<tr><td>Georgia             </td><td>GA                  </td><td>South               </td><td> 9920000            </td><td> 376                </td></tr>
	<tr><td>Hawaii              </td><td>HI                  </td><td>West                </td><td> 1360301            </td><td>   7                </td></tr>
	<tr><td>Idaho               </td><td>ID                  </td><td>West                </td><td> 1567582            </td><td>  12                </td></tr>
	<tr><td>Illinois            </td><td>IL                  </td><td>North Central       </td><td>12830632            </td><td> 364                </td></tr>
	<tr><td>Indiana             </td><td>IN                  </td><td>North Central       </td><td> 6483802            </td><td> 142                </td></tr>
	<tr><td>Iowa                </td><td>IA                  </td><td>North Central       </td><td> 3046355            </td><td>  21                </td></tr>
	<tr><td>Kansas              </td><td>KS                  </td><td>North Central       </td><td> 2853118            </td><td>  63                </td></tr>
	<tr><td>Kentucky            </td><td>KY                  </td><td>South               </td><td> 4339367            </td><td> 116                </td></tr>
	<tr><td>Louisiana           </td><td>LA                  </td><td>South               </td><td> 4533372            </td><td> 351                </td></tr>
	<tr><td>Maine               </td><td>ME                  </td><td>Northeast           </td><td> 1328361            </td><td>  11                </td></tr>
	<tr><td>Maryland            </td><td>MD                  </td><td>South               </td><td> 5773552            </td><td> 293                </td></tr>
	<tr><td>Massachusetts       </td><td>MA                  </td><td>Northeast           </td><td> 6547629            </td><td> 118                </td></tr>
	<tr><td>Michigan            </td><td>MI                  </td><td>North Central       </td><td> 9883640            </td><td> 413                </td></tr>
	<tr><td>Minnesota           </td><td>MN                  </td><td>North Central       </td><td> 5303925            </td><td>  53                </td></tr>
	<tr><td>Mississippi         </td><td>MS                  </td><td>South               </td><td> 2967297            </td><td> 120                </td></tr>
	<tr><td>Missouri            </td><td>MO                  </td><td>North Central       </td><td> 5988927            </td><td> 321                </td></tr>
	<tr><td>Montana             </td><td>MT                  </td><td>West                </td><td>  989415            </td><td>  12                </td></tr>
	<tr><td>Nebraska            </td><td>NE                  </td><td>North Central       </td><td> 1826341            </td><td>  32                </td></tr>
	<tr><td>Nevada              </td><td>NV                  </td><td>West                </td><td> 2700551            </td><td>  84                </td></tr>
	<tr><td>New Hampshire       </td><td>NH                  </td><td>Northeast           </td><td> 1316470            </td><td>   5                </td></tr>
	<tr><td>New Jersey          </td><td>NJ                  </td><td>Northeast           </td><td> 8791894            </td><td> 246                </td></tr>
	<tr><td>New Mexico          </td><td>NM                  </td><td>West                </td><td> 2059179            </td><td>  67                </td></tr>
	<tr><td>New York            </td><td>NY                  </td><td>Northeast           </td><td>19378102            </td><td> 517                </td></tr>
	<tr><td>North Carolina      </td><td>NC                  </td><td>South               </td><td> 9535483            </td><td> 286                </td></tr>
	<tr><td>North Dakota        </td><td>ND                  </td><td>North Central       </td><td>  672591            </td><td>   4                </td></tr>
	<tr><td>Ohio                </td><td>OH                  </td><td>North Central       </td><td>11536504            </td><td> 310                </td></tr>
	<tr><td>Oklahoma            </td><td>OK                  </td><td>South               </td><td> 3751351            </td><td> 111                </td></tr>
	<tr><td>Oregon              </td><td>OR                  </td><td>West                </td><td> 3831074            </td><td>  36                </td></tr>
	<tr><td>Pennsylvania        </td><td>PA                  </td><td>Northeast           </td><td>12702379            </td><td> 457                </td></tr>
	<tr><td>Rhode Island        </td><td>RI                  </td><td>Northeast           </td><td> 1052567            </td><td>  16                </td></tr>
	<tr><td>South Carolina      </td><td>SC                  </td><td>South               </td><td> 4625364            </td><td> 207                </td></tr>
	<tr><td>South Dakota        </td><td>SD                  </td><td>North Central       </td><td>  814180            </td><td>   8                </td></tr>
	<tr><td>Tennessee           </td><td>TN                  </td><td>South               </td><td> 6346105            </td><td> 219                </td></tr>
	<tr><td>Texas               </td><td>TX                  </td><td>South               </td><td>25145561            </td><td> 805                </td></tr>
	<tr><td>Utah                </td><td>UT                  </td><td>West                </td><td> 2763885            </td><td>  22                </td></tr>
	<tr><td>Vermont             </td><td>VT                  </td><td>Northeast           </td><td>  625741            </td><td>   2                </td></tr>
	<tr><td>Virginia            </td><td>VA                  </td><td>South               </td><td> 8001024            </td><td> 250                </td></tr>
	<tr><td>Washington          </td><td>WA                  </td><td>West                </td><td> 6724540            </td><td>  93                </td></tr>
	<tr><td>West Virginia       </td><td>WV                  </td><td>South               </td><td> 1852994            </td><td>  27                </td></tr>
	<tr><td>Wisconsin           </td><td>WI                  </td><td>North Central       </td><td> 5686986            </td><td>  97                </td></tr>
	<tr><td>Wyoming             </td><td>WY                  </td><td>West                </td><td>  563626            </td><td>   5                </td></tr>
</tbody>
</table>




```R
read_csv(olive)
```

    Warning message:
    “Missing column names filled in: 'X1' [1]”Parsed with column specification:
    cols(
      X1 = col_integer(),
      Region = col_character(),
      Area = col_integer(),
      palmitic = col_integer(),
      palmitoleic = col_integer(),
      stearic = col_integer(),
      oleic = col_integer(),
      linoleic = col_integer(),
      linolenic = col_integer(),
      arachidic = col_integer(),
      eicosenoic = col_integer()
    )
    Warning message in rbind(names(probs), probs_f):
    “number of columns of result is not a multiple of vector length (arg 1)”Warning message:
    “572 parsing failures.
    row # A tibble: 5 x 5 col     row col   expected   actual     file                                        expected   <int> <chr> <chr>      <chr>      <chr>                                       actual 1     1 <NA>  11 columns 12 columns '/Library/Frameworks/R.framework/Versions/… file 2     2 <NA>  11 columns 12 columns '/Library/Frameworks/R.framework/Versions/… row 3     3 <NA>  11 columns 12 columns '/Library/Frameworks/R.framework/Versions/… col 4     4 <NA>  11 columns 12 columns '/Library/Frameworks/R.framework/Versions/… expected 5     5 <NA>  11 columns 12 columns '/Library/Frameworks/R.framework/Versions/…
    ... ................. ... ............................................................................... ........ ............................................................................... ...... ............................................................................... .... ............................................................................... ... ............................................................................... ... ............................................................................... ........ ...............................................................................
    See problems(...) for more details.
    ”


<table>
<thead><tr><th scope=col>X1</th><th scope=col>Region</th><th scope=col>Area</th><th scope=col>palmitic</th><th scope=col>palmitoleic</th><th scope=col>stearic</th><th scope=col>oleic</th><th scope=col>linoleic</th><th scope=col>linolenic</th><th scope=col>arachidic</th><th scope=col>eicosenoic</th></tr></thead>
<tbody>
	<tr><td> 1          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1075        </td><td> 75         </td><td>226         </td><td>7823        </td><td>672         </td><td>36          </td><td>60          </td></tr>
	<tr><td> 2          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1088        </td><td> 73         </td><td>224         </td><td>7709        </td><td>781         </td><td>31          </td><td>61          </td></tr>
	<tr><td> 3          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td> 911        </td><td> 54         </td><td>246         </td><td>8113        </td><td>549         </td><td>31          </td><td>63          </td></tr>
	<tr><td> 4          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td> 966        </td><td> 57         </td><td>240         </td><td>7952        </td><td>619         </td><td>50          </td><td>78          </td></tr>
	<tr><td> 5          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1051        </td><td> 67         </td><td>259         </td><td>7771        </td><td>672         </td><td>50          </td><td>80          </td></tr>
	<tr><td> 6          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td> 911        </td><td> 49         </td><td>268         </td><td>7924        </td><td>678         </td><td>51          </td><td>70          </td></tr>
	<tr><td> 7          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td> 922        </td><td> 66         </td><td>264         </td><td>7990        </td><td>618         </td><td>49          </td><td>56          </td></tr>
	<tr><td> 8          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1100        </td><td> 61         </td><td>235         </td><td>7728        </td><td>734         </td><td>39          </td><td>64          </td></tr>
	<tr><td> 9          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1082        </td><td> 60         </td><td>239         </td><td>7745        </td><td>709         </td><td>46          </td><td>83          </td></tr>
	<tr><td>10          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1037        </td><td> 55         </td><td>213         </td><td>7944        </td><td>633         </td><td>26          </td><td>52          </td></tr>
	<tr><td>11          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1051        </td><td> 35         </td><td>219         </td><td>7978        </td><td>605         </td><td>21          </td><td>65          </td></tr>
	<tr><td>12          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1036        </td><td> 59         </td><td>235         </td><td>7868        </td><td>661         </td><td>30          </td><td>62          </td></tr>
	<tr><td>13          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1074        </td><td> 70         </td><td>214         </td><td>7728        </td><td>747         </td><td>50          </td><td>79          </td></tr>
	<tr><td>14          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td> 875        </td><td> 52         </td><td>243         </td><td>8018        </td><td>655         </td><td>41          </td><td>79          </td></tr>
	<tr><td>15          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td> 952        </td><td> 49         </td><td>254         </td><td>7795        </td><td>780         </td><td>50          </td><td>75          </td></tr>
	<tr><td>16          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1155        </td><td> 98         </td><td>201         </td><td>7606        </td><td>816         </td><td>32          </td><td>60          </td></tr>
	<tr><td>17          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td> 943        </td><td> 94         </td><td>183         </td><td>7840        </td><td>788         </td><td>42          </td><td>75          </td></tr>
	<tr><td>18          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1278        </td><td> 69         </td><td>205         </td><td>7344        </td><td>957         </td><td>45          </td><td>70          </td></tr>
	<tr><td>19          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td> 961        </td><td> 70         </td><td>195         </td><td>7958        </td><td>742         </td><td>46          </td><td>75          </td></tr>
	<tr><td>20          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td> 952        </td><td> 77         </td><td>258         </td><td>7820        </td><td>736         </td><td>43          </td><td>78          </td></tr>
	<tr><td>21          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1074        </td><td> 67         </td><td>236         </td><td>7692        </td><td>716         </td><td>56          </td><td>83          </td></tr>
	<tr><td>22          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td> 995        </td><td> 46         </td><td>288         </td><td>7806        </td><td>679         </td><td>56          </td><td>86          </td></tr>
	<tr><td>23          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1056        </td><td> 53         </td><td>247         </td><td>7703        </td><td>700         </td><td>54          </td><td>89          </td></tr>
	<tr><td>24          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1065        </td><td> 39         </td><td>234         </td><td>7876        </td><td>703         </td><td>42          </td><td>74          </td></tr>
	<tr><td>25          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1065        </td><td> 45         </td><td>245         </td><td>7779        </td><td>696         </td><td>47          </td><td>82          </td></tr>
	<tr><td>26          </td><td>Calabria    </td><td>1           </td><td>2           </td><td>1315        </td><td>139         </td><td>230         </td><td>7299        </td><td>832         </td><td>42          </td><td>60          </td></tr>
	<tr><td>27          </td><td>Calabria    </td><td>1           </td><td>2           </td><td>1321        </td><td>136         </td><td>217         </td><td>7174        </td><td>950         </td><td>43          </td><td>63          </td></tr>
	<tr><td>28          </td><td>Calabria    </td><td>1           </td><td>2           </td><td>1359        </td><td>115         </td><td>246         </td><td>7234        </td><td>874         </td><td>45          </td><td>63          </td></tr>
	<tr><td>29          </td><td>Calabria    </td><td>1           </td><td>2           </td><td>1378        </td><td>111         </td><td>272         </td><td>7127        </td><td>940         </td><td>46          </td><td>64          </td></tr>
	<tr><td>30          </td><td>Calabria    </td><td>1           </td><td>2           </td><td>1295        </td><td>109         </td><td>245         </td><td>7253        </td><td>903         </td><td>43          </td><td>62          </td></tr>
	<tr><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td></tr>
	<tr><td>543         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1020        </td><td>100         </td><td>290         </td><td>7620        </td><td> 960        </td><td> 0          </td><td>10          </td></tr>
	<tr><td>544         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td> 970        </td><td> 90         </td><td>220         </td><td>7700        </td><td>1020        </td><td> 0          </td><td> 0          </td></tr>
	<tr><td>545         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1180        </td><td>130         </td><td>220         </td><td>7450        </td><td>1010        </td><td> 0          </td><td>10          </td></tr>
	<tr><td>546         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1060        </td><td>140         </td><td>240         </td><td>7690        </td><td> 850        </td><td>10          </td><td>10          </td></tr>
	<tr><td>547         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td> 990        </td><td>100         </td><td>250         </td><td>7630        </td><td>1030        </td><td> 0          </td><td> 0          </td></tr>
	<tr><td>548         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1010        </td><td> 90         </td><td>350         </td><td>7630        </td><td> 940        </td><td>10          </td><td> 0          </td></tr>
	<tr><td>549         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1040        </td><td> 90         </td><td>250         </td><td>7780        </td><td> 820        </td><td>10          </td><td>10          </td></tr>
	<tr><td>550         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1040        </td><td> 90         </td><td>250         </td><td>7810        </td><td> 810        </td><td>10          </td><td>10          </td></tr>
	<tr><td>551         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1020        </td><td> 90         </td><td>350         </td><td>7620        </td><td> 920        </td><td>10          </td><td> 0          </td></tr>
	<tr><td>552         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1020        </td><td> 90         </td><td>260         </td><td>7620        </td><td>1010        </td><td> 0          </td><td> 0          </td></tr>
	<tr><td>553         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1010        </td><td> 90         </td><td>350         </td><td>7610        </td><td> 930        </td><td>10          </td><td> 0          </td></tr>
	<tr><td>554         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td> 920        </td><td>110         </td><td>340         </td><td>7720        </td><td> 910        </td><td> 0          </td><td> 0          </td></tr>
	<tr><td>555         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1030        </td><td>100         </td><td>250         </td><td>7710        </td><td> 900        </td><td> 0          </td><td>10          </td></tr>
	<tr><td>556         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td> 960        </td><td> 90         </td><td>300         </td><td>7820        </td><td> 830        </td><td> 0          </td><td> 0          </td></tr>
	<tr><td>557         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1030        </td><td>110         </td><td>210         </td><td>7810        </td><td> 840        </td><td> 0          </td><td> 0          </td></tr>
	<tr><td>558         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1010        </td><td>100         </td><td>240         </td><td>7710        </td><td> 910        </td><td>10          </td><td>20          </td></tr>
	<tr><td>559         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1020        </td><td> 90         </td><td>240         </td><td>7800        </td><td> 850        </td><td> 0          </td><td> 0          </td></tr>
	<tr><td>560         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1120        </td><td> 90         </td><td>300         </td><td>7650        </td><td> 830        </td><td> 0          </td><td>10          </td></tr>
	<tr><td>561         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1090        </td><td> 90         </td><td>290         </td><td>7710        </td><td> 800        </td><td>10          </td><td> 0          </td></tr>
	<tr><td>562         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1100        </td><td>120         </td><td>280         </td><td>7630        </td><td> 770        </td><td>10          </td><td>10          </td></tr>
	<tr><td>563         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1090        </td><td> 80         </td><td>240         </td><td>7820        </td><td> 760        </td><td>10          </td><td> 0          </td></tr>
	<tr><td>564         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1150        </td><td> 90         </td><td>250         </td><td>7720        </td><td> 810        </td><td> 0          </td><td>10          </td></tr>
	<tr><td>565         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1110        </td><td> 90         </td><td>230         </td><td>7810        </td><td> 750        </td><td> 0          </td><td>10          </td></tr>
	<tr><td>566         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1010        </td><td>110         </td><td>210         </td><td>7720        </td><td> 950        </td><td> 0          </td><td> 0          </td></tr>
	<tr><td>567         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1070        </td><td>100         </td><td>220         </td><td>7730        </td><td> 870        </td><td>10          </td><td>10          </td></tr>
	<tr><td>568         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1280        </td><td>110         </td><td>290         </td><td>7490        </td><td> 790        </td><td>10          </td><td>10          </td></tr>
	<tr><td>569         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1060        </td><td>100         </td><td>270         </td><td>7740        </td><td> 810        </td><td>10          </td><td>10          </td></tr>
	<tr><td>570         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1010        </td><td> 90         </td><td>210         </td><td>7720        </td><td> 970        </td><td> 0          </td><td> 0          </td></tr>
	<tr><td>571         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td> 990        </td><td>120         </td><td>250         </td><td>7750        </td><td> 870        </td><td>10          </td><td>10          </td></tr>
	<tr><td>572         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td> 960        </td><td> 80         </td><td>240         </td><td>7950        </td><td> 740        </td><td>10          </td><td>20          </td></tr>
</tbody>
</table>



>2. Note that the last one, the `olive` file, gives us a warning. This is because the first line of the file is missing the header for the first column. 
>
>    Read the help file for `read.csv` to figure out how to read in the file without reading this header. If you skip the header, you should not get this warning. Save the result to an object called `dat`


```R
?read.csv
```


```R
olive_dat <- read.csv(olive,header=FALSE)
```


```R
olive_dat %>% head
```


<table>
<thead><tr><th scope=col>V1</th><th scope=col>V2</th><th scope=col>V3</th><th scope=col>V4</th><th scope=col>V5</th><th scope=col>V6</th><th scope=col>V7</th><th scope=col>V8</th><th scope=col>V9</th><th scope=col>V10</th><th scope=col>V11</th><th scope=col>V12</th></tr></thead>
<tbody>
	<tr><td>NA          </td><td>Region      </td><td>Area        </td><td>palmitic    </td><td>palmitoleic </td><td>stearic     </td><td>oleic       </td><td>linoleic    </td><td>linolenic   </td><td>arachidic   </td><td>eicosenoic  </td><td>NA          </td></tr>
	<tr><td> 1          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1075        </td><td>75          </td><td>226         </td><td>7823        </td><td>672         </td><td>36          </td><td>60          </td><td>29          </td></tr>
	<tr><td> 2          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1088        </td><td>73          </td><td>224         </td><td>7709        </td><td>781         </td><td>31          </td><td>61          </td><td>29          </td></tr>
	<tr><td> 3          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>911         </td><td>54          </td><td>246         </td><td>8113        </td><td>549         </td><td>31          </td><td>63          </td><td>29          </td></tr>
	<tr><td> 4          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>966         </td><td>57          </td><td>240         </td><td>7952        </td><td>619         </td><td>50          </td><td>78          </td><td>35          </td></tr>
	<tr><td> 5          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1051        </td><td>67          </td><td>259         </td><td>7771        </td><td>672         </td><td>50          </td><td>80          </td><td>46          </td></tr>
</tbody>
</table>



>3. A problem with the previous approach is that we don't know what the columns represent. Type:
>
>    ```{r}
>    names(dat)
>    ```
>
>    to see that the names are not informative.
>
>    Use the `readLines` function to read in just the first line (we later learn how to extract values from the output). 


```R
names(olive_dat)
```


<ol class=list-inline>
	<li>'V1'</li>
	<li>'V2'</li>
	<li>'V3'</li>
	<li>'V4'</li>
	<li>'V5'</li>
	<li>'V6'</li>
	<li>'V7'</li>
	<li>'V8'</li>
	<li>'V9'</li>
	<li>'V10'</li>
	<li>'V11'</li>
	<li>'V12'</li>
</ol>




```R
olive_header <- readLines(olive,1) %>% str_split(',') %>% .[[1]]
```


```R
olive_header[1] = 'Num'
```


```R
olive_header[length(olive_header)+1] = 'sambalolic'
```


```R
olive_header
```


<ol class=list-inline>
	<li>'Num'</li>
	<li>'Region'</li>
	<li>'Area'</li>
	<li>'palmitic'</li>
	<li>'palmitoleic'</li>
	<li>'stearic'</li>
	<li>'oleic'</li>
	<li>'linoleic'</li>
	<li>'linolenic'</li>
	<li>'arachidic'</li>
	<li>'eicosenoic'</li>
	<li>'sambalolic'</li>
</ol>




```R
olive_dat <- setNames(olive_dat,olive_header)
```


```R
olive_dat %>% filter(Num!='NA')
```


<table>
<thead><tr><th scope=col>Num</th><th scope=col>Region</th><th scope=col>Area</th><th scope=col>palmitic</th><th scope=col>palmitoleic</th><th scope=col>stearic</th><th scope=col>oleic</th><th scope=col>linoleic</th><th scope=col>linolenic</th><th scope=col>arachidic</th><th scope=col>eicosenoic</th><th scope=col>sambalolic</th></tr></thead>
<tbody>
	<tr><td> 1          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1075        </td><td>75          </td><td>226         </td><td>7823        </td><td>672         </td><td>36          </td><td>60          </td><td>29          </td></tr>
	<tr><td> 2          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1088        </td><td>73          </td><td>224         </td><td>7709        </td><td>781         </td><td>31          </td><td>61          </td><td>29          </td></tr>
	<tr><td> 3          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>911         </td><td>54          </td><td>246         </td><td>8113        </td><td>549         </td><td>31          </td><td>63          </td><td>29          </td></tr>
	<tr><td> 4          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>966         </td><td>57          </td><td>240         </td><td>7952        </td><td>619         </td><td>50          </td><td>78          </td><td>35          </td></tr>
	<tr><td> 5          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1051        </td><td>67          </td><td>259         </td><td>7771        </td><td>672         </td><td>50          </td><td>80          </td><td>46          </td></tr>
	<tr><td> 6          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>911         </td><td>49          </td><td>268         </td><td>7924        </td><td>678         </td><td>51          </td><td>70          </td><td>44          </td></tr>
	<tr><td> 7          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>922         </td><td>66          </td><td>264         </td><td>7990        </td><td>618         </td><td>49          </td><td>56          </td><td>29          </td></tr>
	<tr><td> 8          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1100        </td><td>61          </td><td>235         </td><td>7728        </td><td>734         </td><td>39          </td><td>64          </td><td>35          </td></tr>
	<tr><td> 9          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1082        </td><td>60          </td><td>239         </td><td>7745        </td><td>709         </td><td>46          </td><td>83          </td><td>33          </td></tr>
	<tr><td>10          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1037        </td><td>55          </td><td>213         </td><td>7944        </td><td>633         </td><td>26          </td><td>52          </td><td>30          </td></tr>
	<tr><td>11          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1051        </td><td>35          </td><td>219         </td><td>7978        </td><td>605         </td><td>21          </td><td>65          </td><td>24          </td></tr>
	<tr><td>12          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1036        </td><td>59          </td><td>235         </td><td>7868        </td><td>661         </td><td>30          </td><td>62          </td><td>44          </td></tr>
	<tr><td>13          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1074        </td><td>70          </td><td>214         </td><td>7728        </td><td>747         </td><td>50          </td><td>79          </td><td>33          </td></tr>
	<tr><td>14          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>875         </td><td>52          </td><td>243         </td><td>8018        </td><td>655         </td><td>41          </td><td>79          </td><td>32          </td></tr>
	<tr><td>15          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>952         </td><td>49          </td><td>254         </td><td>7795        </td><td>780         </td><td>50          </td><td>75          </td><td>41          </td></tr>
	<tr><td>16          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1155        </td><td>98          </td><td>201         </td><td>7606        </td><td>816         </td><td>32          </td><td>60          </td><td>29          </td></tr>
	<tr><td>17          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>943         </td><td>94          </td><td>183         </td><td>7840        </td><td>788         </td><td>42          </td><td>75          </td><td>31          </td></tr>
	<tr><td>18          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1278        </td><td>69          </td><td>205         </td><td>7344        </td><td>957         </td><td>45          </td><td>70          </td><td>28          </td></tr>
	<tr><td>19          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>961         </td><td>70          </td><td>195         </td><td>7958        </td><td>742         </td><td>46          </td><td>75          </td><td>30          </td></tr>
	<tr><td>20          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>952         </td><td>77          </td><td>258         </td><td>7820        </td><td>736         </td><td>43          </td><td>78          </td><td>33          </td></tr>
	<tr><td>21          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1074        </td><td>67          </td><td>236         </td><td>7692        </td><td>716         </td><td>56          </td><td>83          </td><td>45          </td></tr>
	<tr><td>22          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>995         </td><td>46          </td><td>288         </td><td>7806        </td><td>679         </td><td>56          </td><td>86          </td><td>40          </td></tr>
	<tr><td>23          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1056        </td><td>53          </td><td>247         </td><td>7703        </td><td>700         </td><td>54          </td><td>89          </td><td>51          </td></tr>
	<tr><td>24          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1065        </td><td>39          </td><td>234         </td><td>7876        </td><td>703         </td><td>42          </td><td>74          </td><td>26          </td></tr>
	<tr><td>25          </td><td>North-Apulia</td><td>1           </td><td>1           </td><td>1065        </td><td>45          </td><td>245         </td><td>7779        </td><td>696         </td><td>47          </td><td>82          </td><td>38          </td></tr>
	<tr><td>26          </td><td>Calabria    </td><td>1           </td><td>2           </td><td>1315        </td><td>139         </td><td>230         </td><td>7299        </td><td>832         </td><td>42          </td><td>60          </td><td>32          </td></tr>
	<tr><td>27          </td><td>Calabria    </td><td>1           </td><td>2           </td><td>1321        </td><td>136         </td><td>217         </td><td>7174        </td><td>950         </td><td>43          </td><td>63          </td><td>30          </td></tr>
	<tr><td>28          </td><td>Calabria    </td><td>1           </td><td>2           </td><td>1359        </td><td>115         </td><td>246         </td><td>7234        </td><td>874         </td><td>45          </td><td>63          </td><td>18          </td></tr>
	<tr><td>29          </td><td>Calabria    </td><td>1           </td><td>2           </td><td>1378        </td><td>111         </td><td>272         </td><td>7127        </td><td>940         </td><td>46          </td><td>64          </td><td>23          </td></tr>
	<tr><td>30          </td><td>Calabria    </td><td>1           </td><td>2           </td><td>1295        </td><td>109         </td><td>245         </td><td>7253        </td><td>903         </td><td>43          </td><td>62          </td><td>38          </td></tr>
	<tr><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td></tr>
	<tr><td>543         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1020        </td><td>100         </td><td>290         </td><td>7620        </td><td>960         </td><td>0           </td><td>10          </td><td>2           </td></tr>
	<tr><td>544         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>970         </td><td>90          </td><td>220         </td><td>7700        </td><td>1020        </td><td>0           </td><td>0           </td><td>3           </td></tr>
	<tr><td>545         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1180        </td><td>130         </td><td>220         </td><td>7450        </td><td>1010        </td><td>0           </td><td>10          </td><td>2           </td></tr>
	<tr><td>546         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1060        </td><td>140         </td><td>240         </td><td>7690        </td><td>850         </td><td>10          </td><td>10          </td><td>1           </td></tr>
	<tr><td>547         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>990         </td><td>100         </td><td>250         </td><td>7630        </td><td>1030        </td><td>0           </td><td>0           </td><td>3           </td></tr>
	<tr><td>548         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1010        </td><td>90          </td><td>350         </td><td>7630        </td><td>940         </td><td>10          </td><td>0           </td><td>3           </td></tr>
	<tr><td>549         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1040        </td><td>90          </td><td>250         </td><td>7780        </td><td>820         </td><td>10          </td><td>10          </td><td>1           </td></tr>
	<tr><td>550         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1040        </td><td>90          </td><td>250         </td><td>7810        </td><td>810         </td><td>10          </td><td>10          </td><td>2           </td></tr>
	<tr><td>551         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1020        </td><td>90          </td><td>350         </td><td>7620        </td><td>920         </td><td>10          </td><td>0           </td><td>3           </td></tr>
	<tr><td>552         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1020        </td><td>90          </td><td>260         </td><td>7620        </td><td>1010        </td><td>0           </td><td>0           </td><td>3           </td></tr>
	<tr><td>553         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1010        </td><td>90          </td><td>350         </td><td>7610        </td><td>930         </td><td>10          </td><td>0           </td><td>3           </td></tr>
	<tr><td>554         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>920         </td><td>110         </td><td>340         </td><td>7720        </td><td>910         </td><td>0           </td><td>0           </td><td>3           </td></tr>
	<tr><td>555         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1030        </td><td>100         </td><td>250         </td><td>7710        </td><td>900         </td><td>0           </td><td>10          </td><td>2           </td></tr>
	<tr><td>556         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>960         </td><td>90          </td><td>300         </td><td>7820        </td><td>830         </td><td>0           </td><td>0           </td><td>3           </td></tr>
	<tr><td>557         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1030        </td><td>110         </td><td>210         </td><td>7810        </td><td>840         </td><td>0           </td><td>0           </td><td>1           </td></tr>
	<tr><td>558         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1010        </td><td>100         </td><td>240         </td><td>7710        </td><td>910         </td><td>10          </td><td>20          </td><td>2           </td></tr>
	<tr><td>559         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1020        </td><td>90          </td><td>240         </td><td>7800        </td><td>850         </td><td>0           </td><td>0           </td><td>2           </td></tr>
	<tr><td>560         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1120        </td><td>90          </td><td>300         </td><td>7650        </td><td>830         </td><td>0           </td><td>10          </td><td>1           </td></tr>
	<tr><td>561         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1090        </td><td>90          </td><td>290         </td><td>7710        </td><td>800         </td><td>10          </td><td>0           </td><td>2           </td></tr>
	<tr><td>562         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1100        </td><td>120         </td><td>280         </td><td>7630        </td><td>770         </td><td>10          </td><td>10          </td><td>2           </td></tr>
	<tr><td>563         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1090        </td><td>80          </td><td>240         </td><td>7820        </td><td>760         </td><td>10          </td><td>0           </td><td>2           </td></tr>
	<tr><td>564         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1150        </td><td>90          </td><td>250         </td><td>7720        </td><td>810         </td><td>0           </td><td>10          </td><td>3           </td></tr>
	<tr><td>565         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1110        </td><td>90          </td><td>230         </td><td>7810        </td><td>750         </td><td>0           </td><td>10          </td><td>2           </td></tr>
	<tr><td>566         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1010        </td><td>110         </td><td>210         </td><td>7720        </td><td>950         </td><td>0           </td><td>0           </td><td>1           </td></tr>
	<tr><td>567         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1070        </td><td>100         </td><td>220         </td><td>7730        </td><td>870         </td><td>10          </td><td>10          </td><td>2           </td></tr>
	<tr><td>568         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1280        </td><td>110         </td><td>290         </td><td>7490        </td><td>790         </td><td>10          </td><td>10          </td><td>2           </td></tr>
	<tr><td>569         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1060        </td><td>100         </td><td>270         </td><td>7740        </td><td>810         </td><td>10          </td><td>10          </td><td>3           </td></tr>
	<tr><td>570         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>1010        </td><td>90          </td><td>210         </td><td>7720        </td><td>970         </td><td>0           </td><td>0           </td><td>2           </td></tr>
	<tr><td>571         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>990         </td><td>120         </td><td>250         </td><td>7750        </td><td>870         </td><td>10          </td><td>10          </td><td>2           </td></tr>
	<tr><td>572         </td><td>West-Liguria</td><td>3           </td><td>8           </td><td>960         </td><td>80          </td><td>240         </td><td>7950        </td><td>740         </td><td>10          </td><td>20          </td><td>2           </td></tr>
</tbody>
</table>


