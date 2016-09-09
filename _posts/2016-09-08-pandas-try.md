---
title: 'Pandas try-out.'
layout: post
date: '2016-09-08 22:25'
tag:
  - Python
  - Pandas
  - Programming
  - Data Analysis
blog: true
---

*Please find the original code at: [fluency03/pandas-try.ipynb](https://gist.github.com/fluency03/5bd92243dd350c12bb8f8ec73e02c4ac)*

---


This is a try-out of Pandas, an efficient Python library for data processing.
Reference: http://pandas.pydata.org/pandas-docs/stable/10min.html.


```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```


```python
s = pd.Series([1, 3, 5, np.nan, 6, 8])
```


```python
s
```




    0    1.0
    1    3.0
    2    5.0
    3    NaN
    4    6.0
    5    8.0
    dtype: float64




```python
dates = pd.date_range('20160901', periods=6)
```


```python
dates
```




    DatetimeIndex(['2016-09-01', '2016-09-02', '2016-09-03', '2016-09-04',
                   '2016-09-05', '2016-09-06'],
                  dtype='datetime64[ns]', freq='D')




```python
df = pd.DataFrame(np.random.randn(6,4), index=dates, columns=list('ABCD'))
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>-2.606406</td>
      <td>0.274855</td>
      <td>0.555592</td>
      <td>-0.026283</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>0.617144</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>0.140608</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>-0.481306</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>-1.230769</td>
      <td>-0.750365</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>-0.029360</td>
      <td>0.934064</td>
      <td>1.543013</td>
      <td>-0.654158</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2 = pd.DataFrame({
        'A': 1.,
        'B': pd.Timestamp('20160908'),
        'C': pd.Series(1, index=list(range(4)), dtype='float32'),
        'D': np.array([3] * 4, dtype='int32'),
        'E': pd.Categorical(['test', 'run', 'test', 'run']),
        'F': 'foo'
    })
```


```python
df2
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>2016-09-08</td>
      <td>1.0</td>
      <td>3</td>
      <td>test</td>
      <td>foo</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.0</td>
      <td>2016-09-08</td>
      <td>1.0</td>
      <td>3</td>
      <td>run</td>
      <td>foo</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1.0</td>
      <td>2016-09-08</td>
      <td>1.0</td>
      <td>3</td>
      <td>test</td>
      <td>foo</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1.0</td>
      <td>2016-09-08</td>
      <td>1.0</td>
      <td>3</td>
      <td>run</td>
      <td>foo</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2.dtypes
```




    A           float64
    B    datetime64[ns]
    C           float32
    D             int32
    E          category
    F            object
    dtype: object




```python
df.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>-2.606406</td>
      <td>0.274855</td>
      <td>0.555592</td>
      <td>-0.026283</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>0.617144</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>0.140608</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>-0.481306</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>-1.230769</td>
      <td>-0.750365</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.tail(2)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>-1.230769</td>
      <td>-0.750365</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>-0.029360</td>
      <td>0.934064</td>
      <td>1.543013</td>
      <td>-0.654158</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.index
```




    DatetimeIndex(['2016-09-01', '2016-09-02', '2016-09-03', '2016-09-04',
                   '2016-09-05', '2016-09-06'],
                  dtype='datetime64[ns]', freq='D')




```python
df.columns
```




    Index([u'A', u'B', u'C', u'D'], dtype='object')




```python
df.values
```




    array([[-2.60640646,  0.27485454,  0.55559248, -0.02628256],
           [ 1.39658559, -1.51964705, -0.03348377,  0.61714409],
           [ 0.06083428,  0.54166305, -0.22300526,  0.14060774],
           [ 0.3583945 , -0.93525599, -0.8367702 , -0.48130596],
           [ 1.50447907,  0.95825894, -1.23076907, -0.75036456],
           [-0.02936032,  0.93406389,  1.54301299, -0.65415822]])




```python
df.describe()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>6.000000</td>
      <td>6.000000</td>
      <td>6.000000</td>
      <td>6.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>0.114088</td>
      <td>0.042323</td>
      <td>-0.037570</td>
      <td>-0.192393</td>
    </tr>
    <tr>
      <th>std</th>
      <td>1.487426</td>
      <td>1.032760</td>
      <td>0.994679</td>
      <td>0.529502</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-2.606406</td>
      <td>-1.519647</td>
      <td>-1.230769</td>
      <td>-0.750365</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>-0.006812</td>
      <td>-0.632728</td>
      <td>-0.683329</td>
      <td>-0.610945</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>0.209614</td>
      <td>0.408259</td>
      <td>-0.128245</td>
      <td>-0.253794</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>1.137038</td>
      <td>0.835964</td>
      <td>0.408323</td>
      <td>0.098885</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>1.543013</td>
      <td>0.617144</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.T
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>2016-09-01 00:00:00</th>
      <th>2016-09-02 00:00:00</th>
      <th>2016-09-03 00:00:00</th>
      <th>2016-09-04 00:00:00</th>
      <th>2016-09-05 00:00:00</th>
      <th>2016-09-06 00:00:00</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>-2.606406</td>
      <td>1.396586</td>
      <td>0.060834</td>
      <td>0.358394</td>
      <td>1.504479</td>
      <td>-0.029360</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.274855</td>
      <td>-1.519647</td>
      <td>0.541663</td>
      <td>-0.935256</td>
      <td>0.958259</td>
      <td>0.934064</td>
    </tr>
    <tr>
      <th>C</th>
      <td>0.555592</td>
      <td>-0.033484</td>
      <td>-0.223005</td>
      <td>-0.836770</td>
      <td>-1.230769</td>
      <td>1.543013</td>
    </tr>
    <tr>
      <th>D</th>
      <td>-0.026283</td>
      <td>0.617144</td>
      <td>0.140608</td>
      <td>-0.481306</td>
      <td>-0.750365</td>
      <td>-0.654158</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.sort_index(axis=1, ascending=False)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>D</th>
      <th>C</th>
      <th>B</th>
      <th>A</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>-0.026283</td>
      <td>0.555592</td>
      <td>0.274855</td>
      <td>-2.606406</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>0.617144</td>
      <td>-0.033484</td>
      <td>-1.519647</td>
      <td>1.396586</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.140608</td>
      <td>-0.223005</td>
      <td>0.541663</td>
      <td>0.060834</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>-0.481306</td>
      <td>-0.836770</td>
      <td>-0.935256</td>
      <td>0.358394</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>-0.750365</td>
      <td>-1.230769</td>
      <td>0.958259</td>
      <td>1.504479</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>-0.654158</td>
      <td>1.543013</td>
      <td>0.934064</td>
      <td>-0.029360</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.sort_index(axis=1)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>-2.606406</td>
      <td>0.274855</td>
      <td>0.555592</td>
      <td>-0.026283</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>0.617144</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>0.140608</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>-0.481306</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>-1.230769</td>
      <td>-0.750365</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>-0.029360</td>
      <td>0.934064</td>
      <td>1.543013</td>
      <td>-0.654158</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.sort_values(by='C')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>-1.230769</td>
      <td>-0.750365</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>-0.481306</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>0.140608</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>0.617144</td>
    </tr>
    <tr>
      <th>2016-09-01</th>
      <td>-2.606406</td>
      <td>0.274855</td>
      <td>0.555592</td>
      <td>-0.026283</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>-0.029360</td>
      <td>0.934064</td>
      <td>1.543013</td>
      <td>-0.654158</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['C']
```




    2016-09-01    0.555592
    2016-09-02   -0.033484
    2016-09-03   -0.223005
    2016-09-04   -0.836770
    2016-09-05   -1.230769
    2016-09-06    1.543013
    Freq: D, Name: C, dtype: float64




```python
df[0:3]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>-2.606406</td>
      <td>0.274855</td>
      <td>0.555592</td>
      <td>-0.026283</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>0.617144</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>0.140608</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['20160903':'20160905']
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>0.140608</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>-0.481306</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>-1.230769</td>
      <td>-0.750365</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc[dates[1]]
```




    A    1.396586
    B   -1.519647
    C   -0.033484
    D    0.617144
    Name: 2016-09-02 00:00:00, dtype: float64




```python
df.loc[:, ['B', 'D']]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>B</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>0.274855</td>
      <td>-0.026283</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>-1.519647</td>
      <td>0.617144</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.541663</td>
      <td>0.140608</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>-0.935256</td>
      <td>-0.481306</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>0.958259</td>
      <td>-0.750365</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>0.934064</td>
      <td>-0.654158</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc['20160903':'20160905', ['B', 'D']]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>B</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-03</th>
      <td>0.541663</td>
      <td>0.140608</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>-0.935256</td>
      <td>-0.481306</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>0.958259</td>
      <td>-0.750365</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc['20160903', ['B', 'D']]
```




    B    0.541663
    D    0.140608
    Name: 2016-09-03 00:00:00, dtype: float64




```python
df.loc['20160903', 'D']
```




    0.14060774095817161




```python
df.loc[dates[2], 'D']
```




    0.14060774095817161




```python
df.at[dates[2], 'D']
```




    0.14060774095817161




```python
df.iloc[3]
```




    A    0.358394
    B   -0.935256
    C   -0.836770
    D   -0.481306
    Name: 2016-09-04 00:00:00, dtype: float64




```python
df.iloc[3:5,0:2]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
    </tr>
  </tbody>
</table>
</div>




```python
 df.iloc[[1,2,4],[0,2]]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-0.033484</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>-0.223005</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>-1.230769</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[1:3,:]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>0.617144</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>0.140608</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[:,1:3]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>0.274855</td>
      <td>0.555592</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>-1.519647</td>
      <td>-0.033484</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.541663</td>
      <td>-0.223005</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>-0.935256</td>
      <td>-0.836770</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>0.958259</td>
      <td>-1.230769</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>0.934064</td>
      <td>1.543013</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[1,1]
```




    -1.5196470496894643




```python
df.iat[1,1]
```




    -1.5196470496894643




```python
df[df.A > 0]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>0.617144</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>0.140608</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>-0.481306</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>-1.230769</td>
      <td>-0.750365</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.A
```




    2016-09-01   -2.606406
    2016-09-02    1.396586
    2016-09-03    0.060834
    2016-09-04    0.358394
    2016-09-05    1.504479
    2016-09-06   -0.029360
    Freq: D, Name: A, dtype: float64




```python
df[df > 0]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>NaN</td>
      <td>0.274855</td>
      <td>0.555592</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.617144</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>NaN</td>
      <td>0.140608</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>NaN</td>
      <td>0.934064</td>
      <td>1.543013</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_copy = df.copy()
```


```python
df_copy['E'] = ['one', 'one','two','three','four','three']
```


```python
df_copy
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>-2.606406</td>
      <td>0.274855</td>
      <td>0.555592</td>
      <td>-0.026283</td>
      <td>one</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>0.617144</td>
      <td>one</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>0.140608</td>
      <td>two</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>-0.481306</td>
      <td>three</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>-1.230769</td>
      <td>-0.750365</td>
      <td>four</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>-0.029360</td>
      <td>0.934064</td>
      <td>1.543013</td>
      <td>-0.654158</td>
      <td>three</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_copy[df_copy['E'].isin(['two','four'])]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>0.140608</td>
      <td>two</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>-1.230769</td>
      <td>-0.750365</td>
      <td>four</td>
    </tr>
  </tbody>
</table>
</div>




```python
s1 = pd.Series([1, 2, 3, 4, 5, 6], index=pd.date_range('20160901', periods=6))
```


```python
s1
```




    2016-09-01    1
    2016-09-02    2
    2016-09-03    3
    2016-09-04    4
    2016-09-05    5
    2016-09-06    6
    Freq: D, dtype: int64




```python
df['F'] = s1
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>-2.606406</td>
      <td>0.274855</td>
      <td>0.555592</td>
      <td>-0.026283</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>0.617144</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>0.140608</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>-0.481306</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>-1.230769</td>
      <td>-0.750365</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>-0.029360</td>
      <td>0.934064</td>
      <td>1.543013</td>
      <td>-0.654158</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.at[dates[0], 'A']
```




    -2.6064064590654761




```python
df.iat[0,1] = 0
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>-2.606406</td>
      <td>0.000000</td>
      <td>0.555592</td>
      <td>-0.026283</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>0.617144</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>0.140608</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>-0.481306</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>-1.230769</td>
      <td>-0.750365</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>-0.029360</td>
      <td>0.934064</td>
      <td>1.543013</td>
      <td>-0.654158</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>




```python
 df.loc[:,'D'] = np.array([5] * len(df))
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>-2.606406</td>
      <td>0.000000</td>
      <td>0.555592</td>
      <td>5</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>5</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>5</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>5</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>-1.230769</td>
      <td>5</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>-0.029360</td>
      <td>0.934064</td>
      <td>1.543013</td>
      <td>5</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.at[dates[0], 'A'] = 0
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.555592</td>
      <td>5</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>5</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>5</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>5</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>-1.230769</td>
      <td>5</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>-0.029360</td>
      <td>0.934064</td>
      <td>1.543013</td>
      <td>5</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>




```python
df3 = df.copy()
```


```python
df3[df3 > 0] = -df3
```


```python
df3
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>-0.555592</td>
      <td>-5</td>
      <td>-1</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>-1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>-5</td>
      <td>-2</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>-0.060834</td>
      <td>-0.541663</td>
      <td>-0.223005</td>
      <td>-5</td>
      <td>-3</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>-0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>-5</td>
      <td>-4</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>-1.504479</td>
      <td>-0.958259</td>
      <td>-1.230769</td>
      <td>-5</td>
      <td>-5</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>-0.029360</td>
      <td>-0.934064</td>
      <td>-1.543013</td>
      <td>-5</td>
      <td>-6</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1 = df.reindex(index=dates[0:4], columns=list(df.columns) + ['E'])
```


```python
df1
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.555592</td>
      <td>5</td>
      <td>1</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>5</td>
      <td>2</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>5</td>
      <td>3</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>5</td>
      <td>4</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1.dropna(how='any')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>




```python
df1.iloc[0:2, 5] = 0
```


```python
df1
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.555592</td>
      <td>5</td>
      <td>1</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>5</td>
      <td>2</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>5</td>
      <td>3</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>5</td>
      <td>4</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1.dropna(how='any')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.555592</td>
      <td>5</td>
      <td>1</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>5</td>
      <td>2</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1.fillna(value=10)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.555592</td>
      <td>5</td>
      <td>1</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>5</td>
      <td>2</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>5</td>
      <td>3</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>5</td>
      <td>4</td>
      <td>10.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.isnull(df1)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>




```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.555592</td>
      <td>5</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>5</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>5</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>5</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>-1.230769</td>
      <td>5</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>-0.029360</td>
      <td>0.934064</td>
      <td>1.543013</td>
      <td>5</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.mean()
```




    A    0.548489
    B   -0.003486
    C   -0.037570
    D    5.000000
    F    3.500000
    dtype: float64




```python
df.mean(1)
```




    2016-09-01    1.311118
    2016-09-02    1.368691
    2016-09-03    1.675898
    2016-09-04    1.517274
    2016-09-05    2.246394
    2016-09-06    2.689543
    Freq: D, dtype: float64




```python
s = pd.Series([1, 3, 5, np.nan, 7, 9], index=dates)
```


```python
s
```




    2016-09-01    1.0
    2016-09-02    3.0
    2016-09-03    5.0
    2016-09-04    NaN
    2016-09-05    7.0
    2016-09-06    9.0
    Freq: D, dtype: float64




```python
s = s.shift(2)
```


```python
s
```




    2016-09-01    NaN
    2016-09-02    NaN
    2016-09-03    1.0
    2016-09-04    3.0
    2016-09-05    5.0
    2016-09-06    NaN
    Freq: D, dtype: float64




```python
df.sub(s, axis='index')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>-0.939166</td>
      <td>-0.458337</td>
      <td>-1.223005</td>
      <td>4.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>-2.641606</td>
      <td>-3.935256</td>
      <td>-3.836770</td>
      <td>2.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>-3.495521</td>
      <td>-4.041741</td>
      <td>-6.230769</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.555592</td>
      <td>5</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>-0.033484</td>
      <td>5</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>0.060834</td>
      <td>0.541663</td>
      <td>-0.223005</td>
      <td>5</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>0.358394</td>
      <td>-0.935256</td>
      <td>-0.836770</td>
      <td>5</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>1.504479</td>
      <td>0.958259</td>
      <td>-1.230769</td>
      <td>5</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>-0.029360</td>
      <td>0.934064</td>
      <td>1.543013</td>
      <td>5</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.apply(np.cumsum)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-09-01</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.555592</td>
      <td>5</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2016-09-02</th>
      <td>1.396586</td>
      <td>-1.519647</td>
      <td>0.522109</td>
      <td>10</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2016-09-03</th>
      <td>1.457420</td>
      <td>-0.977984</td>
      <td>0.299103</td>
      <td>15</td>
      <td>6</td>
    </tr>
    <tr>
      <th>2016-09-04</th>
      <td>1.815814</td>
      <td>-1.913240</td>
      <td>-0.537667</td>
      <td>20</td>
      <td>10</td>
    </tr>
    <tr>
      <th>2016-09-05</th>
      <td>3.320293</td>
      <td>-0.954981</td>
      <td>-1.768436</td>
      <td>25</td>
      <td>15</td>
    </tr>
    <tr>
      <th>2016-09-06</th>
      <td>3.290933</td>
      <td>-0.020917</td>
      <td>-0.225423</td>
      <td>30</td>
      <td>21</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.apply(lambda x: x.max() - x.min())
```




    A    1.533839
    B    2.477906
    C    2.773782
    D    0.000000
    F    5.000000
    dtype: float64




```python
s2 = pd.Series(np.random.randint(0, 7, size=10))
```


```python
s2
```




    0    4
    1    2
    2    6
    3    2
    4    2
    5    5
    6    4
    7    2
    8    2
    9    5
    dtype: int32




```python
s2.value_counts()
```




    2    5
    5    2
    4    2
    6    1
    dtype: int64




```python
s3 = pd.Series(['A', 'B', 'C', 'Aaba', 'Baca', np.nan, 'CABA', 'dog', 'cat'])
```


```python
s3
```




    0       A
    1       B
    2       C
    3    Aaba
    4    Baca
    5     NaN
    6    CABA
    7     dog
    8     cat
    dtype: object




```python
s3.str.lower()
```




    0       a
    1       b
    2       c
    3    aaba
    4    baca
    5     NaN
    6    caba
    7     dog
    8     cat
    dtype: object




```python
df3 = pd.DataFrame(np.random.randn(10, 4))
```


```python
df3
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-1.876633</td>
      <td>0.816489</td>
      <td>0.422206</td>
      <td>0.716672</td>
    </tr>
    <tr>
      <th>1</th>
      <td>-0.241701</td>
      <td>0.335117</td>
      <td>0.267718</td>
      <td>-1.721236</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.339564</td>
      <td>-0.293390</td>
      <td>-2.309714</td>
      <td>-1.002716</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.851409</td>
      <td>0.848496</td>
      <td>0.498519</td>
      <td>-0.697270</td>
    </tr>
    <tr>
      <th>4</th>
      <td>-0.276314</td>
      <td>-0.685067</td>
      <td>-0.453861</td>
      <td>0.057357</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0.165486</td>
      <td>-2.245062</td>
      <td>1.367566</td>
      <td>-1.149988</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0.324165</td>
      <td>-1.072810</td>
      <td>1.099337</td>
      <td>-0.730654</td>
    </tr>
    <tr>
      <th>7</th>
      <td>-1.733344</td>
      <td>-0.471668</td>
      <td>0.842963</td>
      <td>-0.777373</td>
    </tr>
    <tr>
      <th>8</th>
      <td>-1.479849</td>
      <td>0.159663</td>
      <td>1.147717</td>
      <td>0.418020</td>
    </tr>
    <tr>
      <th>9</th>
      <td>-0.173146</td>
      <td>0.150676</td>
      <td>0.361353</td>
      <td>-1.150199</td>
    </tr>
  </tbody>
</table>
</div>




```python
pieces = [df3[:3], df3[3:7], df3[7:]]
```


```python
pieces
```




    [          0         1         2         3
     0 -1.876633  0.816489  0.422206  0.716672
     1 -0.241701  0.335117  0.267718 -1.721236
     2  0.339564 -0.293390 -2.309714 -1.002716,
               0         1         2         3
     3  0.851409  0.848496  0.498519 -0.697270
     4 -0.276314 -0.685067 -0.453861  0.057357
     5  0.165486 -2.245062  1.367566 -1.149988
     6  0.324165 -1.072810  1.099337 -0.730654,
               0         1         2         3
     7 -1.733344 -0.471668  0.842963 -0.777373
     8 -1.479849  0.159663  1.147717  0.418020
     9 -0.173146  0.150676  0.361353 -1.150199]




```python
pd.concat(pieces)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-1.876633</td>
      <td>0.816489</td>
      <td>0.422206</td>
      <td>0.716672</td>
    </tr>
    <tr>
      <th>1</th>
      <td>-0.241701</td>
      <td>0.335117</td>
      <td>0.267718</td>
      <td>-1.721236</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.339564</td>
      <td>-0.293390</td>
      <td>-2.309714</td>
      <td>-1.002716</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.851409</td>
      <td>0.848496</td>
      <td>0.498519</td>
      <td>-0.697270</td>
    </tr>
    <tr>
      <th>4</th>
      <td>-0.276314</td>
      <td>-0.685067</td>
      <td>-0.453861</td>
      <td>0.057357</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0.165486</td>
      <td>-2.245062</td>
      <td>1.367566</td>
      <td>-1.149988</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0.324165</td>
      <td>-1.072810</td>
      <td>1.099337</td>
      <td>-0.730654</td>
    </tr>
    <tr>
      <th>7</th>
      <td>-1.733344</td>
      <td>-0.471668</td>
      <td>0.842963</td>
      <td>-0.777373</td>
    </tr>
    <tr>
      <th>8</th>
      <td>-1.479849</td>
      <td>0.159663</td>
      <td>1.147717</td>
      <td>0.418020</td>
    </tr>
    <tr>
      <th>9</th>
      <td>-0.173146</td>
      <td>0.150676</td>
      <td>0.361353</td>
      <td>-1.150199</td>
    </tr>
  </tbody>
</table>
</div>




```python
left = pd.DataFrame({'key': ['foo', 'foo'], 'lval': [1, 2]})
```


```python
left
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>key</th>
      <th>lval</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>foo</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>foo</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
right = pd.DataFrame({'key': ['foo', 'foo'], 'rval': [4, 5]})
```


```python
right
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>key</th>
      <th>rval</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>foo</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>foo</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(left, right, on='key')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>key</th>
      <th>lval</th>
      <th>rval</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>foo</td>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>foo</td>
      <td>1</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>foo</td>
      <td>2</td>
      <td>4</td>
    </tr>
    <tr>
      <th>3</th>
      <td>foo</td>
      <td>2</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python
left2 = pd.DataFrame({'key': ['foo1', 'foo2'], 'lval': [1, 2]})
right2 = pd.DataFrame({'key': ['foo4', 'foo5'], 'rval': [4, 5]})
pd.merge(left, right, on='key')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>key</th>
      <th>lval</th>
      <th>rval</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>foo</td>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>foo</td>
      <td>1</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>foo</td>
      <td>2</td>
      <td>4</td>
    </tr>
    <tr>
      <th>3</th>
      <td>foo</td>
      <td>2</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python
left2
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>key</th>
      <th>lval</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>foo1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>foo2</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
right2
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>key</th>
      <th>rval</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>foo4</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>foo5</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python
df4 = pd.DataFrame(np.random.randn(8, 4), columns=['A','B','C','D'])
```


```python
df4
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-1.090537</td>
      <td>2.060047</td>
      <td>-0.127662</td>
      <td>-0.900321</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.994967</td>
      <td>1.094914</td>
      <td>-0.220771</td>
      <td>0.590341</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.356022</td>
      <td>-1.346051</td>
      <td>-0.830716</td>
      <td>1.252693</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.630810</td>
      <td>0.536613</td>
      <td>0.100553</td>
      <td>-0.447036</td>
    </tr>
    <tr>
      <th>4</th>
      <td>-1.448831</td>
      <td>-0.523173</td>
      <td>-0.556934</td>
      <td>0.245877</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0.214729</td>
      <td>-1.113644</td>
      <td>0.626774</td>
      <td>-0.049145</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0.267699</td>
      <td>0.183280</td>
      <td>1.810382</td>
      <td>0.051761</td>
    </tr>
    <tr>
      <th>7</th>
      <td>-1.601603</td>
      <td>-0.142685</td>
      <td>-1.991400</td>
      <td>-0.260031</td>
    </tr>
  </tbody>
</table>
</div>




```python
s4 = df4.iloc[3]
```


```python
s4
```




    A    0.630810
    B    0.536613
    C    0.100553
    D   -0.447036
    Name: 3, dtype: float64




```python
df4.append(s4, ignore_index=True)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-1.090537</td>
      <td>2.060047</td>
      <td>-0.127662</td>
      <td>-0.900321</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.994967</td>
      <td>1.094914</td>
      <td>-0.220771</td>
      <td>0.590341</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.356022</td>
      <td>-1.346051</td>
      <td>-0.830716</td>
      <td>1.252693</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.630810</td>
      <td>0.536613</td>
      <td>0.100553</td>
      <td>-0.447036</td>
    </tr>
    <tr>
      <th>4</th>
      <td>-1.448831</td>
      <td>-0.523173</td>
      <td>-0.556934</td>
      <td>0.245877</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0.214729</td>
      <td>-1.113644</td>
      <td>0.626774</td>
      <td>-0.049145</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0.267699</td>
      <td>0.183280</td>
      <td>1.810382</td>
      <td>0.051761</td>
    </tr>
    <tr>
      <th>7</th>
      <td>-1.601603</td>
      <td>-0.142685</td>
      <td>-1.991400</td>
      <td>-0.260031</td>
    </tr>
    <tr>
      <th>8</th>
      <td>0.630810</td>
      <td>0.536613</td>
      <td>0.100553</td>
      <td>-0.447036</td>
    </tr>
  </tbody>
</table>
</div>




```python
df5 = pd.DataFrame({
        'A': ['foo', 'bar', 'foo', 'bar', 'foo', 'bar', 'foo', 'foo'],
        'B': ['one', 'one', 'two', 'three', 'two', 'two', 'one', 'three'],
        'C': np.random.randn(8),
        'D': np.random.randn(8)
    })
```


```python
df5
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>foo</td>
      <td>one</td>
      <td>0.097762</td>
      <td>-1.618375</td>
    </tr>
    <tr>
      <th>1</th>
      <td>bar</td>
      <td>one</td>
      <td>0.721226</td>
      <td>-0.360733</td>
    </tr>
    <tr>
      <th>2</th>
      <td>foo</td>
      <td>two</td>
      <td>-0.082561</td>
      <td>0.815051</td>
    </tr>
    <tr>
      <th>3</th>
      <td>bar</td>
      <td>three</td>
      <td>0.884130</td>
      <td>0.304236</td>
    </tr>
    <tr>
      <th>4</th>
      <td>foo</td>
      <td>two</td>
      <td>-1.726142</td>
      <td>0.306904</td>
    </tr>
    <tr>
      <th>5</th>
      <td>bar</td>
      <td>two</td>
      <td>0.594687</td>
      <td>-0.872794</td>
    </tr>
    <tr>
      <th>6</th>
      <td>foo</td>
      <td>one</td>
      <td>-1.602134</td>
      <td>-0.514884</td>
    </tr>
    <tr>
      <th>7</th>
      <td>foo</td>
      <td>three</td>
      <td>0.762957</td>
      <td>-0.634142</td>
    </tr>
  </tbody>
</table>
</div>




```python
df5.groupby('A').sum()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>A</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bar</th>
      <td>2.200043</td>
      <td>-0.929292</td>
    </tr>
    <tr>
      <th>foo</th>
      <td>-2.550118</td>
      <td>-1.645447</td>
    </tr>
  </tbody>
</table>
</div>




```python
df5.groupby('B').sum()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>B</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.783146</td>
      <td>-2.493992</td>
    </tr>
    <tr>
      <th>three</th>
      <td>1.647087</td>
      <td>-0.329907</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-1.214016</td>
      <td>0.249161</td>
    </tr>
  </tbody>
</table>
</div>




```python
df5.groupby(['A','B']).sum()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>A</th>
      <th>B</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">bar</th>
      <th>one</th>
      <td>0.721226</td>
      <td>-0.360733</td>
    </tr>
    <tr>
      <th>three</th>
      <td>0.884130</td>
      <td>0.304236</td>
    </tr>
    <tr>
      <th>two</th>
      <td>0.594687</td>
      <td>-0.872794</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">foo</th>
      <th>one</th>
      <td>-1.504372</td>
      <td>-2.133260</td>
    </tr>
    <tr>
      <th>three</th>
      <td>0.762957</td>
      <td>-0.634142</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-1.808703</td>
      <td>1.121955</td>
    </tr>
  </tbody>
</table>
</div>




```python
tuples = list(zip(*[
            ['bar', 'bar', 'baz', 'baz', 'foo', 'foo', 'qux', 'qux'],
            ['one', 'two', 'one', 'two', 'one', 'two', 'one', 'two']
        ]))
```


```python
tuples
```




    [('bar', 'one'),
     ('bar', 'two'),
     ('baz', 'one'),
     ('baz', 'two'),
     ('foo', 'one'),
     ('foo', 'two'),
     ('qux', 'one'),
     ('qux', 'two')]




```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```


```python
index_tuples = pd.MultiIndex.from_tuples(tuples, names=['first', 'second'])
```


```python
index_tuples
```




    MultiIndex(levels=[[u'bar', u'baz', u'foo', u'qux'], [u'one', u'two']],
               labels=[[0, 0, 1, 1, 2, 2, 3, 3], [0, 1, 0, 1, 0, 1, 0, 1]],
               names=[u'first', u'second'])




```python
df6 = pd.DataFrame(np.random.randn(8, 2), index=index_tuples, columns=['A', 'B'])
```


```python
df6
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
    <tr>
      <th>first</th>
      <th>second</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">bar</th>
      <th>one</th>
      <td>0.229260</td>
      <td>1.879628</td>
    </tr>
    <tr>
      <th>two</th>
      <td>1.307560</td>
      <td>-0.429444</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">baz</th>
      <th>one</th>
      <td>-1.370665</td>
      <td>-0.051630</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.502600</td>
      <td>-1.439812</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">foo</th>
      <th>one</th>
      <td>1.262123</td>
      <td>-0.312040</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.145607</td>
      <td>-0.698815</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">qux</th>
      <th>one</th>
      <td>-1.091181</td>
      <td>0.227027</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.294299</td>
      <td>-1.270815</td>
    </tr>
  </tbody>
</table>
</div>




```python
df7 = df6[:4]
```


```python
df7
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
    <tr>
      <th>first</th>
      <th>second</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">bar</th>
      <th>one</th>
      <td>0.229260</td>
      <td>1.879628</td>
    </tr>
    <tr>
      <th>two</th>
      <td>1.307560</td>
      <td>-0.429444</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">baz</th>
      <th>one</th>
      <td>-1.370665</td>
      <td>-0.051630</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.502600</td>
      <td>-1.439812</td>
    </tr>
  </tbody>
</table>
</div>




```python
stacked = df7.stack()
```


```python
stacked
```




    first  second   
    bar    one     A    0.229260
                   B    1.879628
           two     A    1.307560
                   B   -0.429444
    baz    one     A   -1.370665
                   B   -0.051630
           two     A   -0.502600
                   B   -1.439812
    dtype: float64




```python
stacked.unstack()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
    <tr>
      <th>first</th>
      <th>second</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">bar</th>
      <th>one</th>
      <td>0.229260</td>
      <td>1.879628</td>
    </tr>
    <tr>
      <th>two</th>
      <td>1.307560</td>
      <td>-0.429444</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">baz</th>
      <th>one</th>
      <td>-1.370665</td>
      <td>-0.051630</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.502600</td>
      <td>-1.439812</td>
    </tr>
  </tbody>
</table>
</div>




```python
stacked.unstack(1)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>second</th>
      <th>one</th>
      <th>two</th>
    </tr>
    <tr>
      <th>first</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">bar</th>
      <th>A</th>
      <td>0.229260</td>
      <td>1.307560</td>
    </tr>
    <tr>
      <th>B</th>
      <td>1.879628</td>
      <td>-0.429444</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">baz</th>
      <th>A</th>
      <td>-1.370665</td>
      <td>-0.502600</td>
    </tr>
    <tr>
      <th>B</th>
      <td>-0.051630</td>
      <td>-1.439812</td>
    </tr>
  </tbody>
</table>
</div>




```python
stacked.unstack(0)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>first</th>
      <th>bar</th>
      <th>baz</th>
    </tr>
    <tr>
      <th>second</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">one</th>
      <th>A</th>
      <td>0.229260</td>
      <td>-1.370665</td>
    </tr>
    <tr>
      <th>B</th>
      <td>1.879628</td>
      <td>-0.051630</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">two</th>
      <th>A</th>
      <td>1.307560</td>
      <td>-0.502600</td>
    </tr>
    <tr>
      <th>B</th>
      <td>-0.429444</td>
      <td>-1.439812</td>
    </tr>
  </tbody>
</table>
</div>




```python
df8 = pd.DataFrame({
        'A': ['one', 'one', 'two', 'three'] * 3,
        'B': ['A', 'B', 'C'] * 4,
        'C': ['foo', 'foo', 'foo', 'bar', 'bar', 'bar'] * 2,
        'D': np.random.randn(12),
        'E': np.random.randn(12)
    })
```


```python
df8
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>one</td>
      <td>A</td>
      <td>foo</td>
      <td>1.500428</td>
      <td>-0.162981</td>
    </tr>
    <tr>
      <th>1</th>
      <td>one</td>
      <td>B</td>
      <td>foo</td>
      <td>-0.182384</td>
      <td>-2.619063</td>
    </tr>
    <tr>
      <th>2</th>
      <td>two</td>
      <td>C</td>
      <td>foo</td>
      <td>0.771776</td>
      <td>-0.003201</td>
    </tr>
    <tr>
      <th>3</th>
      <td>three</td>
      <td>A</td>
      <td>bar</td>
      <td>1.034832</td>
      <td>0.745759</td>
    </tr>
    <tr>
      <th>4</th>
      <td>one</td>
      <td>B</td>
      <td>bar</td>
      <td>-0.603579</td>
      <td>-0.328514</td>
    </tr>
    <tr>
      <th>5</th>
      <td>one</td>
      <td>C</td>
      <td>bar</td>
      <td>0.547359</td>
      <td>-0.360326</td>
    </tr>
    <tr>
      <th>6</th>
      <td>two</td>
      <td>A</td>
      <td>foo</td>
      <td>0.194476</td>
      <td>0.703153</td>
    </tr>
    <tr>
      <th>7</th>
      <td>three</td>
      <td>B</td>
      <td>foo</td>
      <td>-0.474702</td>
      <td>0.012466</td>
    </tr>
    <tr>
      <th>8</th>
      <td>one</td>
      <td>C</td>
      <td>foo</td>
      <td>0.012113</td>
      <td>-0.101952</td>
    </tr>
    <tr>
      <th>9</th>
      <td>one</td>
      <td>A</td>
      <td>bar</td>
      <td>-1.147750</td>
      <td>1.017714</td>
    </tr>
    <tr>
      <th>10</th>
      <td>two</td>
      <td>B</td>
      <td>bar</td>
      <td>0.299260</td>
      <td>-0.459977</td>
    </tr>
    <tr>
      <th>11</th>
      <td>three</td>
      <td>C</td>
      <td>bar</td>
      <td>0.953180</td>
      <td>0.792798</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.pivot_table(df8, values='D', index=['A', 'B'], columns=['C'])
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>C</th>
      <th>bar</th>
      <th>foo</th>
    </tr>
    <tr>
      <th>A</th>
      <th>B</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">one</th>
      <th>A</th>
      <td>-1.147750</td>
      <td>1.500428</td>
    </tr>
    <tr>
      <th>B</th>
      <td>-0.603579</td>
      <td>-0.182384</td>
    </tr>
    <tr>
      <th>C</th>
      <td>0.547359</td>
      <td>0.012113</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">three</th>
      <th>A</th>
      <td>1.034832</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>B</th>
      <td>NaN</td>
      <td>-0.474702</td>
    </tr>
    <tr>
      <th>C</th>
      <td>0.953180</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">two</th>
      <th>A</th>
      <td>NaN</td>
      <td>0.194476</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.299260</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>C</th>
      <td>NaN</td>
      <td>0.771776</td>
    </tr>
  </tbody>
</table>
</div>




```python
rng = pd.date_range('9/1/2016', periods=100, freq='S')
```


```python
rng
```




    DatetimeIndex(['2016-09-01 00:00:00', '2016-09-01 00:00:01',
                   '2016-09-01 00:00:02', '2016-09-01 00:00:03',
                   '2016-09-01 00:00:04', '2016-09-01 00:00:05',
                   '2016-09-01 00:00:06', '2016-09-01 00:00:07',
                   '2016-09-01 00:00:08', '2016-09-01 00:00:09',
                   '2016-09-01 00:00:10', '2016-09-01 00:00:11',
                   '2016-09-01 00:00:12', '2016-09-01 00:00:13',
                   '2016-09-01 00:00:14', '2016-09-01 00:00:15',
                   '2016-09-01 00:00:16', '2016-09-01 00:00:17',
                   '2016-09-01 00:00:18', '2016-09-01 00:00:19',
                   '2016-09-01 00:00:20', '2016-09-01 00:00:21',
                   '2016-09-01 00:00:22', '2016-09-01 00:00:23',
                   '2016-09-01 00:00:24', '2016-09-01 00:00:25',
                   '2016-09-01 00:00:26', '2016-09-01 00:00:27',
                   '2016-09-01 00:00:28', '2016-09-01 00:00:29',
                   '2016-09-01 00:00:30', '2016-09-01 00:00:31',
                   '2016-09-01 00:00:32', '2016-09-01 00:00:33',
                   '2016-09-01 00:00:34', '2016-09-01 00:00:35',
                   '2016-09-01 00:00:36', '2016-09-01 00:00:37',
                   '2016-09-01 00:00:38', '2016-09-01 00:00:39',
                   '2016-09-01 00:00:40', '2016-09-01 00:00:41',
                   '2016-09-01 00:00:42', '2016-09-01 00:00:43',
                   '2016-09-01 00:00:44', '2016-09-01 00:00:45',
                   '2016-09-01 00:00:46', '2016-09-01 00:00:47',
                   '2016-09-01 00:00:48', '2016-09-01 00:00:49',
                   '2016-09-01 00:00:50', '2016-09-01 00:00:51',
                   '2016-09-01 00:00:52', '2016-09-01 00:00:53',
                   '2016-09-01 00:00:54', '2016-09-01 00:00:55',
                   '2016-09-01 00:00:56', '2016-09-01 00:00:57',
                   '2016-09-01 00:00:58', '2016-09-01 00:00:59',
                   '2016-09-01 00:01:00', '2016-09-01 00:01:01',
                   '2016-09-01 00:01:02', '2016-09-01 00:01:03',
                   '2016-09-01 00:01:04', '2016-09-01 00:01:05',
                   '2016-09-01 00:01:06', '2016-09-01 00:01:07',
                   '2016-09-01 00:01:08', '2016-09-01 00:01:09',
                   '2016-09-01 00:01:10', '2016-09-01 00:01:11',
                   '2016-09-01 00:01:12', '2016-09-01 00:01:13',
                   '2016-09-01 00:01:14', '2016-09-01 00:01:15',
                   '2016-09-01 00:01:16', '2016-09-01 00:01:17',
                   '2016-09-01 00:01:18', '2016-09-01 00:01:19',
                   '2016-09-01 00:01:20', '2016-09-01 00:01:21',
                   '2016-09-01 00:01:22', '2016-09-01 00:01:23',
                   '2016-09-01 00:01:24', '2016-09-01 00:01:25',
                   '2016-09-01 00:01:26', '2016-09-01 00:01:27',
                   '2016-09-01 00:01:28', '2016-09-01 00:01:29',
                   '2016-09-01 00:01:30', '2016-09-01 00:01:31',
                   '2016-09-01 00:01:32', '2016-09-01 00:01:33',
                   '2016-09-01 00:01:34', '2016-09-01 00:01:35',
                   '2016-09-01 00:01:36', '2016-09-01 00:01:37',
                   '2016-09-01 00:01:38', '2016-09-01 00:01:39'],
                  dtype='datetime64[ns]', freq='S')




```python
ts = pd.Series(np.random.randint(0, 500, len(rng)), index=rng)
```


```python
ts
```




    2016-09-01 00:00:00    294
    2016-09-01 00:00:01    138
    2016-09-01 00:00:02     47
    2016-09-01 00:00:03    136
    2016-09-01 00:00:04    394
    2016-09-01 00:00:05    185
    2016-09-01 00:00:06    252
    2016-09-01 00:00:07    215
    2016-09-01 00:00:08    294
    2016-09-01 00:00:09     54
    2016-09-01 00:00:10    483
    2016-09-01 00:00:11     50
    2016-09-01 00:00:12    338
    2016-09-01 00:00:13     14
    2016-09-01 00:00:14     67
    2016-09-01 00:00:15    476
    2016-09-01 00:00:16    363
    2016-09-01 00:00:17     42
    2016-09-01 00:00:18    436
    2016-09-01 00:00:19    350
    2016-09-01 00:00:20    194
    2016-09-01 00:00:21    420
    2016-09-01 00:00:22    188
    2016-09-01 00:00:23    172
    2016-09-01 00:00:24    448
    2016-09-01 00:00:25    135
    2016-09-01 00:00:26    178
    2016-09-01 00:00:27     84
    2016-09-01 00:00:28    305
    2016-09-01 00:00:29    266
                          ... 
    2016-09-01 00:01:10    156
    2016-09-01 00:01:11    457
    2016-09-01 00:01:12     70
    2016-09-01 00:01:13    278
    2016-09-01 00:01:14    132
    2016-09-01 00:01:15     91
    2016-09-01 00:01:16    464
    2016-09-01 00:01:17    217
    2016-09-01 00:01:18     93
    2016-09-01 00:01:19    252
    2016-09-01 00:01:20    485
    2016-09-01 00:01:21    410
    2016-09-01 00:01:22    251
    2016-09-01 00:01:23    444
    2016-09-01 00:01:24    180
    2016-09-01 00:01:25    383
    2016-09-01 00:01:26    376
    2016-09-01 00:01:27    235
    2016-09-01 00:01:28     54
    2016-09-01 00:01:29    334
    2016-09-01 00:01:30     59
    2016-09-01 00:01:31    260
    2016-09-01 00:01:32    174
    2016-09-01 00:01:33     89
    2016-09-01 00:01:34     52
    2016-09-01 00:01:35      7
    2016-09-01 00:01:36    373
    2016-09-01 00:01:37     85
    2016-09-01 00:01:38    426
    2016-09-01 00:01:39    209
    Freq: S, dtype: int32




```python
ts.resample('5Min').sum()
```




    2016-09-01    23738
    Freq: 5T, dtype: int32




```python
rng = pd.date_range('9/6/2016 00:00', periods=5, freq='D')
```


```python
rng
```




    DatetimeIndex(['2016-09-06', '2016-09-07', '2016-09-08', '2016-09-09',
                   '2016-09-10'],
                  dtype='datetime64[ns]', freq='D')




```python
ts = pd.Series(np.random.randn(len(rng)), rng)
```


```python
ts
```




    2016-09-06    0.074045
    2016-09-07    1.641663
    2016-09-08    0.173677
    2016-09-09   -0.072644
    2016-09-10    0.634405
    Freq: D, dtype: float64




```python
ts_utc = ts.tz_localize('UTC')
```


```python
ts_utc
```




    2016-09-06 00:00:00+00:00    0.074045
    2016-09-07 00:00:00+00:00    1.641663
    2016-09-08 00:00:00+00:00    0.173677
    2016-09-09 00:00:00+00:00   -0.072644
    2016-09-10 00:00:00+00:00    0.634405
    Freq: D, dtype: float64




```python
ts_cet = ts.tz_localize('CET')
```


```python
ts_cet
```




    2016-09-06 00:00:00+02:00    0.074045
    2016-09-07 00:00:00+02:00    1.641663
    2016-09-08 00:00:00+02:00    0.173677
    2016-09-09 00:00:00+02:00   -0.072644
    2016-09-10 00:00:00+02:00    0.634405
    Freq: D, dtype: float64




```python
ts_utc.tz_convert('US/Eastern')
```




    2016-09-05 20:00:00-04:00    0.074045
    2016-09-06 20:00:00-04:00    1.641663
    2016-09-07 20:00:00-04:00    0.173677
    2016-09-08 20:00:00-04:00   -0.072644
    2016-09-09 20:00:00-04:00    0.634405
    Freq: D, dtype: float64




```python
rng = pd.date_range('9/1/2016', periods=5, freq='M')
```


```python
rng
```




    DatetimeIndex(['2016-09-30', '2016-10-31', '2016-11-30', '2016-12-31',
                   '2017-01-31'],
                  dtype='datetime64[ns]', freq='M')




```python
ts = pd.Series(np.random.randn(len(rng)), index=rng)
```


```python
ts
```




    2016-09-30    0.753563
    2016-10-31    0.845888
    2016-11-30   -0.949407
    2016-12-31   -0.703824
    2017-01-31   -1.026283
    Freq: M, dtype: float64




```python
ps = ts.to_period()
```


```python
ps
```




    2016-09    0.753563
    2016-10    0.845888
    2016-11   -0.949407
    2016-12   -0.703824
    2017-01   -1.026283
    Freq: M, dtype: float64




```python
 ps.to_timestamp()
```




    2016-09-01    0.753563
    2016-10-01    0.845888
    2016-11-01   -0.949407
    2016-12-01   -0.703824
    2017-01-01   -1.026283
    Freq: MS, dtype: float64




```python
prng = pd.period_range('1990Q1', '2000Q4', freq='Q-NOV')
```


```python
prng
```




    PeriodIndex(['1990Q1', '1990Q2', '1990Q3', '1990Q4', '1991Q1', '1991Q2',
                 '1991Q3', '1991Q4', '1992Q1', '1992Q2', '1992Q3', '1992Q4',
                 '1993Q1', '1993Q2', '1993Q3', '1993Q4', '1994Q1', '1994Q2',
                 '1994Q3', '1994Q4', '1995Q1', '1995Q2', '1995Q3', '1995Q4',
                 '1996Q1', '1996Q2', '1996Q3', '1996Q4', '1997Q1', '1997Q2',
                 '1997Q3', '1997Q4', '1998Q1', '1998Q2', '1998Q3', '1998Q4',
                 '1999Q1', '1999Q2', '1999Q3', '1999Q4', '2000Q1', '2000Q2',
                 '2000Q3', '2000Q4'],
                dtype='int64', freq='Q-NOV')




```python
ts = pd.Series(np.random.randn(len(prng)), prng)
```


```python
ts
```




    1990Q1    0.827222
    1990Q2   -0.566670
    1990Q3    0.538898
    1990Q4    0.845913
    1991Q1   -0.429069
    1991Q2    0.643896
    1991Q3    1.213193
    1991Q4   -2.820272
    1992Q1    0.039655
    1992Q2    0.430139
    1992Q3   -0.712574
    1992Q4   -0.327513
    1993Q1   -0.895656
    1993Q2    0.666212
    1993Q3   -0.973674
    1993Q4   -1.077933
    1994Q1   -0.432721
    1994Q2    0.595106
    1994Q3    0.454867
    1994Q4    1.617461
    1995Q1   -0.033128
    1995Q2    0.884539
    1995Q3    0.456274
    1995Q4    0.590472
    1996Q1   -0.390998
    1996Q2    0.503376
    1996Q3   -0.417626
    1996Q4    1.773398
    1997Q1   -0.302470
    1997Q2   -0.495763
    1997Q3   -0.467924
    1997Q4   -0.570019
    1998Q1   -0.566928
    1998Q2   -0.891156
    1998Q3   -0.598373
    1998Q4    2.090135
    1999Q1   -0.675571
    1999Q2    0.769161
    1999Q3   -1.088377
    1999Q4   -0.663135
    2000Q1    0.230678
    2000Q2   -0.881019
    2000Q3   -0.627200
    2000Q4    1.996798
    Freq: Q-NOV, dtype: float64




```python
ts.index = (prng.asfreq('M', 'e') + 1).asfreq('H', 's') + 9
```


```python
ts
```




    1990-03-01 09:00    0.827222
    1990-06-01 09:00   -0.566670
    1990-09-01 09:00    0.538898
    1990-12-01 09:00    0.845913
    1991-03-01 09:00   -0.429069
    1991-06-01 09:00    0.643896
    1991-09-01 09:00    1.213193
    1991-12-01 09:00   -2.820272
    1992-03-01 09:00    0.039655
    1992-06-01 09:00    0.430139
    1992-09-01 09:00   -0.712574
    1992-12-01 09:00   -0.327513
    1993-03-01 09:00   -0.895656
    1993-06-01 09:00    0.666212
    1993-09-01 09:00   -0.973674
    1993-12-01 09:00   -1.077933
    1994-03-01 09:00   -0.432721
    1994-06-01 09:00    0.595106
    1994-09-01 09:00    0.454867
    1994-12-01 09:00    1.617461
    1995-03-01 09:00   -0.033128
    1995-06-01 09:00    0.884539
    1995-09-01 09:00    0.456274
    1995-12-01 09:00    0.590472
    1996-03-01 09:00   -0.390998
    1996-06-01 09:00    0.503376
    1996-09-01 09:00   -0.417626
    1996-12-01 09:00    1.773398
    1997-03-01 09:00   -0.302470
    1997-06-01 09:00   -0.495763
    1997-09-01 09:00   -0.467924
    1997-12-01 09:00   -0.570019
    1998-03-01 09:00   -0.566928
    1998-06-01 09:00   -0.891156
    1998-09-01 09:00   -0.598373
    1998-12-01 09:00    2.090135
    1999-03-01 09:00   -0.675571
    1999-06-01 09:00    0.769161
    1999-09-01 09:00   -1.088377
    1999-12-01 09:00   -0.663135
    2000-03-01 09:00    0.230678
    2000-06-01 09:00   -0.881019
    2000-09-01 09:00   -0.627200
    2000-12-01 09:00    1.996798
    Freq: H, dtype: float64




```python
df = pd.DataFrame({
        "id":[1,2,3,4,5,6], 
        "raw_grade":['a', 'b', 'b', 'a', 'a', 'e']
    })
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>raw_grade</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>b</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>b</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>a</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>a</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>e</td>
    </tr>
  </tbody>
</table>
</div>




```python
df["grade"] = df["raw_grade"].astype("category")
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>raw_grade</th>
      <th>grade</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>a</td>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>b</td>
      <td>b</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>b</td>
      <td>b</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>a</td>
      <td>a</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>a</td>
      <td>a</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>e</td>
      <td>e</td>
    </tr>
  </tbody>
</table>
</div>




```python
df["grade"].cat.categories = ["very good", "good", "very bad"]
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>raw_grade</th>
      <th>grade</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>a</td>
      <td>very good</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>b</td>
      <td>good</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>b</td>
      <td>good</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>a</td>
      <td>very good</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>a</td>
      <td>very good</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>e</td>
      <td>very bad</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.sort_values(by="grade")
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>raw_grade</th>
      <th>grade</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>e</td>
      <td>very bad</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>b</td>
      <td>good</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>b</td>
      <td>good</td>
    </tr>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>a</td>
      <td>very good</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>a</td>
      <td>very good</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>a</td>
      <td>very good</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.groupby("grade").size()
```




    grade
    very bad     1
    bad          0
    medium       0
    good         2
    very good    3
    dtype: int64




```python
ts = pd.Series(np.random.randn(1000), index=pd.date_range('5/2/1991', periods=1000))
```


```python
ts
```




    1991-05-02    1.257390
    1991-05-03   -1.791260
    1991-05-04   -0.437662
    1991-05-05   -0.533181
    1991-05-06   -0.908821
    1991-05-07   -0.486872
    1991-05-08    0.758828
    1991-05-09   -1.458996
    1991-05-10   -0.244546
    1991-05-11   -1.007976
    1991-05-12   -2.226191
    1991-05-13    1.292603
    1991-05-14   -0.887038
    1991-05-15    0.763275
    1991-05-16    0.837798
    1991-05-17   -0.094574
    1991-05-18    0.390533
    1991-05-19    2.280134
    1991-05-20   -0.900988
    1991-05-21    0.059597
    1991-05-22    1.098285
    1991-05-23   -0.461206
    1991-05-24    1.340366
    1991-05-25    0.516629
    1991-05-26   -0.977948
    1991-05-27   -0.207736
    1991-05-28   -0.630130
    1991-05-29   -0.771257
    1991-05-30    0.199690
    1991-05-31   -2.049951
                    ...   
    1993-12-27    0.713616
    1993-12-28    0.495014
    1993-12-29   -0.697527
    1993-12-30    0.751486
    1993-12-31    0.087321
    1994-01-01    1.099643
    1994-01-02    0.002018
    1994-01-03   -0.551513
    1994-01-04   -0.255413
    1994-01-05   -0.000148
    1994-01-06   -1.992390
    1994-01-07    0.657600
    1994-01-08   -1.896776
    1994-01-09    0.802736
    1994-01-10    1.577782
    1994-01-11   -0.086485
    1994-01-12    1.107224
    1994-01-13    1.038899
    1994-01-14   -0.958931
    1994-01-15   -0.282096
    1994-01-16    0.899036
    1994-01-17    0.247833
    1994-01-18   -0.304941
    1994-01-19    1.138112
    1994-01-20   -0.692533
    1994-01-21    0.480837
    1994-01-22   -0.357399
    1994-01-23   -0.850648
    1994-01-24    0.614167
    1994-01-25   -0.356880
    Freq: D, dtype: float64




```python
ts = ts.cumsum()
```


```python
%matplotlib inline
ts.plot()
```




    <matplotlib.axes._subplots.AxesSubplot at 0xa05eb70>




![png](pandas-try_files/pandas-try_162_1.png)



```python
df = pd.DataFrame(np.random.randn(1000, 4), index=ts.index, columns=['A', 'B', 'C', 'D'])
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1991-05-02</th>
      <td>-0.181150</td>
      <td>-0.957295</td>
      <td>-0.057522</td>
      <td>0.001560</td>
    </tr>
    <tr>
      <th>1991-05-03</th>
      <td>-0.284470</td>
      <td>0.742788</td>
      <td>0.647555</td>
      <td>-0.416180</td>
    </tr>
    <tr>
      <th>1991-05-04</th>
      <td>0.517094</td>
      <td>-2.871973</td>
      <td>-1.253756</td>
      <td>-0.258581</td>
    </tr>
    <tr>
      <th>1991-05-05</th>
      <td>1.592095</td>
      <td>-0.593789</td>
      <td>0.501064</td>
      <td>-0.063690</td>
    </tr>
    <tr>
      <th>1991-05-06</th>
      <td>-0.518838</td>
      <td>-0.876118</td>
      <td>-0.837675</td>
      <td>-0.564786</td>
    </tr>
    <tr>
      <th>1991-05-07</th>
      <td>1.247132</td>
      <td>-0.551763</td>
      <td>1.052134</td>
      <td>-0.093155</td>
    </tr>
    <tr>
      <th>1991-05-08</th>
      <td>-0.000902</td>
      <td>-0.761523</td>
      <td>0.437382</td>
      <td>0.381192</td>
    </tr>
    <tr>
      <th>1991-05-09</th>
      <td>-0.842995</td>
      <td>0.488727</td>
      <td>0.762946</td>
      <td>-1.532750</td>
    </tr>
    <tr>
      <th>1991-05-10</th>
      <td>-0.520463</td>
      <td>-0.219125</td>
      <td>-0.457703</td>
      <td>0.446695</td>
    </tr>
    <tr>
      <th>1991-05-11</th>
      <td>0.776387</td>
      <td>1.595178</td>
      <td>-2.194137</td>
      <td>-0.740743</td>
    </tr>
    <tr>
      <th>1991-05-12</th>
      <td>-1.239203</td>
      <td>0.879069</td>
      <td>-0.817139</td>
      <td>0.896210</td>
    </tr>
    <tr>
      <th>1991-05-13</th>
      <td>-1.168397</td>
      <td>0.341598</td>
      <td>1.129077</td>
      <td>1.138952</td>
    </tr>
    <tr>
      <th>1991-05-14</th>
      <td>0.938392</td>
      <td>0.171932</td>
      <td>-0.041558</td>
      <td>-0.016437</td>
    </tr>
    <tr>
      <th>1991-05-15</th>
      <td>-0.129544</td>
      <td>-1.639046</td>
      <td>-1.155710</td>
      <td>0.303192</td>
    </tr>
    <tr>
      <th>1991-05-16</th>
      <td>1.922161</td>
      <td>0.937356</td>
      <td>-0.533923</td>
      <td>-0.532668</td>
    </tr>
    <tr>
      <th>1991-05-17</th>
      <td>0.817362</td>
      <td>0.034958</td>
      <td>-0.597319</td>
      <td>-0.708231</td>
    </tr>
    <tr>
      <th>1991-05-18</th>
      <td>-1.282023</td>
      <td>-0.170580</td>
      <td>-0.433599</td>
      <td>-1.497121</td>
    </tr>
    <tr>
      <th>1991-05-19</th>
      <td>-1.303456</td>
      <td>-0.287871</td>
      <td>1.265599</td>
      <td>-0.002070</td>
    </tr>
    <tr>
      <th>1991-05-20</th>
      <td>-0.427402</td>
      <td>0.537894</td>
      <td>1.791134</td>
      <td>-0.246753</td>
    </tr>
    <tr>
      <th>1991-05-21</th>
      <td>2.061886</td>
      <td>0.353314</td>
      <td>0.759877</td>
      <td>-0.068749</td>
    </tr>
    <tr>
      <th>1991-05-22</th>
      <td>-0.770536</td>
      <td>1.117953</td>
      <td>-0.222758</td>
      <td>-0.154455</td>
    </tr>
    <tr>
      <th>1991-05-23</th>
      <td>-1.205073</td>
      <td>-0.264110</td>
      <td>-0.529387</td>
      <td>-1.211013</td>
    </tr>
    <tr>
      <th>1991-05-24</th>
      <td>-0.181345</td>
      <td>-1.604915</td>
      <td>1.392524</td>
      <td>0.091337</td>
    </tr>
    <tr>
      <th>1991-05-25</th>
      <td>1.104626</td>
      <td>-0.521902</td>
      <td>-0.125279</td>
      <td>0.305068</td>
    </tr>
    <tr>
      <th>1991-05-26</th>
      <td>-1.144370</td>
      <td>1.163434</td>
      <td>-0.300637</td>
      <td>1.395567</td>
    </tr>
    <tr>
      <th>1991-05-27</th>
      <td>-1.261388</td>
      <td>1.792261</td>
      <td>-0.111150</td>
      <td>-0.269389</td>
    </tr>
    <tr>
      <th>1991-05-28</th>
      <td>1.722603</td>
      <td>0.974655</td>
      <td>-0.042505</td>
      <td>1.445339</td>
    </tr>
    <tr>
      <th>1991-05-29</th>
      <td>2.212833</td>
      <td>-0.575373</td>
      <td>-0.278933</td>
      <td>-0.442497</td>
    </tr>
    <tr>
      <th>1991-05-30</th>
      <td>-1.341318</td>
      <td>1.022408</td>
      <td>0.671116</td>
      <td>0.492023</td>
    </tr>
    <tr>
      <th>1991-05-31</th>
      <td>0.592305</td>
      <td>0.607429</td>
      <td>-0.368017</td>
      <td>0.324935</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1993-12-27</th>
      <td>0.164014</td>
      <td>1.797152</td>
      <td>0.072612</td>
      <td>-0.142386</td>
    </tr>
    <tr>
      <th>1993-12-28</th>
      <td>0.674225</td>
      <td>0.295835</td>
      <td>-0.444194</td>
      <td>-1.022951</td>
    </tr>
    <tr>
      <th>1993-12-29</th>
      <td>1.231691</td>
      <td>1.241295</td>
      <td>2.248797</td>
      <td>1.162231</td>
    </tr>
    <tr>
      <th>1993-12-30</th>
      <td>0.355719</td>
      <td>-0.301497</td>
      <td>-1.061819</td>
      <td>-1.347002</td>
    </tr>
    <tr>
      <th>1993-12-31</th>
      <td>-0.100045</td>
      <td>0.448490</td>
      <td>-0.172988</td>
      <td>-0.411941</td>
    </tr>
    <tr>
      <th>1994-01-01</th>
      <td>-0.808260</td>
      <td>-0.467375</td>
      <td>-0.349722</td>
      <td>-0.432848</td>
    </tr>
    <tr>
      <th>1994-01-02</th>
      <td>0.599992</td>
      <td>-0.738425</td>
      <td>-0.345207</td>
      <td>0.606335</td>
    </tr>
    <tr>
      <th>1994-01-03</th>
      <td>-0.098913</td>
      <td>-0.766472</td>
      <td>-0.784677</td>
      <td>-1.814139</td>
    </tr>
    <tr>
      <th>1994-01-04</th>
      <td>0.957741</td>
      <td>-1.041438</td>
      <td>-0.834887</td>
      <td>-0.111918</td>
    </tr>
    <tr>
      <th>1994-01-05</th>
      <td>-0.304802</td>
      <td>-0.757530</td>
      <td>-1.137094</td>
      <td>-0.826770</td>
    </tr>
    <tr>
      <th>1994-01-06</th>
      <td>-0.850552</td>
      <td>-1.184060</td>
      <td>0.255056</td>
      <td>0.680844</td>
    </tr>
    <tr>
      <th>1994-01-07</th>
      <td>-0.480313</td>
      <td>-0.828893</td>
      <td>1.402496</td>
      <td>-0.322905</td>
    </tr>
    <tr>
      <th>1994-01-08</th>
      <td>0.234437</td>
      <td>-0.397773</td>
      <td>2.129368</td>
      <td>-0.493484</td>
    </tr>
    <tr>
      <th>1994-01-09</th>
      <td>-0.731429</td>
      <td>0.052424</td>
      <td>1.377166</td>
      <td>0.266586</td>
    </tr>
    <tr>
      <th>1994-01-10</th>
      <td>-0.040682</td>
      <td>-1.956872</td>
      <td>-0.224669</td>
      <td>0.781529</td>
    </tr>
    <tr>
      <th>1994-01-11</th>
      <td>-0.523772</td>
      <td>-0.576783</td>
      <td>0.537342</td>
      <td>-0.179806</td>
    </tr>
    <tr>
      <th>1994-01-12</th>
      <td>-0.262393</td>
      <td>-0.107493</td>
      <td>-1.569042</td>
      <td>1.950397</td>
    </tr>
    <tr>
      <th>1994-01-13</th>
      <td>-0.372553</td>
      <td>1.130330</td>
      <td>1.774926</td>
      <td>1.878014</td>
    </tr>
    <tr>
      <th>1994-01-14</th>
      <td>-0.935736</td>
      <td>0.341406</td>
      <td>-0.037356</td>
      <td>-1.605649</td>
    </tr>
    <tr>
      <th>1994-01-15</th>
      <td>-0.505803</td>
      <td>-1.541566</td>
      <td>-1.151154</td>
      <td>-0.033850</td>
    </tr>
    <tr>
      <th>1994-01-16</th>
      <td>0.125065</td>
      <td>-0.427373</td>
      <td>-0.208576</td>
      <td>0.360421</td>
    </tr>
    <tr>
      <th>1994-01-17</th>
      <td>-0.667756</td>
      <td>0.183957</td>
      <td>-1.092257</td>
      <td>1.544484</td>
    </tr>
    <tr>
      <th>1994-01-18</th>
      <td>-0.471887</td>
      <td>1.171327</td>
      <td>0.195789</td>
      <td>-0.394288</td>
    </tr>
    <tr>
      <th>1994-01-19</th>
      <td>0.013925</td>
      <td>-1.188688</td>
      <td>-0.408268</td>
      <td>-1.992954</td>
    </tr>
    <tr>
      <th>1994-01-20</th>
      <td>0.709561</td>
      <td>1.421713</td>
      <td>-0.362021</td>
      <td>-1.112694</td>
    </tr>
    <tr>
      <th>1994-01-21</th>
      <td>0.531137</td>
      <td>0.009957</td>
      <td>0.118453</td>
      <td>0.714784</td>
    </tr>
    <tr>
      <th>1994-01-22</th>
      <td>-0.636296</td>
      <td>1.604575</td>
      <td>-1.011673</td>
      <td>-0.389672</td>
    </tr>
    <tr>
      <th>1994-01-23</th>
      <td>0.592773</td>
      <td>0.574860</td>
      <td>2.326218</td>
      <td>0.045527</td>
    </tr>
    <tr>
      <th>1994-01-24</th>
      <td>1.018601</td>
      <td>-0.261418</td>
      <td>-1.934164</td>
      <td>1.397783</td>
    </tr>
    <tr>
      <th>1994-01-25</th>
      <td>0.096301</td>
      <td>0.253715</td>
      <td>0.994029</td>
      <td>2.727224</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 4 columns</p>
</div>




```python
df = df.cumsum()
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1991-05-02</th>
      <td>-0.181150</td>
      <td>-0.957295</td>
      <td>-0.057522</td>
      <td>0.001560</td>
    </tr>
    <tr>
      <th>1991-05-03</th>
      <td>-0.465619</td>
      <td>-0.214507</td>
      <td>0.590033</td>
      <td>-0.414619</td>
    </tr>
    <tr>
      <th>1991-05-04</th>
      <td>0.051474</td>
      <td>-3.086479</td>
      <td>-0.663723</td>
      <td>-0.673200</td>
    </tr>
    <tr>
      <th>1991-05-05</th>
      <td>1.643569</td>
      <td>-3.680268</td>
      <td>-0.162659</td>
      <td>-0.736890</td>
    </tr>
    <tr>
      <th>1991-05-06</th>
      <td>1.124731</td>
      <td>-4.556386</td>
      <td>-1.000335</td>
      <td>-1.301676</td>
    </tr>
    <tr>
      <th>1991-05-07</th>
      <td>2.371863</td>
      <td>-5.108150</td>
      <td>0.051799</td>
      <td>-1.394831</td>
    </tr>
    <tr>
      <th>1991-05-08</th>
      <td>2.370961</td>
      <td>-5.869673</td>
      <td>0.489181</td>
      <td>-1.013639</td>
    </tr>
    <tr>
      <th>1991-05-09</th>
      <td>1.527966</td>
      <td>-5.380946</td>
      <td>1.252127</td>
      <td>-2.546389</td>
    </tr>
    <tr>
      <th>1991-05-10</th>
      <td>1.007503</td>
      <td>-5.600070</td>
      <td>0.794424</td>
      <td>-2.099694</td>
    </tr>
    <tr>
      <th>1991-05-11</th>
      <td>1.783891</td>
      <td>-4.004892</td>
      <td>-1.399713</td>
      <td>-2.840437</td>
    </tr>
    <tr>
      <th>1991-05-12</th>
      <td>0.544687</td>
      <td>-3.125823</td>
      <td>-2.216852</td>
      <td>-1.944226</td>
    </tr>
    <tr>
      <th>1991-05-13</th>
      <td>-0.623709</td>
      <td>-2.784225</td>
      <td>-1.087775</td>
      <td>-0.805274</td>
    </tr>
    <tr>
      <th>1991-05-14</th>
      <td>0.314683</td>
      <td>-2.612293</td>
      <td>-1.129332</td>
      <td>-0.821711</td>
    </tr>
    <tr>
      <th>1991-05-15</th>
      <td>0.185139</td>
      <td>-4.251338</td>
      <td>-2.285043</td>
      <td>-0.518519</td>
    </tr>
    <tr>
      <th>1991-05-16</th>
      <td>2.107300</td>
      <td>-3.313983</td>
      <td>-2.818965</td>
      <td>-1.051187</td>
    </tr>
    <tr>
      <th>1991-05-17</th>
      <td>2.924663</td>
      <td>-3.279024</td>
      <td>-3.416284</td>
      <td>-1.759418</td>
    </tr>
    <tr>
      <th>1991-05-18</th>
      <td>1.642640</td>
      <td>-3.449604</td>
      <td>-3.849884</td>
      <td>-3.256539</td>
    </tr>
    <tr>
      <th>1991-05-19</th>
      <td>0.339184</td>
      <td>-3.737476</td>
      <td>-2.584284</td>
      <td>-3.258609</td>
    </tr>
    <tr>
      <th>1991-05-20</th>
      <td>-0.088218</td>
      <td>-3.199582</td>
      <td>-0.793150</td>
      <td>-3.505362</td>
    </tr>
    <tr>
      <th>1991-05-21</th>
      <td>1.973667</td>
      <td>-2.846267</td>
      <td>-0.033273</td>
      <td>-3.574112</td>
    </tr>
    <tr>
      <th>1991-05-22</th>
      <td>1.203131</td>
      <td>-1.728314</td>
      <td>-0.256031</td>
      <td>-3.728567</td>
    </tr>
    <tr>
      <th>1991-05-23</th>
      <td>-0.001941</td>
      <td>-1.992424</td>
      <td>-0.785418</td>
      <td>-4.939580</td>
    </tr>
    <tr>
      <th>1991-05-24</th>
      <td>-0.183286</td>
      <td>-3.597339</td>
      <td>0.607105</td>
      <td>-4.848243</td>
    </tr>
    <tr>
      <th>1991-05-25</th>
      <td>0.921340</td>
      <td>-4.119241</td>
      <td>0.481826</td>
      <td>-4.543174</td>
    </tr>
    <tr>
      <th>1991-05-26</th>
      <td>-0.223030</td>
      <td>-2.955807</td>
      <td>0.181189</td>
      <td>-3.147607</td>
    </tr>
    <tr>
      <th>1991-05-27</th>
      <td>-1.484418</td>
      <td>-1.163546</td>
      <td>0.070039</td>
      <td>-3.416996</td>
    </tr>
    <tr>
      <th>1991-05-28</th>
      <td>0.238185</td>
      <td>-0.188891</td>
      <td>0.027534</td>
      <td>-1.971657</td>
    </tr>
    <tr>
      <th>1991-05-29</th>
      <td>2.451018</td>
      <td>-0.764264</td>
      <td>-0.251398</td>
      <td>-2.414153</td>
    </tr>
    <tr>
      <th>1991-05-30</th>
      <td>1.109700</td>
      <td>0.258144</td>
      <td>0.419718</td>
      <td>-1.922130</td>
    </tr>
    <tr>
      <th>1991-05-31</th>
      <td>1.702005</td>
      <td>0.865573</td>
      <td>0.051701</td>
      <td>-1.597195</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1993-12-27</th>
      <td>-11.718762</td>
      <td>49.063902</td>
      <td>3.474600</td>
      <td>6.574303</td>
    </tr>
    <tr>
      <th>1993-12-28</th>
      <td>-11.044536</td>
      <td>49.359737</td>
      <td>3.030406</td>
      <td>5.551352</td>
    </tr>
    <tr>
      <th>1993-12-29</th>
      <td>-9.812846</td>
      <td>50.601032</td>
      <td>5.279204</td>
      <td>6.713583</td>
    </tr>
    <tr>
      <th>1993-12-30</th>
      <td>-9.457126</td>
      <td>50.299535</td>
      <td>4.217385</td>
      <td>5.366581</td>
    </tr>
    <tr>
      <th>1993-12-31</th>
      <td>-9.557171</td>
      <td>50.748025</td>
      <td>4.044397</td>
      <td>4.954640</td>
    </tr>
    <tr>
      <th>1994-01-01</th>
      <td>-10.365432</td>
      <td>50.280650</td>
      <td>3.694675</td>
      <td>4.521792</td>
    </tr>
    <tr>
      <th>1994-01-02</th>
      <td>-9.765439</td>
      <td>49.542224</td>
      <td>3.349469</td>
      <td>5.128127</td>
    </tr>
    <tr>
      <th>1994-01-03</th>
      <td>-9.864352</td>
      <td>48.775752</td>
      <td>2.564792</td>
      <td>3.313989</td>
    </tr>
    <tr>
      <th>1994-01-04</th>
      <td>-8.906611</td>
      <td>47.734314</td>
      <td>1.729905</td>
      <td>3.202071</td>
    </tr>
    <tr>
      <th>1994-01-05</th>
      <td>-9.211413</td>
      <td>46.976784</td>
      <td>0.592811</td>
      <td>2.375301</td>
    </tr>
    <tr>
      <th>1994-01-06</th>
      <td>-10.061965</td>
      <td>45.792724</td>
      <td>0.847866</td>
      <td>3.056145</td>
    </tr>
    <tr>
      <th>1994-01-07</th>
      <td>-10.542277</td>
      <td>44.963831</td>
      <td>2.250362</td>
      <td>2.733240</td>
    </tr>
    <tr>
      <th>1994-01-08</th>
      <td>-10.307840</td>
      <td>44.566058</td>
      <td>4.379730</td>
      <td>2.239756</td>
    </tr>
    <tr>
      <th>1994-01-09</th>
      <td>-11.039269</td>
      <td>44.618482</td>
      <td>5.756896</td>
      <td>2.506342</td>
    </tr>
    <tr>
      <th>1994-01-10</th>
      <td>-11.079951</td>
      <td>42.661610</td>
      <td>5.532226</td>
      <td>3.287872</td>
    </tr>
    <tr>
      <th>1994-01-11</th>
      <td>-11.603723</td>
      <td>42.084827</td>
      <td>6.069568</td>
      <td>3.108065</td>
    </tr>
    <tr>
      <th>1994-01-12</th>
      <td>-11.866116</td>
      <td>41.977334</td>
      <td>4.500526</td>
      <td>5.058462</td>
    </tr>
    <tr>
      <th>1994-01-13</th>
      <td>-12.238669</td>
      <td>43.107664</td>
      <td>6.275452</td>
      <td>6.936477</td>
    </tr>
    <tr>
      <th>1994-01-14</th>
      <td>-13.174405</td>
      <td>43.449070</td>
      <td>6.238096</td>
      <td>5.330828</td>
    </tr>
    <tr>
      <th>1994-01-15</th>
      <td>-13.680208</td>
      <td>41.907504</td>
      <td>5.086942</td>
      <td>5.296978</td>
    </tr>
    <tr>
      <th>1994-01-16</th>
      <td>-13.555143</td>
      <td>41.480131</td>
      <td>4.878366</td>
      <td>5.657398</td>
    </tr>
    <tr>
      <th>1994-01-17</th>
      <td>-14.222899</td>
      <td>41.664088</td>
      <td>3.786109</td>
      <td>7.201883</td>
    </tr>
    <tr>
      <th>1994-01-18</th>
      <td>-14.694785</td>
      <td>42.835415</td>
      <td>3.981899</td>
      <td>6.807595</td>
    </tr>
    <tr>
      <th>1994-01-19</th>
      <td>-14.680860</td>
      <td>41.646727</td>
      <td>3.573631</td>
      <td>4.814641</td>
    </tr>
    <tr>
      <th>1994-01-20</th>
      <td>-13.971299</td>
      <td>43.068440</td>
      <td>3.211609</td>
      <td>3.701947</td>
    </tr>
    <tr>
      <th>1994-01-21</th>
      <td>-13.440162</td>
      <td>43.078396</td>
      <td>3.330063</td>
      <td>4.416731</td>
    </tr>
    <tr>
      <th>1994-01-22</th>
      <td>-14.076458</td>
      <td>44.682972</td>
      <td>2.318389</td>
      <td>4.027059</td>
    </tr>
    <tr>
      <th>1994-01-23</th>
      <td>-13.483685</td>
      <td>45.257832</td>
      <td>4.644607</td>
      <td>4.072586</td>
    </tr>
    <tr>
      <th>1994-01-24</th>
      <td>-12.465084</td>
      <td>44.996413</td>
      <td>2.710443</td>
      <td>5.470369</td>
    </tr>
    <tr>
      <th>1994-01-25</th>
      <td>-12.368782</td>
      <td>45.250128</td>
      <td>3.704472</td>
      <td>8.197593</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 4 columns</p>
</div>




```python
plt.figure(); df.plot(); plt.legend(loc='best')
```




    <matplotlib.legend.Legend at 0xa54d9b0>




    <matplotlib.figure.Figure at 0xa54dda0>



![png](pandas-try_files/pandas-try_167_2.png)



```python
df.to_csv('foo.csv')
```


```python
pd.read_csv('foo.csv')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1991-05-02</td>
      <td>-0.181150</td>
      <td>-0.957295</td>
      <td>-0.057522</td>
      <td>0.001560</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1991-05-03</td>
      <td>-0.465619</td>
      <td>-0.214507</td>
      <td>0.590033</td>
      <td>-0.414619</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1991-05-04</td>
      <td>0.051474</td>
      <td>-3.086479</td>
      <td>-0.663723</td>
      <td>-0.673200</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1991-05-05</td>
      <td>1.643569</td>
      <td>-3.680268</td>
      <td>-0.162659</td>
      <td>-0.736890</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1991-05-06</td>
      <td>1.124731</td>
      <td>-4.556386</td>
      <td>-1.000335</td>
      <td>-1.301676</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1991-05-07</td>
      <td>2.371863</td>
      <td>-5.108150</td>
      <td>0.051799</td>
      <td>-1.394831</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1991-05-08</td>
      <td>2.370961</td>
      <td>-5.869673</td>
      <td>0.489181</td>
      <td>-1.013639</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1991-05-09</td>
      <td>1.527966</td>
      <td>-5.380946</td>
      <td>1.252127</td>
      <td>-2.546389</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1991-05-10</td>
      <td>1.007503</td>
      <td>-5.600070</td>
      <td>0.794424</td>
      <td>-2.099694</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1991-05-11</td>
      <td>1.783891</td>
      <td>-4.004892</td>
      <td>-1.399713</td>
      <td>-2.840437</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1991-05-12</td>
      <td>0.544687</td>
      <td>-3.125823</td>
      <td>-2.216852</td>
      <td>-1.944226</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1991-05-13</td>
      <td>-0.623709</td>
      <td>-2.784225</td>
      <td>-1.087775</td>
      <td>-0.805274</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1991-05-14</td>
      <td>0.314683</td>
      <td>-2.612293</td>
      <td>-1.129332</td>
      <td>-0.821711</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1991-05-15</td>
      <td>0.185139</td>
      <td>-4.251338</td>
      <td>-2.285043</td>
      <td>-0.518519</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1991-05-16</td>
      <td>2.107300</td>
      <td>-3.313983</td>
      <td>-2.818965</td>
      <td>-1.051187</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1991-05-17</td>
      <td>2.924663</td>
      <td>-3.279024</td>
      <td>-3.416284</td>
      <td>-1.759418</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1991-05-18</td>
      <td>1.642640</td>
      <td>-3.449604</td>
      <td>-3.849884</td>
      <td>-3.256539</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1991-05-19</td>
      <td>0.339184</td>
      <td>-3.737476</td>
      <td>-2.584284</td>
      <td>-3.258609</td>
    </tr>
    <tr>
      <th>18</th>
      <td>1991-05-20</td>
      <td>-0.088218</td>
      <td>-3.199582</td>
      <td>-0.793150</td>
      <td>-3.505362</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1991-05-21</td>
      <td>1.973667</td>
      <td>-2.846267</td>
      <td>-0.033273</td>
      <td>-3.574112</td>
    </tr>
    <tr>
      <th>20</th>
      <td>1991-05-22</td>
      <td>1.203131</td>
      <td>-1.728314</td>
      <td>-0.256031</td>
      <td>-3.728567</td>
    </tr>
    <tr>
      <th>21</th>
      <td>1991-05-23</td>
      <td>-0.001941</td>
      <td>-1.992424</td>
      <td>-0.785418</td>
      <td>-4.939580</td>
    </tr>
    <tr>
      <th>22</th>
      <td>1991-05-24</td>
      <td>-0.183286</td>
      <td>-3.597339</td>
      <td>0.607105</td>
      <td>-4.848243</td>
    </tr>
    <tr>
      <th>23</th>
      <td>1991-05-25</td>
      <td>0.921340</td>
      <td>-4.119241</td>
      <td>0.481826</td>
      <td>-4.543174</td>
    </tr>
    <tr>
      <th>24</th>
      <td>1991-05-26</td>
      <td>-0.223030</td>
      <td>-2.955807</td>
      <td>0.181189</td>
      <td>-3.147607</td>
    </tr>
    <tr>
      <th>25</th>
      <td>1991-05-27</td>
      <td>-1.484418</td>
      <td>-1.163546</td>
      <td>0.070039</td>
      <td>-3.416996</td>
    </tr>
    <tr>
      <th>26</th>
      <td>1991-05-28</td>
      <td>0.238185</td>
      <td>-0.188891</td>
      <td>0.027534</td>
      <td>-1.971657</td>
    </tr>
    <tr>
      <th>27</th>
      <td>1991-05-29</td>
      <td>2.451018</td>
      <td>-0.764264</td>
      <td>-0.251398</td>
      <td>-2.414153</td>
    </tr>
    <tr>
      <th>28</th>
      <td>1991-05-30</td>
      <td>1.109700</td>
      <td>0.258144</td>
      <td>0.419718</td>
      <td>-1.922130</td>
    </tr>
    <tr>
      <th>29</th>
      <td>1991-05-31</td>
      <td>1.702005</td>
      <td>0.865573</td>
      <td>0.051701</td>
      <td>-1.597195</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>970</th>
      <td>1993-12-27</td>
      <td>-11.718762</td>
      <td>49.063902</td>
      <td>3.474600</td>
      <td>6.574303</td>
    </tr>
    <tr>
      <th>971</th>
      <td>1993-12-28</td>
      <td>-11.044536</td>
      <td>49.359737</td>
      <td>3.030406</td>
      <td>5.551352</td>
    </tr>
    <tr>
      <th>972</th>
      <td>1993-12-29</td>
      <td>-9.812846</td>
      <td>50.601032</td>
      <td>5.279204</td>
      <td>6.713583</td>
    </tr>
    <tr>
      <th>973</th>
      <td>1993-12-30</td>
      <td>-9.457126</td>
      <td>50.299535</td>
      <td>4.217385</td>
      <td>5.366581</td>
    </tr>
    <tr>
      <th>974</th>
      <td>1993-12-31</td>
      <td>-9.557171</td>
      <td>50.748025</td>
      <td>4.044397</td>
      <td>4.954640</td>
    </tr>
    <tr>
      <th>975</th>
      <td>1994-01-01</td>
      <td>-10.365432</td>
      <td>50.280650</td>
      <td>3.694675</td>
      <td>4.521792</td>
    </tr>
    <tr>
      <th>976</th>
      <td>1994-01-02</td>
      <td>-9.765439</td>
      <td>49.542224</td>
      <td>3.349469</td>
      <td>5.128127</td>
    </tr>
    <tr>
      <th>977</th>
      <td>1994-01-03</td>
      <td>-9.864352</td>
      <td>48.775752</td>
      <td>2.564792</td>
      <td>3.313989</td>
    </tr>
    <tr>
      <th>978</th>
      <td>1994-01-04</td>
      <td>-8.906611</td>
      <td>47.734314</td>
      <td>1.729905</td>
      <td>3.202071</td>
    </tr>
    <tr>
      <th>979</th>
      <td>1994-01-05</td>
      <td>-9.211413</td>
      <td>46.976784</td>
      <td>0.592811</td>
      <td>2.375301</td>
    </tr>
    <tr>
      <th>980</th>
      <td>1994-01-06</td>
      <td>-10.061965</td>
      <td>45.792724</td>
      <td>0.847866</td>
      <td>3.056145</td>
    </tr>
    <tr>
      <th>981</th>
      <td>1994-01-07</td>
      <td>-10.542277</td>
      <td>44.963831</td>
      <td>2.250362</td>
      <td>2.733240</td>
    </tr>
    <tr>
      <th>982</th>
      <td>1994-01-08</td>
      <td>-10.307840</td>
      <td>44.566058</td>
      <td>4.379730</td>
      <td>2.239756</td>
    </tr>
    <tr>
      <th>983</th>
      <td>1994-01-09</td>
      <td>-11.039269</td>
      <td>44.618482</td>
      <td>5.756896</td>
      <td>2.506342</td>
    </tr>
    <tr>
      <th>984</th>
      <td>1994-01-10</td>
      <td>-11.079951</td>
      <td>42.661610</td>
      <td>5.532226</td>
      <td>3.287872</td>
    </tr>
    <tr>
      <th>985</th>
      <td>1994-01-11</td>
      <td>-11.603723</td>
      <td>42.084827</td>
      <td>6.069568</td>
      <td>3.108065</td>
    </tr>
    <tr>
      <th>986</th>
      <td>1994-01-12</td>
      <td>-11.866116</td>
      <td>41.977334</td>
      <td>4.500526</td>
      <td>5.058462</td>
    </tr>
    <tr>
      <th>987</th>
      <td>1994-01-13</td>
      <td>-12.238669</td>
      <td>43.107664</td>
      <td>6.275452</td>
      <td>6.936477</td>
    </tr>
    <tr>
      <th>988</th>
      <td>1994-01-14</td>
      <td>-13.174405</td>
      <td>43.449070</td>
      <td>6.238096</td>
      <td>5.330828</td>
    </tr>
    <tr>
      <th>989</th>
      <td>1994-01-15</td>
      <td>-13.680208</td>
      <td>41.907504</td>
      <td>5.086942</td>
      <td>5.296978</td>
    </tr>
    <tr>
      <th>990</th>
      <td>1994-01-16</td>
      <td>-13.555143</td>
      <td>41.480131</td>
      <td>4.878366</td>
      <td>5.657398</td>
    </tr>
    <tr>
      <th>991</th>
      <td>1994-01-17</td>
      <td>-14.222899</td>
      <td>41.664088</td>
      <td>3.786109</td>
      <td>7.201883</td>
    </tr>
    <tr>
      <th>992</th>
      <td>1994-01-18</td>
      <td>-14.694785</td>
      <td>42.835415</td>
      <td>3.981899</td>
      <td>6.807595</td>
    </tr>
    <tr>
      <th>993</th>
      <td>1994-01-19</td>
      <td>-14.680860</td>
      <td>41.646727</td>
      <td>3.573631</td>
      <td>4.814641</td>
    </tr>
    <tr>
      <th>994</th>
      <td>1994-01-20</td>
      <td>-13.971299</td>
      <td>43.068440</td>
      <td>3.211609</td>
      <td>3.701947</td>
    </tr>
    <tr>
      <th>995</th>
      <td>1994-01-21</td>
      <td>-13.440162</td>
      <td>43.078396</td>
      <td>3.330063</td>
      <td>4.416731</td>
    </tr>
    <tr>
      <th>996</th>
      <td>1994-01-22</td>
      <td>-14.076458</td>
      <td>44.682972</td>
      <td>2.318389</td>
      <td>4.027059</td>
    </tr>
    <tr>
      <th>997</th>
      <td>1994-01-23</td>
      <td>-13.483685</td>
      <td>45.257832</td>
      <td>4.644607</td>
      <td>4.072586</td>
    </tr>
    <tr>
      <th>998</th>
      <td>1994-01-24</td>
      <td>-12.465084</td>
      <td>44.996413</td>
      <td>2.710443</td>
      <td>5.470369</td>
    </tr>
    <tr>
      <th>999</th>
      <td>1994-01-25</td>
      <td>-12.368782</td>
      <td>45.250128</td>
      <td>3.704472</td>
      <td>8.197593</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 5 columns</p>
</div>




```python
df.to_hdf('foo.h5','df')
```


```python
pd.read_hdf('foo.h5','df')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1991-05-02</th>
      <td>-0.181150</td>
      <td>-0.957295</td>
      <td>-0.057522</td>
      <td>0.001560</td>
    </tr>
    <tr>
      <th>1991-05-03</th>
      <td>-0.465619</td>
      <td>-0.214507</td>
      <td>0.590033</td>
      <td>-0.414619</td>
    </tr>
    <tr>
      <th>1991-05-04</th>
      <td>0.051474</td>
      <td>-3.086479</td>
      <td>-0.663723</td>
      <td>-0.673200</td>
    </tr>
    <tr>
      <th>1991-05-05</th>
      <td>1.643569</td>
      <td>-3.680268</td>
      <td>-0.162659</td>
      <td>-0.736890</td>
    </tr>
    <tr>
      <th>1991-05-06</th>
      <td>1.124731</td>
      <td>-4.556386</td>
      <td>-1.000335</td>
      <td>-1.301676</td>
    </tr>
    <tr>
      <th>1991-05-07</th>
      <td>2.371863</td>
      <td>-5.108150</td>
      <td>0.051799</td>
      <td>-1.394831</td>
    </tr>
    <tr>
      <th>1991-05-08</th>
      <td>2.370961</td>
      <td>-5.869673</td>
      <td>0.489181</td>
      <td>-1.013639</td>
    </tr>
    <tr>
      <th>1991-05-09</th>
      <td>1.527966</td>
      <td>-5.380946</td>
      <td>1.252127</td>
      <td>-2.546389</td>
    </tr>
    <tr>
      <th>1991-05-10</th>
      <td>1.007503</td>
      <td>-5.600070</td>
      <td>0.794424</td>
      <td>-2.099694</td>
    </tr>
    <tr>
      <th>1991-05-11</th>
      <td>1.783891</td>
      <td>-4.004892</td>
      <td>-1.399713</td>
      <td>-2.840437</td>
    </tr>
    <tr>
      <th>1991-05-12</th>
      <td>0.544687</td>
      <td>-3.125823</td>
      <td>-2.216852</td>
      <td>-1.944226</td>
    </tr>
    <tr>
      <th>1991-05-13</th>
      <td>-0.623709</td>
      <td>-2.784225</td>
      <td>-1.087775</td>
      <td>-0.805274</td>
    </tr>
    <tr>
      <th>1991-05-14</th>
      <td>0.314683</td>
      <td>-2.612293</td>
      <td>-1.129332</td>
      <td>-0.821711</td>
    </tr>
    <tr>
      <th>1991-05-15</th>
      <td>0.185139</td>
      <td>-4.251338</td>
      <td>-2.285043</td>
      <td>-0.518519</td>
    </tr>
    <tr>
      <th>1991-05-16</th>
      <td>2.107300</td>
      <td>-3.313983</td>
      <td>-2.818965</td>
      <td>-1.051187</td>
    </tr>
    <tr>
      <th>1991-05-17</th>
      <td>2.924663</td>
      <td>-3.279024</td>
      <td>-3.416284</td>
      <td>-1.759418</td>
    </tr>
    <tr>
      <th>1991-05-18</th>
      <td>1.642640</td>
      <td>-3.449604</td>
      <td>-3.849884</td>
      <td>-3.256539</td>
    </tr>
    <tr>
      <th>1991-05-19</th>
      <td>0.339184</td>
      <td>-3.737476</td>
      <td>-2.584284</td>
      <td>-3.258609</td>
    </tr>
    <tr>
      <th>1991-05-20</th>
      <td>-0.088218</td>
      <td>-3.199582</td>
      <td>-0.793150</td>
      <td>-3.505362</td>
    </tr>
    <tr>
      <th>1991-05-21</th>
      <td>1.973667</td>
      <td>-2.846267</td>
      <td>-0.033273</td>
      <td>-3.574112</td>
    </tr>
    <tr>
      <th>1991-05-22</th>
      <td>1.203131</td>
      <td>-1.728314</td>
      <td>-0.256031</td>
      <td>-3.728567</td>
    </tr>
    <tr>
      <th>1991-05-23</th>
      <td>-0.001941</td>
      <td>-1.992424</td>
      <td>-0.785418</td>
      <td>-4.939580</td>
    </tr>
    <tr>
      <th>1991-05-24</th>
      <td>-0.183286</td>
      <td>-3.597339</td>
      <td>0.607105</td>
      <td>-4.848243</td>
    </tr>
    <tr>
      <th>1991-05-25</th>
      <td>0.921340</td>
      <td>-4.119241</td>
      <td>0.481826</td>
      <td>-4.543174</td>
    </tr>
    <tr>
      <th>1991-05-26</th>
      <td>-0.223030</td>
      <td>-2.955807</td>
      <td>0.181189</td>
      <td>-3.147607</td>
    </tr>
    <tr>
      <th>1991-05-27</th>
      <td>-1.484418</td>
      <td>-1.163546</td>
      <td>0.070039</td>
      <td>-3.416996</td>
    </tr>
    <tr>
      <th>1991-05-28</th>
      <td>0.238185</td>
      <td>-0.188891</td>
      <td>0.027534</td>
      <td>-1.971657</td>
    </tr>
    <tr>
      <th>1991-05-29</th>
      <td>2.451018</td>
      <td>-0.764264</td>
      <td>-0.251398</td>
      <td>-2.414153</td>
    </tr>
    <tr>
      <th>1991-05-30</th>
      <td>1.109700</td>
      <td>0.258144</td>
      <td>0.419718</td>
      <td>-1.922130</td>
    </tr>
    <tr>
      <th>1991-05-31</th>
      <td>1.702005</td>
      <td>0.865573</td>
      <td>0.051701</td>
      <td>-1.597195</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1993-12-27</th>
      <td>-11.718762</td>
      <td>49.063902</td>
      <td>3.474600</td>
      <td>6.574303</td>
    </tr>
    <tr>
      <th>1993-12-28</th>
      <td>-11.044536</td>
      <td>49.359737</td>
      <td>3.030406</td>
      <td>5.551352</td>
    </tr>
    <tr>
      <th>1993-12-29</th>
      <td>-9.812846</td>
      <td>50.601032</td>
      <td>5.279204</td>
      <td>6.713583</td>
    </tr>
    <tr>
      <th>1993-12-30</th>
      <td>-9.457126</td>
      <td>50.299535</td>
      <td>4.217385</td>
      <td>5.366581</td>
    </tr>
    <tr>
      <th>1993-12-31</th>
      <td>-9.557171</td>
      <td>50.748025</td>
      <td>4.044397</td>
      <td>4.954640</td>
    </tr>
    <tr>
      <th>1994-01-01</th>
      <td>-10.365432</td>
      <td>50.280650</td>
      <td>3.694675</td>
      <td>4.521792</td>
    </tr>
    <tr>
      <th>1994-01-02</th>
      <td>-9.765439</td>
      <td>49.542224</td>
      <td>3.349469</td>
      <td>5.128127</td>
    </tr>
    <tr>
      <th>1994-01-03</th>
      <td>-9.864352</td>
      <td>48.775752</td>
      <td>2.564792</td>
      <td>3.313989</td>
    </tr>
    <tr>
      <th>1994-01-04</th>
      <td>-8.906611</td>
      <td>47.734314</td>
      <td>1.729905</td>
      <td>3.202071</td>
    </tr>
    <tr>
      <th>1994-01-05</th>
      <td>-9.211413</td>
      <td>46.976784</td>
      <td>0.592811</td>
      <td>2.375301</td>
    </tr>
    <tr>
      <th>1994-01-06</th>
      <td>-10.061965</td>
      <td>45.792724</td>
      <td>0.847866</td>
      <td>3.056145</td>
    </tr>
    <tr>
      <th>1994-01-07</th>
      <td>-10.542277</td>
      <td>44.963831</td>
      <td>2.250362</td>
      <td>2.733240</td>
    </tr>
    <tr>
      <th>1994-01-08</th>
      <td>-10.307840</td>
      <td>44.566058</td>
      <td>4.379730</td>
      <td>2.239756</td>
    </tr>
    <tr>
      <th>1994-01-09</th>
      <td>-11.039269</td>
      <td>44.618482</td>
      <td>5.756896</td>
      <td>2.506342</td>
    </tr>
    <tr>
      <th>1994-01-10</th>
      <td>-11.079951</td>
      <td>42.661610</td>
      <td>5.532226</td>
      <td>3.287872</td>
    </tr>
    <tr>
      <th>1994-01-11</th>
      <td>-11.603723</td>
      <td>42.084827</td>
      <td>6.069568</td>
      <td>3.108065</td>
    </tr>
    <tr>
      <th>1994-01-12</th>
      <td>-11.866116</td>
      <td>41.977334</td>
      <td>4.500526</td>
      <td>5.058462</td>
    </tr>
    <tr>
      <th>1994-01-13</th>
      <td>-12.238669</td>
      <td>43.107664</td>
      <td>6.275452</td>
      <td>6.936477</td>
    </tr>
    <tr>
      <th>1994-01-14</th>
      <td>-13.174405</td>
      <td>43.449070</td>
      <td>6.238096</td>
      <td>5.330828</td>
    </tr>
    <tr>
      <th>1994-01-15</th>
      <td>-13.680208</td>
      <td>41.907504</td>
      <td>5.086942</td>
      <td>5.296978</td>
    </tr>
    <tr>
      <th>1994-01-16</th>
      <td>-13.555143</td>
      <td>41.480131</td>
      <td>4.878366</td>
      <td>5.657398</td>
    </tr>
    <tr>
      <th>1994-01-17</th>
      <td>-14.222899</td>
      <td>41.664088</td>
      <td>3.786109</td>
      <td>7.201883</td>
    </tr>
    <tr>
      <th>1994-01-18</th>
      <td>-14.694785</td>
      <td>42.835415</td>
      <td>3.981899</td>
      <td>6.807595</td>
    </tr>
    <tr>
      <th>1994-01-19</th>
      <td>-14.680860</td>
      <td>41.646727</td>
      <td>3.573631</td>
      <td>4.814641</td>
    </tr>
    <tr>
      <th>1994-01-20</th>
      <td>-13.971299</td>
      <td>43.068440</td>
      <td>3.211609</td>
      <td>3.701947</td>
    </tr>
    <tr>
      <th>1994-01-21</th>
      <td>-13.440162</td>
      <td>43.078396</td>
      <td>3.330063</td>
      <td>4.416731</td>
    </tr>
    <tr>
      <th>1994-01-22</th>
      <td>-14.076458</td>
      <td>44.682972</td>
      <td>2.318389</td>
      <td>4.027059</td>
    </tr>
    <tr>
      <th>1994-01-23</th>
      <td>-13.483685</td>
      <td>45.257832</td>
      <td>4.644607</td>
      <td>4.072586</td>
    </tr>
    <tr>
      <th>1994-01-24</th>
      <td>-12.465084</td>
      <td>44.996413</td>
      <td>2.710443</td>
      <td>5.470369</td>
    </tr>
    <tr>
      <th>1994-01-25</th>
      <td>-12.368782</td>
      <td>45.250128</td>
      <td>3.704472</td>
      <td>8.197593</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 4 columns</p>
</div>




```python
df.to_excel('foo.xlsx', sheet_name='Sheet1')
```


```python
pd.read_excel('foo.xlsx', 'Sheet1', index_col=None, na_values=['NA'])
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1991-05-02</th>
      <td>-0.181150</td>
      <td>-0.957295</td>
      <td>-0.057522</td>
      <td>0.001560</td>
    </tr>
    <tr>
      <th>1991-05-03</th>
      <td>-0.465619</td>
      <td>-0.214507</td>
      <td>0.590033</td>
      <td>-0.414619</td>
    </tr>
    <tr>
      <th>1991-05-04</th>
      <td>0.051474</td>
      <td>-3.086479</td>
      <td>-0.663723</td>
      <td>-0.673200</td>
    </tr>
    <tr>
      <th>1991-05-05</th>
      <td>1.643569</td>
      <td>-3.680268</td>
      <td>-0.162659</td>
      <td>-0.736890</td>
    </tr>
    <tr>
      <th>1991-05-06</th>
      <td>1.124731</td>
      <td>-4.556386</td>
      <td>-1.000335</td>
      <td>-1.301676</td>
    </tr>
    <tr>
      <th>1991-05-07</th>
      <td>2.371863</td>
      <td>-5.108150</td>
      <td>0.051799</td>
      <td>-1.394831</td>
    </tr>
    <tr>
      <th>1991-05-08</th>
      <td>2.370961</td>
      <td>-5.869673</td>
      <td>0.489181</td>
      <td>-1.013639</td>
    </tr>
    <tr>
      <th>1991-05-09</th>
      <td>1.527966</td>
      <td>-5.380946</td>
      <td>1.252127</td>
      <td>-2.546389</td>
    </tr>
    <tr>
      <th>1991-05-10</th>
      <td>1.007503</td>
      <td>-5.600070</td>
      <td>0.794424</td>
      <td>-2.099694</td>
    </tr>
    <tr>
      <th>1991-05-11</th>
      <td>1.783891</td>
      <td>-4.004892</td>
      <td>-1.399713</td>
      <td>-2.840437</td>
    </tr>
    <tr>
      <th>1991-05-12</th>
      <td>0.544687</td>
      <td>-3.125823</td>
      <td>-2.216852</td>
      <td>-1.944226</td>
    </tr>
    <tr>
      <th>1991-05-13</th>
      <td>-0.623709</td>
      <td>-2.784225</td>
      <td>-1.087775</td>
      <td>-0.805274</td>
    </tr>
    <tr>
      <th>1991-05-14</th>
      <td>0.314683</td>
      <td>-2.612293</td>
      <td>-1.129332</td>
      <td>-0.821711</td>
    </tr>
    <tr>
      <th>1991-05-15</th>
      <td>0.185139</td>
      <td>-4.251338</td>
      <td>-2.285043</td>
      <td>-0.518519</td>
    </tr>
    <tr>
      <th>1991-05-16</th>
      <td>2.107300</td>
      <td>-3.313983</td>
      <td>-2.818965</td>
      <td>-1.051187</td>
    </tr>
    <tr>
      <th>1991-05-17</th>
      <td>2.924663</td>
      <td>-3.279024</td>
      <td>-3.416284</td>
      <td>-1.759418</td>
    </tr>
    <tr>
      <th>1991-05-18</th>
      <td>1.642640</td>
      <td>-3.449604</td>
      <td>-3.849884</td>
      <td>-3.256539</td>
    </tr>
    <tr>
      <th>1991-05-19</th>
      <td>0.339184</td>
      <td>-3.737476</td>
      <td>-2.584284</td>
      <td>-3.258609</td>
    </tr>
    <tr>
      <th>1991-05-20</th>
      <td>-0.088218</td>
      <td>-3.199582</td>
      <td>-0.793150</td>
      <td>-3.505362</td>
    </tr>
    <tr>
      <th>1991-05-21</th>
      <td>1.973667</td>
      <td>-2.846267</td>
      <td>-0.033273</td>
      <td>-3.574112</td>
    </tr>
    <tr>
      <th>1991-05-22</th>
      <td>1.203131</td>
      <td>-1.728314</td>
      <td>-0.256031</td>
      <td>-3.728567</td>
    </tr>
    <tr>
      <th>1991-05-23</th>
      <td>-0.001941</td>
      <td>-1.992424</td>
      <td>-0.785418</td>
      <td>-4.939580</td>
    </tr>
    <tr>
      <th>1991-05-24</th>
      <td>-0.183286</td>
      <td>-3.597339</td>
      <td>0.607105</td>
      <td>-4.848243</td>
    </tr>
    <tr>
      <th>1991-05-25</th>
      <td>0.921340</td>
      <td>-4.119241</td>
      <td>0.481826</td>
      <td>-4.543174</td>
    </tr>
    <tr>
      <th>1991-05-26</th>
      <td>-0.223030</td>
      <td>-2.955807</td>
      <td>0.181189</td>
      <td>-3.147607</td>
    </tr>
    <tr>
      <th>1991-05-27</th>
      <td>-1.484418</td>
      <td>-1.163546</td>
      <td>0.070039</td>
      <td>-3.416996</td>
    </tr>
    <tr>
      <th>1991-05-28</th>
      <td>0.238185</td>
      <td>-0.188891</td>
      <td>0.027534</td>
      <td>-1.971657</td>
    </tr>
    <tr>
      <th>1991-05-29</th>
      <td>2.451018</td>
      <td>-0.764264</td>
      <td>-0.251398</td>
      <td>-2.414153</td>
    </tr>
    <tr>
      <th>1991-05-30</th>
      <td>1.109700</td>
      <td>0.258144</td>
      <td>0.419718</td>
      <td>-1.922130</td>
    </tr>
    <tr>
      <th>1991-05-31</th>
      <td>1.702005</td>
      <td>0.865573</td>
      <td>0.051701</td>
      <td>-1.597195</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1993-12-27</th>
      <td>-11.718762</td>
      <td>49.063902</td>
      <td>3.474600</td>
      <td>6.574303</td>
    </tr>
    <tr>
      <th>1993-12-28</th>
      <td>-11.044536</td>
      <td>49.359737</td>
      <td>3.030406</td>
      <td>5.551352</td>
    </tr>
    <tr>
      <th>1993-12-29</th>
      <td>-9.812846</td>
      <td>50.601032</td>
      <td>5.279204</td>
      <td>6.713583</td>
    </tr>
    <tr>
      <th>1993-12-30</th>
      <td>-9.457126</td>
      <td>50.299535</td>
      <td>4.217385</td>
      <td>5.366581</td>
    </tr>
    <tr>
      <th>1993-12-31</th>
      <td>-9.557171</td>
      <td>50.748025</td>
      <td>4.044397</td>
      <td>4.954640</td>
    </tr>
    <tr>
      <th>1994-01-01</th>
      <td>-10.365432</td>
      <td>50.280650</td>
      <td>3.694675</td>
      <td>4.521792</td>
    </tr>
    <tr>
      <th>1994-01-02</th>
      <td>-9.765439</td>
      <td>49.542224</td>
      <td>3.349469</td>
      <td>5.128127</td>
    </tr>
    <tr>
      <th>1994-01-03</th>
      <td>-9.864352</td>
      <td>48.775752</td>
      <td>2.564792</td>
      <td>3.313989</td>
    </tr>
    <tr>
      <th>1994-01-04</th>
      <td>-8.906611</td>
      <td>47.734314</td>
      <td>1.729905</td>
      <td>3.202071</td>
    </tr>
    <tr>
      <th>1994-01-05</th>
      <td>-9.211413</td>
      <td>46.976784</td>
      <td>0.592811</td>
      <td>2.375301</td>
    </tr>
    <tr>
      <th>1994-01-06</th>
      <td>-10.061965</td>
      <td>45.792724</td>
      <td>0.847866</td>
      <td>3.056145</td>
    </tr>
    <tr>
      <th>1994-01-07</th>
      <td>-10.542277</td>
      <td>44.963831</td>
      <td>2.250362</td>
      <td>2.733240</td>
    </tr>
    <tr>
      <th>1994-01-08</th>
      <td>-10.307840</td>
      <td>44.566058</td>
      <td>4.379730</td>
      <td>2.239756</td>
    </tr>
    <tr>
      <th>1994-01-09</th>
      <td>-11.039269</td>
      <td>44.618482</td>
      <td>5.756896</td>
      <td>2.506342</td>
    </tr>
    <tr>
      <th>1994-01-10</th>
      <td>-11.079951</td>
      <td>42.661610</td>
      <td>5.532226</td>
      <td>3.287872</td>
    </tr>
    <tr>
      <th>1994-01-11</th>
      <td>-11.603723</td>
      <td>42.084827</td>
      <td>6.069568</td>
      <td>3.108065</td>
    </tr>
    <tr>
      <th>1994-01-12</th>
      <td>-11.866116</td>
      <td>41.977334</td>
      <td>4.500526</td>
      <td>5.058462</td>
    </tr>
    <tr>
      <th>1994-01-13</th>
      <td>-12.238669</td>
      <td>43.107664</td>
      <td>6.275452</td>
      <td>6.936477</td>
    </tr>
    <tr>
      <th>1994-01-14</th>
      <td>-13.174405</td>
      <td>43.449070</td>
      <td>6.238096</td>
      <td>5.330828</td>
    </tr>
    <tr>
      <th>1994-01-15</th>
      <td>-13.680208</td>
      <td>41.907504</td>
      <td>5.086942</td>
      <td>5.296978</td>
    </tr>
    <tr>
      <th>1994-01-16</th>
      <td>-13.555143</td>
      <td>41.480131</td>
      <td>4.878366</td>
      <td>5.657398</td>
    </tr>
    <tr>
      <th>1994-01-17</th>
      <td>-14.222899</td>
      <td>41.664088</td>
      <td>3.786109</td>
      <td>7.201883</td>
    </tr>
    <tr>
      <th>1994-01-18</th>
      <td>-14.694785</td>
      <td>42.835415</td>
      <td>3.981899</td>
      <td>6.807595</td>
    </tr>
    <tr>
      <th>1994-01-19</th>
      <td>-14.680860</td>
      <td>41.646727</td>
      <td>3.573631</td>
      <td>4.814641</td>
    </tr>
    <tr>
      <th>1994-01-20</th>
      <td>-13.971299</td>
      <td>43.068440</td>
      <td>3.211609</td>
      <td>3.701947</td>
    </tr>
    <tr>
      <th>1994-01-21</th>
      <td>-13.440162</td>
      <td>43.078396</td>
      <td>3.330063</td>
      <td>4.416731</td>
    </tr>
    <tr>
      <th>1994-01-22</th>
      <td>-14.076458</td>
      <td>44.682972</td>
      <td>2.318389</td>
      <td>4.027059</td>
    </tr>
    <tr>
      <th>1994-01-23</th>
      <td>-13.483685</td>
      <td>45.257832</td>
      <td>4.644607</td>
      <td>4.072586</td>
    </tr>
    <tr>
      <th>1994-01-24</th>
      <td>-12.465084</td>
      <td>44.996413</td>
      <td>2.710443</td>
      <td>5.470369</td>
    </tr>
    <tr>
      <th>1994-01-25</th>
      <td>-12.368782</td>
      <td>45.250128</td>
      <td>3.704472</td>
      <td>8.197593</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 4 columns</p>
</div>




```python

```



