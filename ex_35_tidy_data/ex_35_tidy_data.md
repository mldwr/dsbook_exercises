
## Exercises

>1. Examine the dataset `co2`. Which of the following is true:

>    A. `co2` is tidy data: it has one year for each row.

>    B. `co2` is not tidy: we need at least one column with a character vector.

>    C. `co2` is not tidy:  it is a matrix not a data frame.

>    __D__. `co2` is not tidy: to be tidy we would have to wrangle it to have three columns: year, month and value; then each co2 observation has a row.

Definition of `tidy data` from this chapter is as follows: *each row represents one observation and the columns represent the different variables available for each of these observations* 

According to this defintion the time-series objects does not define a tidy data set, because each row represents the observation of some kind of carbon-dioxide measurement per year. We have just one columnt, which contains the measurement, but the meta-data `str(co2)` tells us that the data 


```R
library(dslabs)
```


```R
data("co2")
```


```R
co2[1]
```


315.42



```R
str(co2)
```

     Time-Series [1:468] from 1959 to 1998: 315 316 316 318 318 ...



```R
class(co2)
```


'ts'



```R
plot(co2)
```


![png](output_9_0.png)


>2. Examine the dataset  `ChickWeight`. Which of the following is true:

>    A.  `ChickWeight` is not tidy: each chick has more than one row. 

>    B.  `ChickWeight` is tidy: each observation, here a weight, is represented by one row. The chick from which this measurement came from is one the variables.

>    C.  `ChickWeight` is not a tidy: we are missing the year column.

>    D.  `ChickWeight` is tidy: it is stored in a data frame.


```R
data(ChickWeight)
```


```R
ChickWeight
```


<table>
<thead><tr><th scope=col>weight</th><th scope=col>Time</th><th scope=col>Chick</th><th scope=col>Diet</th></tr></thead>
<tbody>
	<tr><td> 42</td><td> 0 </td><td>1  </td><td>1  </td></tr>
	<tr><td> 51</td><td> 2 </td><td>1  </td><td>1  </td></tr>
	<tr><td> 59</td><td> 4 </td><td>1  </td><td>1  </td></tr>
	<tr><td> 64</td><td> 6 </td><td>1  </td><td>1  </td></tr>
	<tr><td> 76</td><td> 8 </td><td>1  </td><td>1  </td></tr>
	<tr><td> 93</td><td>10 </td><td>1  </td><td>1  </td></tr>
	<tr><td>106</td><td>12 </td><td>1  </td><td>1  </td></tr>
	<tr><td>125</td><td>14 </td><td>1  </td><td>1  </td></tr>
	<tr><td>149</td><td>16 </td><td>1  </td><td>1  </td></tr>
	<tr><td>171</td><td>18 </td><td>1  </td><td>1  </td></tr>
	<tr><td>199</td><td>20 </td><td>1  </td><td>1  </td></tr>
	<tr><td>205</td><td>21 </td><td>1  </td><td>1  </td></tr>
	<tr><td> 40</td><td> 0 </td><td>2  </td><td>1  </td></tr>
	<tr><td> 49</td><td> 2 </td><td>2  </td><td>1  </td></tr>
	<tr><td> 58</td><td> 4 </td><td>2  </td><td>1  </td></tr>
	<tr><td> 72</td><td> 6 </td><td>2  </td><td>1  </td></tr>
	<tr><td> 84</td><td> 8 </td><td>2  </td><td>1  </td></tr>
	<tr><td>103</td><td>10 </td><td>2  </td><td>1  </td></tr>
	<tr><td>122</td><td>12 </td><td>2  </td><td>1  </td></tr>
	<tr><td>138</td><td>14 </td><td>2  </td><td>1  </td></tr>
	<tr><td>162</td><td>16 </td><td>2  </td><td>1  </td></tr>
	<tr><td>187</td><td>18 </td><td>2  </td><td>1  </td></tr>
	<tr><td>209</td><td>20 </td><td>2  </td><td>1  </td></tr>
	<tr><td>215</td><td>21 </td><td>2  </td><td>1  </td></tr>
	<tr><td> 43</td><td> 0 </td><td>3  </td><td>1  </td></tr>
	<tr><td> 39</td><td> 2 </td><td>3  </td><td>1  </td></tr>
	<tr><td> 55</td><td> 4 </td><td>3  </td><td>1  </td></tr>
	<tr><td> 67</td><td> 6 </td><td>3  </td><td>1  </td></tr>
	<tr><td> 84</td><td> 8 </td><td>3  </td><td>1  </td></tr>
	<tr><td> 99</td><td>10 </td><td>3  </td><td>1  </td></tr>
	<tr><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td></tr>
	<tr><td>154</td><td>12 </td><td>48 </td><td>4  </td></tr>
	<tr><td>170</td><td>14 </td><td>48 </td><td>4  </td></tr>
	<tr><td>222</td><td>16 </td><td>48 </td><td>4  </td></tr>
	<tr><td>261</td><td>18 </td><td>48 </td><td>4  </td></tr>
	<tr><td>303</td><td>20 </td><td>48 </td><td>4  </td></tr>
	<tr><td>322</td><td>21 </td><td>48 </td><td>4  </td></tr>
	<tr><td> 40</td><td> 0 </td><td>49 </td><td>4  </td></tr>
	<tr><td> 53</td><td> 2 </td><td>49 </td><td>4  </td></tr>
	<tr><td> 64</td><td> 4 </td><td>49 </td><td>4  </td></tr>
	<tr><td> 85</td><td> 6 </td><td>49 </td><td>4  </td></tr>
	<tr><td>108</td><td> 8 </td><td>49 </td><td>4  </td></tr>
	<tr><td>128</td><td>10 </td><td>49 </td><td>4  </td></tr>
	<tr><td>152</td><td>12 </td><td>49 </td><td>4  </td></tr>
	<tr><td>166</td><td>14 </td><td>49 </td><td>4  </td></tr>
	<tr><td>184</td><td>16 </td><td>49 </td><td>4  </td></tr>
	<tr><td>203</td><td>18 </td><td>49 </td><td>4  </td></tr>
	<tr><td>233</td><td>20 </td><td>49 </td><td>4  </td></tr>
	<tr><td>237</td><td>21 </td><td>49 </td><td>4  </td></tr>
	<tr><td> 41</td><td> 0 </td><td>50 </td><td>4  </td></tr>
	<tr><td> 54</td><td> 2 </td><td>50 </td><td>4  </td></tr>
	<tr><td> 67</td><td> 4 </td><td>50 </td><td>4  </td></tr>
	<tr><td> 84</td><td> 6 </td><td>50 </td><td>4  </td></tr>
	<tr><td>105</td><td> 8 </td><td>50 </td><td>4  </td></tr>
	<tr><td>122</td><td>10 </td><td>50 </td><td>4  </td></tr>
	<tr><td>155</td><td>12 </td><td>50 </td><td>4  </td></tr>
	<tr><td>175</td><td>14 </td><td>50 </td><td>4  </td></tr>
	<tr><td>205</td><td>16 </td><td>50 </td><td>4  </td></tr>
	<tr><td>234</td><td>18 </td><td>50 </td><td>4  </td></tr>
	<tr><td>264</td><td>20 </td><td>50 </td><td>4  </td></tr>
	<tr><td>264</td><td>21 </td><td>50 </td><td>4  </td></tr>
</tbody>
</table>




```R
str(ChickWeight)
```

    Classes ‘nfnGroupedData’, ‘nfGroupedData’, ‘groupedData’ and 'data.frame':	578 obs. of  4 variables:
     $ weight: num  42 51 59 64 76 93 106 125 149 171 ...
     $ Time  : num  0 2 4 6 8 10 12 14 16 18 ...
     $ Chick : Ord.factor w/ 50 levels "18"<"16"<"15"<..: 15 15 15 15 15 15 15 15 15 15 ...
     $ Diet  : Factor w/ 4 levels "1","2","3","4": 1 1 1 1 1 1 1 1 1 1 ...
     - attr(*, "formula")=Class 'formula'  language weight ~ Time | Chick
      .. ..- attr(*, ".Environment")=<environment: R_EmptyEnv> 
     - attr(*, "outer")=Class 'formula'  language ~Diet
      .. ..- attr(*, ".Environment")=<environment: R_EmptyEnv> 
     - attr(*, "labels")=List of 2
      ..$ x: chr "Time"
      ..$ y: chr "Body weight"
     - attr(*, "units")=List of 2
      ..$ x: chr "(days)"
      ..$ y: chr "(gm)"



```R
class(ChickWeight)
```


<ol class=list-inline>
	<li>'nfnGroupedData'</li>
	<li>'nfGroupedData'</li>
	<li>'groupedData'</li>
	<li>'data.frame'</li>
</ol>



>3. Examine the dataset `BOD`. Which of the following is true:

>    A. `BOD` is not tidy: it only has six rows.

>    B. `BOD` is not tidy: the first column is just an index.

>    C. `BOD` is tidy: each row is an observation with two values, time and demand.

>    D. `BOD` is tidy: all small datasets are tidy by definition.

>4. Which of the following datasets is tidy (you can pick more than one):

>    A. `BJsales`

>    B. `EuStockMarkets`

>    C. `DNase`

>    D. `Formaldehyde`

>    E. `Orange`

>    F. `UCBAdmissions`


```R

```
