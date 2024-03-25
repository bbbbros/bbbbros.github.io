# Chapter 1. DataFrame 살펴보기 

# __1. DataFrame이 뭔가요?__

>  - DataFrame은 2차원(col과 row을 가짐)테이블 데이터 구조를 가지는 자료형
>  - Data Analysis, Machine Learning에서 data 변형을 위해 가장 많이 사용
>  - **주의** : Series나 DataFrame은 대소문자가 구분되므로 Series, DataFrame으로 사용


```python
# pandas import
import pandas as pd
import numpy as np
```

### <b>1-1. DataFrame 만들어 보기</b>

> Dictionary 형으로 생성 


```python
a1 = pd.DataFrame({"a" : [1,2,3], "b" : [4,5,6], "c" : [7,8,9]})
a1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>4</td>
      <td>7</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>5</td>
      <td>8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>6</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>



>  List 형태로 데이터 프레임 생성


```python
#a2 = pd.DataFrame([[1,2,3], [4,5,6], [7,8,9]], ["a","b","c"])
a2 = pd.DataFrame([[1,2,3], [4,5,6], [7,8,9]], columns = ["a","b","c"])
#a2.DataFrame(columns = ["a","b","c"])
#a2.columns("a","b","c")
a2.rename(index={0:100},columns = {"a":"A", "b":"B"}, inplace=True)
a2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>c</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>100</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7</td>
      <td>8</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>



### <b>1-2. 파일을 읽어서 DataFrame생성하기</b>
> - pandas.read_csv 함수 사용
>  - 대부분의 업무에서는 분석하고자 하는 Datat가 존재할 것
>  - 이를 읽어 들이는 것부터 데이터 분석의 시작!
>  - 이번 실습에서 읽을 파일 : sc_cust_info_txn_v1.5.csv


```python
# kt 데이터 파일을 활용
# 파일을 수정하고 저장 자체를 MS Office에서 하여서 encoding을 cp949로 해주어야 함
cust = pd.read_csv('./sc_cust_info_txn_v1.5.csv', encoding = "cp949")
cust
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>28</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>2640.0000</td>
      <td>792.000000</td>
      <td>1584.0000</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>1</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>300.0000</td>
      <td>90.000000</td>
      <td>180.0000</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>2</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>E</td>
      <td>F</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.0000</td>
      <td>2526.000000</td>
      <td>6983.0000</td>
      <td>0.0</td>
      <td>6981.0000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>3</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>F</td>
      <td>F</td>
      <td>32</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>15544.7334</td>
      <td>2331.710010</td>
      <td>6750.4666</td>
      <td>0.0</td>
      <td>6508.8000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>4</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>D</td>
      <td>M</td>
      <td>18</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>4700.0000</td>
      <td>0.000000</td>
      <td>4502.0000</td>
      <td>0.0</td>
      <td>4507.7000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>9925</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>15</td>
      <td>1</td>
      <td>N</td>
      <td>Y</td>
      <td>1296.0999</td>
      <td>194.414985</td>
      <td>643.1001</td>
      <td>0.0</td>
      <td>852.5499</td>
      <td>N</td>
    </tr>
    <tr>
      <th>9926</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>G</td>
      <td>M</td>
      <td>12</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>13799.6666</td>
      <td>2069.949990</td>
      <td>10605.9266</td>
      <td>0.0</td>
      <td>10603.9266</td>
      <td>N</td>
    </tr>
    <tr>
      <th>9927</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10005</td>
      <td>C</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>1396.2000</td>
      <td>1206.000000</td>
      <td>0.0000</td>
      <td>1212.0</td>
      <td>0.0000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>9928</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>40</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>3140.0000</td>
      <td>942.000000</td>
      <td>1884.0000</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>9929</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>59</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>2436.9000</td>
      <td>365.535000</td>
      <td>1839.9000</td>
      <td>0.0</td>
      <td>1919.7999</td>
      <td>N</td>
    </tr>
  </tbody>
</table>
<p>9930 rows × 15 columns</p>
</div>



- DataFrame 데이터 살펴보기
>DataFrame의 구조 (인덱스와 컬럼)
 - 인덱스(Index) : 행의 레이블에 대한 정보를 보유하고 있음
 - 컬럼(Columns) : 열의 레이블에 대한 정보를 보유하고 있음
 - 인덱스와 컬럼 자체는 중복값일 수 없음

### <b>1-3. 데이터 살펴보기</b>
- head, tail 함수사용하기
> - 데이터 전체가 아닌, 일부(처음부터, 혹은 마지막부터)를 간단히 보기 위한 함수 (default: 5줄)
 - **head, tail을 왜 사용할까?**
   - 광대한 데이터를 다룰 수 있는 Pandas의 특성상 특정변수에 제대로 데이터가 들어갔는지 간략히 확인
   - 데이터 자료형의 확인
   - 각 레이블에 맞는 데이터 매칭 확인


```python
# 상위 3개
cust.head(n=3)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>28</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>2640.0</td>
      <td>792.0</td>
      <td>1584.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>1</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>300.0</td>
      <td>90.0</td>
      <td>180.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>2</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>E</td>
      <td>F</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.0</td>
      <td>2526.0</td>
      <td>6983.0</td>
      <td>0.0</td>
      <td>6981.0</td>
      <td>N</td>
    </tr>
  </tbody>
</table>
</div>




```python
#하위 10개 
cust.tail(n=10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>9920</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>D</td>
      <td>M</td>
      <td>46</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>6920.0000</td>
      <td>2076.000000</td>
      <td>4152.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>9921</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>D</td>
      <td>M</td>
      <td>54</td>
      <td>1</td>
      <td>N</td>
      <td>Y</td>
      <td>5198.0666</td>
      <td>0.000000</td>
      <td>4760.8666</td>
      <td>0.0000</td>
      <td>4749.3000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>9922</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>E</td>
      <td>M</td>
      <td>65</td>
      <td>4</td>
      <td>N</td>
      <td>N</td>
      <td>9115.1334</td>
      <td>3209.600000</td>
      <td>0.0000</td>
      <td>3523.7334</td>
      <td>0.0000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>9923</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>M</td>
      <td>76</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>1860.0000</td>
      <td>1716.000000</td>
      <td>0.0000</td>
      <td>1722.0000</td>
      <td>0.0000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>9924</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10005</td>
      <td>C</td>
      <td>_</td>
      <td>_</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>17038.2000</td>
      <td>5111.460000</td>
      <td>10222.9200</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>9925</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>15</td>
      <td>1</td>
      <td>N</td>
      <td>Y</td>
      <td>1296.0999</td>
      <td>194.414985</td>
      <td>643.1001</td>
      <td>0.0000</td>
      <td>852.5499</td>
      <td>N</td>
    </tr>
    <tr>
      <th>9926</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>G</td>
      <td>M</td>
      <td>12</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>13799.6666</td>
      <td>2069.949990</td>
      <td>10605.9266</td>
      <td>0.0000</td>
      <td>10603.9266</td>
      <td>N</td>
    </tr>
    <tr>
      <th>9927</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10005</td>
      <td>C</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>1396.2000</td>
      <td>1206.000000</td>
      <td>0.0000</td>
      <td>1212.0000</td>
      <td>0.0000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>9928</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>40</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>3140.0000</td>
      <td>942.000000</td>
      <td>1884.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>9929</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>59</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>2436.9000</td>
      <td>365.535000</td>
      <td>1839.9000</td>
      <td>0.0000</td>
      <td>1919.7999</td>
      <td>N</td>
    </tr>
  </tbody>
</table>
</div>



- DataFrame 기본 함수로 살펴보기
> - **shape :** 속성 반환값은 튜플로 존재하며 row과 col의 개수를 튜플로 반환함(row,col순)
  - columns : 해당 DataFrame을 구성하는 컬럼명을 확인할 수 있음
  - **info**  : 데이터 타입, 각 아이템의 개수 등 출력
  - describe : 데이터 컬럼별 요약 통계량을 나타냄, 숫자형 데이터의 통계치 계산
            (count:데이터의 갯수 / mean:평균값 / std:표준편차 / min:최소값 / 4분위 수 / max:최대값) 
  - dtypes : 데이터 형태의 종류(Data Types)


```python
# shape : 데이터를 파악하는데 중요함
cust.shape
```




    (9930, 15)




```python
# DataFrame의 columns들을 보여줌
cust.columns
```




    Index(['base_ym', 'dpro_tgt_perd_val', 'cust_ctg_type', 'cust_class',
           'sex_type', 'age', 'efct_svc_count', 'dt_stop_yn', 'npay_yn',
           'r3m_avg_bill_amt', 'r3m_A_avg_arpu_amt', 'r3m_B_avg_arpu_amt',
           'r6m_A_avg_arpu_amt', 'r6m_B_avg_arpu_amt', 'termination_yn'],
          dtype='object')




```python
# 데이터 타입 및 각 아이템등의 정보를 보여줌
cust.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 9930 entries, 0 to 9929
    Data columns (total 15 columns):
     #   Column              Non-Null Count  Dtype  
    ---  ------              --------------  -----  
     0   base_ym             9930 non-null   int64  
     1   dpro_tgt_perd_val   9930 non-null   int64  
     2   cust_ctg_type       9930 non-null   int64  
     3   cust_class          9930 non-null   object 
     4   sex_type            9930 non-null   object 
     5   age                 9930 non-null   object 
     6   efct_svc_count      9930 non-null   int64  
     7   dt_stop_yn          9930 non-null   object 
     8   npay_yn             9930 non-null   object 
     9   r3m_avg_bill_amt    9930 non-null   float64
     10  r3m_A_avg_arpu_amt  9930 non-null   float64
     11  r3m_B_avg_arpu_amt  9930 non-null   float64
     12  r6m_A_avg_arpu_amt  9930 non-null   float64
     13  r6m_B_avg_arpu_amt  9930 non-null   float64
     14  termination_yn      9930 non-null   object 
    dtypes: float64(5), int64(4), object(6)
    memory usage: 1.1+ MB



```python
# DataFrame의 기본적인 통계정보를 보여줌 (int float등 산술계산이 가능항 columns에 대해서)
cust.describe()

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>efct_svc_count</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>9930.0</td>
      <td>9930.0</td>
      <td>9930.000000</td>
      <td>9930.000000</td>
      <td>9.930000e+03</td>
      <td>9.930000e+03</td>
      <td>9.930000e+03</td>
      <td>9.930000e+03</td>
      <td>9930.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.372810</td>
      <td>1.520040</td>
      <td>1.181774e+04</td>
      <td>1.897536e+03</td>
      <td>6.395259e+03</td>
      <td>8.496206e+02</td>
      <td>4624.897630</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.605016</td>
      <td>15.404037</td>
      <td>1.397822e+05</td>
      <td>1.235342e+04</td>
      <td>8.346138e+04</td>
      <td>1.235124e+04</td>
      <td>4561.049131</td>
    </tr>
    <tr>
      <th>min</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.000000</td>
      <td>0.000000</td>
      <td>0.000000e+00</td>
      <td>0.000000e+00</td>
      <td>0.000000e+00</td>
      <td>0.000000e+00</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.000000</td>
      <td>1.000000</td>
      <td>3.624503e+03</td>
      <td>3.240000e+02</td>
      <td>1.260000e+03</td>
      <td>0.000000e+00</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.000000</td>
      <td>1.000000</td>
      <td>8.284467e+03</td>
      <td>1.593307e+03</td>
      <td>4.768617e+03</td>
      <td>0.000000e+00</td>
      <td>3959.316700</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.000000</td>
      <td>1.000000</td>
      <td>1.372000e+04</td>
      <td>2.308360e+03</td>
      <td>7.982000e+03</td>
      <td>1.006125e+03</td>
      <td>7741.006900</td>
    </tr>
    <tr>
      <th>max</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10010.000000</td>
      <td>905.000000</td>
      <td>1.281568e+07</td>
      <td>1.188998e+06</td>
      <td>7.689409e+06</td>
      <td>1.208498e+06</td>
      <td>64947.092000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# DataFrame의 데이터 종류
#cust.values
#cust.index
cust.name = '***고객정보****'
cust.index.name = '순번'
cust.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 9930 entries, 0 to 9929
    Data columns (total 15 columns):
     #   Column              Non-Null Count  Dtype  
    ---  ------              --------------  -----  
     0   base_ym             9930 non-null   int64  
     1   dpro_tgt_perd_val   9930 non-null   int64  
     2   cust_ctg_type       9930 non-null   int64  
     3   cust_class          9930 non-null   object 
     4   sex_type            9930 non-null   object 
     5   age                 9930 non-null   object 
     6   efct_svc_count      9930 non-null   int64  
     7   dt_stop_yn          9930 non-null   object 
     8   npay_yn             9930 non-null   object 
     9   r3m_avg_bill_amt    9930 non-null   float64
     10  r3m_A_avg_arpu_amt  9930 non-null   float64
     11  r3m_B_avg_arpu_amt  9930 non-null   float64
     12  r6m_A_avg_arpu_amt  9930 non-null   float64
     13  r6m_B_avg_arpu_amt  9930 non-null   float64
     14  termination_yn      9930 non-null   object 
    dtypes: float64(5), int64(4), object(6)
    memory usage: 1.1+ MB


### <b>1-4. read_csv 함수 파라미터 살펴보기</b>
> - 함수에 커서를 가져다 두고 shift+tab을 누르면 해당 함수의 parameter 볼 수 있음
> - sep - 각 데이터 값을 구별하기 위한 구분자(separator) 설정 
> - index_col : index로 사용할 column 설정
> - usecols : 실제로 dataframe에 로딩할 columns만 설정
> - usecols은 index_col을 포함하여야 함


```python
#cust2 = pd.read_csv('./sc_cust_info_txn_v1.5.csv', index_col='cust_class', usecols=['cust_class', 'r3m_avg_bill_amt', 'r3m_B_avg_arpu_amt', 'r6m_B_avg_arpu_amt'])
cust2 = pd.read_csv('./sc_cust_info_txn_v1.5.csv', usecols=['cust_class', 'r3m_avg_bill_amt', 'r3m_B_avg_arpu_amt', 'r6m_B_avg_arpu_amt'])
cust2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_class</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>C</td>
      <td>2640.0000</td>
      <td>1584.0000</td>
      <td>0.0000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>_</td>
      <td>300.0000</td>
      <td>180.0000</td>
      <td>0.0000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>E</td>
      <td>16840.0000</td>
      <td>6983.0000</td>
      <td>6981.0000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>F</td>
      <td>15544.7334</td>
      <td>6750.4666</td>
      <td>6508.8000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>D</td>
      <td>4700.0000</td>
      <td>4502.0000</td>
      <td>4507.7000</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>9925</th>
      <td>C</td>
      <td>1296.0999</td>
      <td>643.1001</td>
      <td>852.5499</td>
    </tr>
    <tr>
      <th>9926</th>
      <td>G</td>
      <td>13799.6666</td>
      <td>10605.9266</td>
      <td>10603.9266</td>
    </tr>
    <tr>
      <th>9927</th>
      <td>C</td>
      <td>1396.2000</td>
      <td>0.0000</td>
      <td>0.0000</td>
    </tr>
    <tr>
      <th>9928</th>
      <td>C</td>
      <td>3140.0000</td>
      <td>1884.0000</td>
      <td>0.0000</td>
    </tr>
    <tr>
      <th>9929</th>
      <td>C</td>
      <td>2436.9000</td>
      <td>1839.9000</td>
      <td>1919.7999</td>
    </tr>
  </tbody>
</table>
<p>9930 rows × 4 columns</p>
</div>



# __2. Data 조회하기__
DataFrame에서 data를 __조회, 수정__해보고 이를 이해해본다. 

### <b>1-1. 데이터 추출하기</b>

#### <b>1) column 선택하기</b>

> - 기본적으로 [ ]는 column을 추출 : 특정한 col을기준으로 모델링을 하고자 하는 경우
> - 컬럼 인덱스일 경우 인덱스의 리스트 사용 가능
>   - 리스트를 전달할 경우 결과는 Dataframe
>   - 하나의 컬럼명을 전달할 경우 결과는 Series

#### <b>2) 하나의 컬럼 선택하기</b>

> - Series 형태로 가지고 올 수도, DataFrame형태로 가지고 올 수 있음


```python
#cust.cust_class = cust['cust_class']
cust.age = cust['age']
```


```python
cust.age
```




    순번
    0       28
    1        _
    2       24
    3       32
    4       18
            ..
    9925    15
    9926    12
    9927     _
    9928    40
    9929    59
    Name: age, Length: 9930, dtype: object




```python
# cf : series 형태로 가지고 오기(hcust.cust_class = cust['cust_class'])
print(type(cust['cust_class']))
cust['cust_class']
```

    <class 'pandas.core.series.Series'>





    순번
    0       C
    1       _
    2       E
    3       F
    4       D
           ..
    9925    C
    9926    G
    9927    C
    9928    C
    9929    C
    Name: cust_class, Length: 9930, dtype: object




```python
# cf : Dataframe형태로 가지고 오기
print(type(cust[['cust_class']]))
cust[['cust_class']]
```

    <class 'pandas.core.frame.DataFrame'>





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_class</th>
    </tr>
    <tr>
      <th>순번</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>C</td>
    </tr>
    <tr>
      <th>1</th>
      <td>_</td>
    </tr>
    <tr>
      <th>2</th>
      <td>E</td>
    </tr>
    <tr>
      <th>3</th>
      <td>F</td>
    </tr>
    <tr>
      <th>4</th>
      <td>D</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>9925</th>
      <td>C</td>
    </tr>
    <tr>
      <th>9926</th>
      <td>G</td>
    </tr>
    <tr>
      <th>9927</th>
      <td>C</td>
    </tr>
    <tr>
      <th>9928</th>
      <td>C</td>
    </tr>
    <tr>
      <th>9929</th>
      <td>C</td>
    </tr>
  </tbody>
</table>
<p>9930 rows × 1 columns</p>
</div>



#### <b>3) 복수의 컬럼 선택하기</b>


```python
# 'cust_class' , 'age' 'r3m_avg_bill_amt'등 3개의 col 선택하기
cust[['cust_class', 'age', 'r3m_avg_bill_amt']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_class</th>
      <th>age</th>
      <th>r3m_avg_bill_amt</th>
    </tr>
    <tr>
      <th>순번</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>C</td>
      <td>28</td>
      <td>2640.0000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>_</td>
      <td>_</td>
      <td>300.0000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>E</td>
      <td>24</td>
      <td>16840.0000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>F</td>
      <td>32</td>
      <td>15544.7334</td>
    </tr>
    <tr>
      <th>4</th>
      <td>D</td>
      <td>18</td>
      <td>4700.0000</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>9925</th>
      <td>C</td>
      <td>15</td>
      <td>1296.0999</td>
    </tr>
    <tr>
      <th>9926</th>
      <td>G</td>
      <td>12</td>
      <td>13799.6666</td>
    </tr>
    <tr>
      <th>9927</th>
      <td>C</td>
      <td>_</td>
      <td>1396.2000</td>
    </tr>
    <tr>
      <th>9928</th>
      <td>C</td>
      <td>40</td>
      <td>3140.0000</td>
    </tr>
    <tr>
      <th>9929</th>
      <td>C</td>
      <td>59</td>
      <td>2436.9000</td>
    </tr>
  </tbody>
</table>
<p>9930 rows × 3 columns</p>
</div>



#### <b>4) DataFrame slicing</b>

>- 특정 **행 범위**를 가지고 오고 싶다면 [ ]를 사용
>- DataFrame의 경우 기본적으로 [ ] 연산자가 **column 선택**에 사용되지만 **slicing은 row 레벨**로 지원


```python
# 7,8,9행을 가지고 옴 (인덱스 기준)
#cust[7:10]
```

#### <b>5) row 선택하기</b>

 - DataFrame에서는 기본적으로 **[ ]을 사용하여 column을 선택**
 > __row 선택(두가지 방법이 존재)__
 > - **loc** : Dataframe에 존재하는 **인덱스를 그대로 사용** (인덱스 기준으로 행 데이터 읽기)
 > - **iloc** : Datafrmae에 존재하는 인덱스 상관없이 **0 based index로 사용** (행 번호 기준으로 행 데이터 읽기)
 > - 이 두 함수는 ,를 사용하여 column 선택도 가능



```python
cust.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 9930 entries, 0 to 9929
    Data columns (total 15 columns):
     #   Column              Non-Null Count  Dtype  
    ---  ------              --------------  -----  
     0   base_ym             9930 non-null   int64  
     1   dpro_tgt_perd_val   9930 non-null   int64  
     2   cust_ctg_type       9930 non-null   int64  
     3   cust_class          9930 non-null   object 
     4   sex_type            9930 non-null   object 
     5   age                 9930 non-null   object 
     6   efct_svc_count      9930 non-null   int64  
     7   dt_stop_yn          9930 non-null   object 
     8   npay_yn             9930 non-null   object 
     9   r3m_avg_bill_amt    9930 non-null   float64
     10  r3m_A_avg_arpu_amt  9930 non-null   float64
     11  r3m_B_avg_arpu_amt  9930 non-null   float64
     12  r6m_A_avg_arpu_amt  9930 non-null   float64
     13  r6m_B_avg_arpu_amt  9930 non-null   float64
     14  termination_yn      9930 non-null   object 
    dtypes: float64(5), int64(4), object(6)
    memory usage: 1.1+ MB



```python
# arange함수는 10부터 19에서 끝나도록 간격을 1로 반환한다.
cp=np.arange(10,20)
cp
```




    array([10, 11, 12, 13, 14, 15, 16, 17, 18, 19])




```python
cust.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
    <tr>
      <th>순번</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>28</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>2640.0000</td>
      <td>792.00000</td>
      <td>1584.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>1</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>300.0000</td>
      <td>90.00000</td>
      <td>180.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>2</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>E</td>
      <td>F</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.0000</td>
      <td>2526.00000</td>
      <td>6983.0000</td>
      <td>0.0</td>
      <td>6981.0</td>
      <td>N</td>
    </tr>
    <tr>
      <th>3</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>F</td>
      <td>F</td>
      <td>32</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>15544.7334</td>
      <td>2331.71001</td>
      <td>6750.4666</td>
      <td>0.0</td>
      <td>6508.8</td>
      <td>N</td>
    </tr>
    <tr>
      <th>4</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>D</td>
      <td>M</td>
      <td>18</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>4700.0000</td>
      <td>0.00000</td>
      <td>4502.0000</td>
      <td>0.0</td>
      <td>4507.7</td>
      <td>N</td>
    </tr>
  </tbody>
</table>
</div>




```python
#index를 100부터 달아주기 (인덱스 변호를 다시 매겨주기)
cust.index = np.arange(100, 10030)
cust
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>100</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>28</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>2640.0000</td>
      <td>792.000000</td>
      <td>1584.0000</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>101</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>300.0000</td>
      <td>90.000000</td>
      <td>180.0000</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>102</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>E</td>
      <td>F</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.0000</td>
      <td>2526.000000</td>
      <td>6983.0000</td>
      <td>0.0</td>
      <td>6981.0000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>103</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>F</td>
      <td>F</td>
      <td>32</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>15544.7334</td>
      <td>2331.710010</td>
      <td>6750.4666</td>
      <td>0.0</td>
      <td>6508.8000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>104</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>D</td>
      <td>M</td>
      <td>18</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>4700.0000</td>
      <td>0.000000</td>
      <td>4502.0000</td>
      <td>0.0</td>
      <td>4507.7000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>10025</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>15</td>
      <td>1</td>
      <td>N</td>
      <td>Y</td>
      <td>1296.0999</td>
      <td>194.414985</td>
      <td>643.1001</td>
      <td>0.0</td>
      <td>852.5499</td>
      <td>N</td>
    </tr>
    <tr>
      <th>10026</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>G</td>
      <td>M</td>
      <td>12</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>13799.6666</td>
      <td>2069.949990</td>
      <td>10605.9266</td>
      <td>0.0</td>
      <td>10603.9266</td>
      <td>N</td>
    </tr>
    <tr>
      <th>10027</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10005</td>
      <td>C</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>1396.2000</td>
      <td>1206.000000</td>
      <td>0.0000</td>
      <td>1212.0</td>
      <td>0.0000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>10028</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>40</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>3140.0000</td>
      <td>942.000000</td>
      <td>1884.0000</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>10029</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>59</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>2436.9000</td>
      <td>365.535000</td>
      <td>1839.9000</td>
      <td>0.0</td>
      <td>1919.7999</td>
      <td>N</td>
    </tr>
  </tbody>
</table>
<p>9930 rows × 15 columns</p>
</div>




```python
cust.tail()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>10025</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>15</td>
      <td>1</td>
      <td>N</td>
      <td>Y</td>
      <td>1296.0999</td>
      <td>194.414985</td>
      <td>643.1001</td>
      <td>0.0</td>
      <td>852.5499</td>
      <td>N</td>
    </tr>
    <tr>
      <th>10026</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>G</td>
      <td>M</td>
      <td>12</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>13799.6666</td>
      <td>2069.949990</td>
      <td>10605.9266</td>
      <td>0.0</td>
      <td>10603.9266</td>
      <td>N</td>
    </tr>
    <tr>
      <th>10027</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10005</td>
      <td>C</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>1396.2000</td>
      <td>1206.000000</td>
      <td>0.0000</td>
      <td>1212.0</td>
      <td>0.0000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>10028</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>40</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>3140.0000</td>
      <td>942.000000</td>
      <td>1884.0000</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>10029</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>59</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>2436.9000</td>
      <td>365.535000</td>
      <td>1839.9000</td>
      <td>0.0</td>
      <td>1919.7999</td>
      <td>N</td>
    </tr>
  </tbody>
</table>
</div>



#### loc는 인덱스 이름 기반이고
>-  iloc는 인덱스 위치 기반임.
>- loc[2]와 iloc[2]의 차이는 loc는 인덱스가 2인것, iloc는 2번째 인덱스의 값을 가져오라는것


```python
#한개의 row만 가지고 오기
cust.loc[[289]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>289</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>G</td>
      <td>M</td>
      <td>28</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>14340.91989</td>
      <td>331.5999</td>
      <td>12705.6</td>
      <td>0.0</td>
      <td>12703.6</td>
      <td>N</td>
    </tr>
  </tbody>
</table>
</div>




```python
#여러개의 row 가지고 오기
cust.loc[[102, 202, 302]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>102</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>E</td>
      <td>F</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.00000</td>
      <td>2526.0000</td>
      <td>6983.0</td>
      <td>0.0</td>
      <td>6981.00</td>
      <td>N</td>
    </tr>
    <tr>
      <th>202</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10010</td>
      <td>_</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>22362.93330</td>
      <td>2082.0000</td>
      <td>9410.0</td>
      <td>0.0</td>
      <td>9408.00</td>
      <td>N</td>
    </tr>
    <tr>
      <th>302</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>G</td>
      <td>M</td>
      <td>52</td>
      <td>1</td>
      <td>N</td>
      <td>Y</td>
      <td>17769.50989</td>
      <td>1506.9999</td>
      <td>14647.1</td>
      <td>0.0</td>
      <td>14744.95</td>
      <td>N</td>
    </tr>
  </tbody>
</table>
</div>




```python
#iloc과비교(위와 같은 값을 가지고 오려면...)    (직접 타이핑 해보세요)
cust.iloc[[2, 102, 202]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>102</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>E</td>
      <td>F</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.00000</td>
      <td>2526.0000</td>
      <td>6983.0</td>
      <td>0.0</td>
      <td>6981.00</td>
      <td>N</td>
    </tr>
    <tr>
      <th>202</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10010</td>
      <td>_</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>22362.93330</td>
      <td>2082.0000</td>
      <td>9410.0</td>
      <td>0.0</td>
      <td>9408.00</td>
      <td>N</td>
    </tr>
    <tr>
      <th>302</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>G</td>
      <td>M</td>
      <td>52</td>
      <td>1</td>
      <td>N</td>
      <td>Y</td>
      <td>17769.50989</td>
      <td>1506.9999</td>
      <td>14647.1</td>
      <td>0.0</td>
      <td>14744.95</td>
      <td>N</td>
    </tr>
  </tbody>
</table>
</div>



- row, column 동시에 선택하기
 > loc, iloc 속성을 이용할 때, 콤마를 이용하여 row와 col 다 명시 가능


```python
# 100, 200, 300 대상으로 cust_class, sex_type, age, r3m_avg_bill_amt, r3m_A_avg_arpu_amt  col 가지고 오기(loc사용)
cust.loc[[100, 200, 300], ['cust_class', 'sex_type', 'age', 'r3m_avg_bill_amt', 'r3m_A_avg_arpu_amt']]   # row, col
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>100</th>
      <td>C</td>
      <td>F</td>
      <td>28</td>
      <td>2640.00000</td>
      <td>792.0000</td>
    </tr>
    <tr>
      <th>200</th>
      <td>E</td>
      <td>M</td>
      <td>61</td>
      <td>9526.77000</td>
      <td>1878.9000</td>
    </tr>
    <tr>
      <th>300</th>
      <td>D</td>
      <td>M</td>
      <td>84</td>
      <td>11622.37472</td>
      <td>2716.7952</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 같은 형태로 iloc사용하기 (index를 level로 가지고 오기)
# 100, 200, 300 대상으로 cust_class, sex_type, age, r3m_avg_bill_amt, r3m_A_avg_arpu_amt  col 가지고 오기(iloc사용)

# cust.iloc[[0, 100, 200],  ['cust_class', 'sex_type', 'age', 'r3m_avg_bill_amt', 'r3m_A_avg_arpu_amt']] <--- iloc를 사용할땐 정수형 인덱스만 사용가능
cust.iloc[[0, 100, 200], [3, 4, 5, 9, 10]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>100</th>
      <td>C</td>
      <td>F</td>
      <td>28</td>
      <td>2640.00000</td>
      <td>792.0000</td>
    </tr>
    <tr>
      <th>200</th>
      <td>E</td>
      <td>M</td>
      <td>61</td>
      <td>9526.77000</td>
      <td>1878.9000</td>
    </tr>
    <tr>
      <th>300</th>
      <td>D</td>
      <td>M</td>
      <td>84</td>
      <td>11622.37472</td>
      <td>2716.7952</td>
    </tr>
  </tbody>
</table>
</div>



#### __6) boolean selection 연산으로 row 선택하기 (= 컬럼 조건문으로 행 추출하기)__

 - 해당 조건에 맞는 row만 선택
 - 조건을 명시하고 조건을 명시한 형태로 indexing 하여 가지고 옴

 - ex: 남자이면서 3개월 평균 청구 금액이 50000 이상이면서 100000 미만인 사람만 가지고오기 


```python
#조건을 전부다  [ ]안에 넣어 주면 됨
extract = cust[(cust['sex_type']=='M') & (cust['r3m_avg_bill_amt']>=50000) & (cust['r3m_avg_bill_amt']< 100000)]
extract.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>472</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>F</td>
      <td>M</td>
      <td>28</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>65113.66670</td>
      <td>1310.4000</td>
      <td>20083.5033</td>
      <td>0.0</td>
      <td>19426.1983</td>
      <td>N</td>
    </tr>
    <tr>
      <th>1149</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>D</td>
      <td>M</td>
      <td>20</td>
      <td>2</td>
      <td>N</td>
      <td>N</td>
      <td>80335.67685</td>
      <td>69136.1001</td>
      <td>3896.3334</td>
      <td>0.0</td>
      <td>3727.6666</td>
      <td>N</td>
    </tr>
    <tr>
      <th>1464</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>M</td>
      <td>45</td>
      <td>1</td>
      <td>N</td>
      <td>Y</td>
      <td>54865.70000</td>
      <td>2321.8666</td>
      <td>8744.9382</td>
      <td>0.0</td>
      <td>8774.7162</td>
      <td>N</td>
    </tr>
    <tr>
      <th>1893</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>G</td>
      <td>M</td>
      <td>48</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>64804.34037</td>
      <td>47599.4501</td>
      <td>11313.5866</td>
      <td>0.0</td>
      <td>11351.4984</td>
      <td>N</td>
    </tr>
    <tr>
      <th>2127</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>G</td>
      <td>M</td>
      <td>47</td>
      <td>1</td>
      <td>N</td>
      <td>Y</td>
      <td>55368.98422</td>
      <td>37432.2666</td>
      <td>12903.1736</td>
      <td>0.0</td>
      <td>12901.1736</td>
      <td>N</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 조건문이 너무 길어지거나 복잡해지면...아래와 같은 방식으로 해도 무방함
# 남자이면서 
sex = cust['sex_type']=='M'
# 3개월 평균 청구 금액이 50000 이상이면서 100000 미만
bill = (cust['r3m_avg_bill_amt']>=50000) & (cust['r3m_avg_bill_amt']< 100000)

cust[sex & bill].head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>472</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>F</td>
      <td>M</td>
      <td>28</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>65113.66670</td>
      <td>1310.4000</td>
      <td>20083.5033</td>
      <td>0.0</td>
      <td>19426.1983</td>
      <td>N</td>
    </tr>
    <tr>
      <th>1149</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>D</td>
      <td>M</td>
      <td>20</td>
      <td>2</td>
      <td>N</td>
      <td>N</td>
      <td>80335.67685</td>
      <td>69136.1001</td>
      <td>3896.3334</td>
      <td>0.0</td>
      <td>3727.6666</td>
      <td>N</td>
    </tr>
    <tr>
      <th>1464</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>M</td>
      <td>45</td>
      <td>1</td>
      <td>N</td>
      <td>Y</td>
      <td>54865.70000</td>
      <td>2321.8666</td>
      <td>8744.9382</td>
      <td>0.0</td>
      <td>8774.7162</td>
      <td>N</td>
    </tr>
    <tr>
      <th>1893</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>G</td>
      <td>M</td>
      <td>48</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>64804.34037</td>
      <td>47599.4501</td>
      <td>11313.5866</td>
      <td>0.0</td>
      <td>11351.4984</td>
      <td>N</td>
    </tr>
    <tr>
      <th>2127</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>G</td>
      <td>M</td>
      <td>47</td>
      <td>1</td>
      <td>N</td>
      <td>Y</td>
      <td>55368.98422</td>
      <td>37432.2666</td>
      <td>12903.1736</td>
      <td>0.0</td>
      <td>12901.1736</td>
      <td>N</td>
    </tr>
  </tbody>
</table>
</div>



#### <b>7) 정리 </b>

- 기본적인 대괄호는 col을 가지고 오는 경우 사용, 하지만 slicing은 row를 가지고 온다.
- row를 가지고 오는 경우는 loc과 iloc을 사용하는데, loc과 iloc은 컬럼과 row를 동시에 가지고 올 수 있다.


```python
import matplotlib.pyplot as plt      #matplotlib.pyplot import   
```

### <b>1-2. 데이터 추가하기</b>

#### <b>1) 새 column 추가하기</b>

>- 데이터 전처리 과정에서 빈번하게 발생하는 것
>- insert 함수 사용하여 원하는 위치에 추가하기


```python
# r3m_avg_bill_amt 두배로 새로운 col만들기
cust['r3m_avg_bill_amt2'] = cust['r3m_avg_bill_amt'] * 2
cust.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
      <th>r3m_avg_bill_amt2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>100</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>28</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>2640.0000</td>
      <td>792.00000</td>
      <td>1584.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
      <td>5280.0000</td>
    </tr>
    <tr>
      <th>101</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>300.0000</td>
      <td>90.00000</td>
      <td>180.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
      <td>600.0000</td>
    </tr>
    <tr>
      <th>102</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>E</td>
      <td>F</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.0000</td>
      <td>2526.00000</td>
      <td>6983.0000</td>
      <td>0.0</td>
      <td>6981.0</td>
      <td>N</td>
      <td>33680.0000</td>
    </tr>
    <tr>
      <th>103</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>F</td>
      <td>F</td>
      <td>32</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>15544.7334</td>
      <td>2331.71001</td>
      <td>6750.4666</td>
      <td>0.0</td>
      <td>6508.8</td>
      <td>N</td>
      <td>31089.4668</td>
    </tr>
    <tr>
      <th>104</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>D</td>
      <td>M</td>
      <td>18</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>4700.0000</td>
      <td>0.00000</td>
      <td>4502.0000</td>
      <td>0.0</td>
      <td>4507.7</td>
      <td>N</td>
      <td>9400.0000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 기존에 col을 연산하여 새로운 데이터 생성
cust['r3m_avg_bill_amt3'] = cust['r3m_avg_bill_amt2'] + cust['r3m_avg_bill_amt']
cust.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
      <th>r3m_avg_bill_amt2</th>
      <th>r3m_avg_bill_amt3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>100</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>28</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>2640.0000</td>
      <td>792.00000</td>
      <td>1584.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
      <td>5280.0000</td>
      <td>7920.0000</td>
    </tr>
    <tr>
      <th>101</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>300.0000</td>
      <td>90.00000</td>
      <td>180.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
      <td>600.0000</td>
      <td>900.0000</td>
    </tr>
    <tr>
      <th>102</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>E</td>
      <td>F</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.0000</td>
      <td>2526.00000</td>
      <td>6983.0000</td>
      <td>0.0</td>
      <td>6981.0</td>
      <td>N</td>
      <td>33680.0000</td>
      <td>50520.0000</td>
    </tr>
    <tr>
      <th>103</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>F</td>
      <td>F</td>
      <td>32</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>15544.7334</td>
      <td>2331.71001</td>
      <td>6750.4666</td>
      <td>0.0</td>
      <td>6508.8</td>
      <td>N</td>
      <td>31089.4668</td>
      <td>46634.2002</td>
    </tr>
    <tr>
      <th>104</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>D</td>
      <td>M</td>
      <td>18</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>4700.0000</td>
      <td>0.00000</td>
      <td>4502.0000</td>
      <td>0.0</td>
      <td>4507.7</td>
      <td>N</td>
      <td>9400.0000</td>
      <td>14100.0000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 컬럼 삭제
cust.drop('r3m_avg_bill_amt3', axis=1, inplace=True)  # axis가 0이면 index, 1이면 컬럼
cust.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
      <th>r3m_avg_bill_amt2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>100</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>28</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>2640.0000</td>
      <td>792.00000</td>
      <td>1584.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
      <td>5280.0000</td>
    </tr>
    <tr>
      <th>101</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>300.0000</td>
      <td>90.00000</td>
      <td>180.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
      <td>600.0000</td>
    </tr>
    <tr>
      <th>102</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>E</td>
      <td>F</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.0000</td>
      <td>2526.00000</td>
      <td>6983.0000</td>
      <td>0.0</td>
      <td>6981.0</td>
      <td>N</td>
      <td>33680.0000</td>
    </tr>
    <tr>
      <th>103</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>F</td>
      <td>F</td>
      <td>32</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>15544.7334</td>
      <td>2331.71001</td>
      <td>6750.4666</td>
      <td>0.0</td>
      <td>6508.8</td>
      <td>N</td>
      <td>31089.4668</td>
    </tr>
    <tr>
      <th>104</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>D</td>
      <td>M</td>
      <td>18</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>4700.0000</td>
      <td>0.00000</td>
      <td>4502.0000</td>
      <td>0.0</td>
      <td>4507.7</td>
      <td>N</td>
      <td>9400.0000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 새로은 col들은 항상맨뒤에 존재 원하는 위치에 col을 추가하고자 하는 경우
# 위치를 조절 하고 싶다면(insert함수 사용)
cust.insert(10, 'r3m_avg_bill_amt10', cust['r3m_avg_bill_amt'] *10)  # 0부터 시작하여 10번째 col에 insert
cust.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_avg_bill_amt10</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
      <th>r3m_avg_bill_amt2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>100</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>28</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>2640.0000</td>
      <td>26400.000</td>
      <td>792.00000</td>
      <td>1584.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
      <td>5280.0000</td>
    </tr>
    <tr>
      <th>101</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>300.0000</td>
      <td>3000.000</td>
      <td>90.00000</td>
      <td>180.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
      <td>600.0000</td>
    </tr>
    <tr>
      <th>102</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>E</td>
      <td>F</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.0000</td>
      <td>168400.000</td>
      <td>2526.00000</td>
      <td>6983.0000</td>
      <td>0.0</td>
      <td>6981.0</td>
      <td>N</td>
      <td>33680.0000</td>
    </tr>
    <tr>
      <th>103</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>F</td>
      <td>F</td>
      <td>32</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>15544.7334</td>
      <td>155447.334</td>
      <td>2331.71001</td>
      <td>6750.4666</td>
      <td>0.0</td>
      <td>6508.8</td>
      <td>N</td>
      <td>31089.4668</td>
    </tr>
    <tr>
      <th>104</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>D</td>
      <td>M</td>
      <td>18</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>4700.0000</td>
      <td>47000.000</td>
      <td>0.00000</td>
      <td>4502.0000</td>
      <td>0.0</td>
      <td>4507.7</td>
      <td>N</td>
      <td>9400.0000</td>
    </tr>
  </tbody>
</table>
</div>



#### __2) column 삭제하기__

>- drop 함수 사용하여 삭제
>- axis는 삭제를 가로(행)기준으로 할 것인지, 세로(열)기준으로 할 것인지 명시하는 'drop()'메소드의 파라미터임 
>- 리스트를 사용하면 멀티플 col 삭제 가능


```python
# axis : dataframe은 차원이 존재 함으로 항상 0과 1이 존재 
# (0은 행레벨, 1을 열 레벨)
cust.drop('r3m_avg_bill_amt10', axis=1)
cust.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_avg_bill_amt10</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
      <th>r3m_avg_bill_amt2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>100</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>28</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>2640.0000</td>
      <td>26400.000</td>
      <td>792.00000</td>
      <td>1584.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
      <td>5280.0000</td>
    </tr>
    <tr>
      <th>101</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>300.0000</td>
      <td>3000.000</td>
      <td>90.00000</td>
      <td>180.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
      <td>600.0000</td>
    </tr>
    <tr>
      <th>102</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>E</td>
      <td>F</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.0000</td>
      <td>168400.000</td>
      <td>2526.00000</td>
      <td>6983.0000</td>
      <td>0.0</td>
      <td>6981.0</td>
      <td>N</td>
      <td>33680.0000</td>
    </tr>
    <tr>
      <th>103</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>F</td>
      <td>F</td>
      <td>32</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>15544.7334</td>
      <td>155447.334</td>
      <td>2331.71001</td>
      <td>6750.4666</td>
      <td>0.0</td>
      <td>6508.8</td>
      <td>N</td>
      <td>31089.4668</td>
    </tr>
    <tr>
      <th>104</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>D</td>
      <td>M</td>
      <td>18</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>4700.0000</td>
      <td>47000.000</td>
      <td>0.00000</td>
      <td>4502.0000</td>
      <td>0.0</td>
      <td>4507.7</td>
      <td>N</td>
      <td>9400.0000</td>
    </tr>
  </tbody>
</table>
</div>




```python
#원본 데이터를 열어 보면 원본 데이터는 안 지워진 상태
cust.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_avg_bill_amt10</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
      <th>r3m_avg_bill_amt2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>100</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>28</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>2640.0000</td>
      <td>26400.000</td>
      <td>792.00000</td>
      <td>1584.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
      <td>5280.0000</td>
    </tr>
    <tr>
      <th>101</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>300.0000</td>
      <td>3000.000</td>
      <td>90.00000</td>
      <td>180.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
      <td>600.0000</td>
    </tr>
    <tr>
      <th>102</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>E</td>
      <td>F</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.0000</td>
      <td>168400.000</td>
      <td>2526.00000</td>
      <td>6983.0000</td>
      <td>0.0</td>
      <td>6981.0</td>
      <td>N</td>
      <td>33680.0000</td>
    </tr>
    <tr>
      <th>103</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>F</td>
      <td>F</td>
      <td>32</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>15544.7334</td>
      <td>155447.334</td>
      <td>2331.71001</td>
      <td>6750.4666</td>
      <td>0.0</td>
      <td>6508.8</td>
      <td>N</td>
      <td>31089.4668</td>
    </tr>
    <tr>
      <th>104</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>D</td>
      <td>M</td>
      <td>18</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>4700.0000</td>
      <td>47000.000</td>
      <td>0.00000</td>
      <td>4502.0000</td>
      <td>0.0</td>
      <td>4507.7</td>
      <td>N</td>
      <td>9400.0000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 원본 데이터를 지우고자 한다면... 
# 방법1 : 데이터를 지우고 다른 데이터 프레임에 저장
cust1=cust.drop('r3m_avg_bill_amt10', axis=1)
cust1.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
      <th>r3m_avg_bill_amt2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>100</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>28</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>2640.0000</td>
      <td>792.00000</td>
      <td>1584.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
      <td>5280.0000</td>
    </tr>
    <tr>
      <th>101</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>300.0000</td>
      <td>90.00000</td>
      <td>180.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
      <td>600.0000</td>
    </tr>
    <tr>
      <th>102</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>E</td>
      <td>F</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.0000</td>
      <td>2526.00000</td>
      <td>6983.0000</td>
      <td>0.0</td>
      <td>6981.0</td>
      <td>N</td>
      <td>33680.0000</td>
    </tr>
    <tr>
      <th>103</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>F</td>
      <td>F</td>
      <td>32</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>15544.7334</td>
      <td>2331.71001</td>
      <td>6750.4666</td>
      <td>0.0</td>
      <td>6508.8</td>
      <td>N</td>
      <td>31089.4668</td>
    </tr>
    <tr>
      <th>104</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>D</td>
      <td>M</td>
      <td>18</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>4700.0000</td>
      <td>0.00000</td>
      <td>4502.0000</td>
      <td>0.0</td>
      <td>4507.7</td>
      <td>N</td>
      <td>9400.0000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 원본 자체를 지우고자 한다면...
# 방법 2 : inplace 파라미터를 할용 True인 경우 원본데이터에 수행
cust.drop('r3m_avg_bill_amt10', axis=1, inplace=True)
cust.info()  ## 확인
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 9930 entries, 100 to 10029
    Data columns (total 16 columns):
     #   Column              Non-Null Count  Dtype  
    ---  ------              --------------  -----  
     0   base_ym             9930 non-null   int64  
     1   dpro_tgt_perd_val   9930 non-null   int64  
     2   cust_ctg_type       9930 non-null   int64  
     3   cust_class          9930 non-null   object 
     4   sex_type            9930 non-null   object 
     5   age                 9930 non-null   object 
     6   efct_svc_count      9930 non-null   int64  
     7   dt_stop_yn          9930 non-null   object 
     8   npay_yn             9930 non-null   object 
     9   r3m_avg_bill_amt    9930 non-null   float64
     10  r3m_A_avg_arpu_amt  9930 non-null   float64
     11  r3m_B_avg_arpu_amt  9930 non-null   float64
     12  r6m_A_avg_arpu_amt  9930 non-null   float64
     13  r6m_B_avg_arpu_amt  9930 non-null   float64
     14  termination_yn      9930 non-null   object 
     15  r3m_avg_bill_amt2   9930 non-null   float64
    dtypes: float64(6), int64(4), object(6)
    memory usage: 1.6+ MB


# Chapter 2. DataFrame 변형하기

# __1. DataFrame group by 이해하기__


### <b>1-1. 데이터 묶기</b>


```python
import pandas as pd
import numpy as np
```

#### <b>1) 그룹화(groupby)</b>

  + 같은 값을 하나로 묶어 통계 또는 집계 결과를얻기위해 사용하는 것
  + 아래의 세 단계를 적용하여 데이터를 그룹화(groupping) / 특정한 col을 기준으로 데이터를 그룹핑 하여 통계에 활용하는 것
    - 데이터 분할(split) : 어떠한 기준을 바탕으로 데이터를 나누는 일
    - operation 적용(applying) : 각 그룹에 어떤 함수를 독립적으로 적용시키는 일
    - 데이터 병합(cobine) : 적용되어 나온 결과들을 통합하는 일
  + 데이터 분석에 있어 사용빈도가 높음
  + groupby의 결과는 dictionary형태임


![](https://t1.daumcdn.net/cfile/tistory/9978503F5B8264490F)


```python
cust = pd.read_csv('./sc_cust_info_txn_v1.5.csv', encoding = "cp949")
cust.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>28</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>2640.0000</td>
      <td>792.00000</td>
      <td>1584.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>1</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>300.0000</td>
      <td>90.00000</td>
      <td>180.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>2</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>E</td>
      <td>F</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.0000</td>
      <td>2526.00000</td>
      <td>6983.0000</td>
      <td>0.0</td>
      <td>6981.0</td>
      <td>N</td>
    </tr>
    <tr>
      <th>3</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>F</td>
      <td>F</td>
      <td>32</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>15544.7334</td>
      <td>2331.71001</td>
      <td>6750.4666</td>
      <td>0.0</td>
      <td>6508.8</td>
      <td>N</td>
    </tr>
    <tr>
      <th>4</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>D</td>
      <td>M</td>
      <td>18</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>4700.0000</td>
      <td>0.00000</td>
      <td>4502.0000</td>
      <td>0.0</td>
      <td>4507.7</td>
      <td>N</td>
    </tr>
  </tbody>
</table>
</div>



> ##### __1-1) groupby의 groups 속성__
> - 각 그룹과 그룹에 속한 index를 dict 형태로 표현


```python
# 파라미터 값으로 col의 리스트나 col을 전달
# 출력은 우선 dataframe이라고 하는 객체임(그룹을 생성까지 한 상태)

gender_group = cust.groupby('sex_type')
gender_group.count()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
    <tr>
      <th>sex_type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>F</th>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
    </tr>
    <tr>
      <th>M</th>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
    </tr>
    <tr>
      <th>_</th>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
    </tr>
  </tbody>
</table>
</div>




```python
# groups를 활용하여 그룹의 속성을 살펴보기
gender_group.groups
```




    {'F': [0, 2, 3, 5, 7, 9, 12, 13, 14, 16, 17, 19, 20, 21, 24, 25, 26, 40, 41, 43, 46, 47, 49, 51, 52, 55, 65, 69, 73, 75, 77, 79, 80, 81, 82, 85, 86, 90, 91, 93, 94, 95, 101, 105, 106, 111, 112, 116, 119, 120, 121, 127, 130, 131, 134, 135, 136, 137, 138, 142, 143, 147, 148, 149, 151, 152, 155, 156, 157, 159, 163, 164, 166, 167, 169, 173, 174, 176, 177, 181, 184, 190, 191, 193, 195, 197, 205, 206, 208, 210, 211, 213, 215, 216, 218, 221, 225, 230, 234, 235, ...], 'M': [4, 6, 8, 11, 15, 18, 22, 23, 27, 28, 29, 30, 31, 32, 33, 34, 36, 37, 38, 39, 42, 44, 45, 48, 50, 53, 54, 56, 57, 58, 59, 60, 61, 63, 64, 67, 68, 70, 74, 76, 78, 84, 87, 88, 89, 96, 97, 98, 99, 100, 103, 104, 107, 108, 109, 110, 113, 115, 117, 122, 123, 124, 125, 126, 128, 132, 133, 139, 140, 141, 144, 145, 146, 150, 153, 154, 158, 160, 161, 162, 168, 170, 171, 172, 175, 178, 179, 180, 183, 185, 186, 187, 188, 189, 192, 194, 198, 199, 200, 201, ...], '_': [1, 10, 35, 62, 66, 71, 72, 83, 92, 102, 114, 118, 129, 165, 182, 196, 228, 232, 243, 288, 314, 317, 324, 393, 394, 451, 489, 496, 501, 502, 573, 611, 629, 658, 667, 669, 676, 683, 690, 701, 708, 717, 739, 751, 758, 773, 792, 816, 820, 821, 836, 851, 864, 895, 910, 935, 937, 942, 943, 946, 950, 971, 986, 991, 992, 1005, 1008, 1011, 1012, 1015, 1021, 1023, 1027, 1056, 1058, 1062, 1077, 1088, 1102, 1108, 1147, 1171, 1174, 1185, 1196, 1209, 1214, 1215, 1237, 1240, 1241, 1273, 1281, 1284, 1296, 1302, 1314, 1330, 1360, 1363, ...]}



>##### __1-2) groupby 내부 함수 활용하기__
 - 그룹 데이터에 적용 가능한 통계 함수(NaN은 제외하여 연산)
 - count : 데이터 개수
 - size : 집단별 크기
 - sum  : 데이터의 합
 - mean, std, var : 평균, 표준편차, 분산
 - min, max : 최소, 최대값


```python
# count 함수 확인
gender_group.count()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
    <tr>
      <th>sex_type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>F</th>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
      <td>4251</td>
    </tr>
    <tr>
      <th>M</th>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
      <td>4998</td>
    </tr>
    <tr>
      <th>_</th>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
    </tr>
  </tbody>
</table>
</div>




```python
# mean 함수 확인
gender_group.mean()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>efct_svc_count</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
    </tr>
    <tr>
      <th>sex_type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>F</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.001882</td>
      <td>1.098800</td>
      <td>9580.926307</td>
      <td>1570.372299</td>
      <td>5283.876950</td>
      <td>452.780488</td>
      <td>4961.455810</td>
    </tr>
    <tr>
      <th>M</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.004802</td>
      <td>1.204882</td>
      <td>9839.707339</td>
      <td>1778.988878</td>
      <td>5342.748791</td>
      <td>641.426866</td>
      <td>4851.027884</td>
    </tr>
    <tr>
      <th>_</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10006.389134</td>
      <td>6.462555</td>
      <td>40297.790077</td>
      <td>4809.827390</td>
      <td>21057.412985</td>
      <td>4854.788244</td>
      <td>864.386867</td>
    </tr>
  </tbody>
</table>
</div>




```python
# max값 확인하기
gender_group.max()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
    <tr>
      <th>sex_type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>F</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10005</td>
      <td>_</td>
      <td>_</td>
      <td>9</td>
      <td>Y</td>
      <td>Y</td>
      <td>7.979563e+04</td>
      <td>5.500240e+04</td>
      <td>5.710153e+04</td>
      <td>2.302815e+04</td>
      <td>48787.2333</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>M</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10005</td>
      <td>_</td>
      <td>_</td>
      <td>14</td>
      <td>Y</td>
      <td>Y</td>
      <td>1.447397e+05</td>
      <td>1.315815e+05</td>
      <td>6.583656e+04</td>
      <td>2.749282e+04</td>
      <td>64947.0920</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>_</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10010</td>
      <td>_</td>
      <td>_</td>
      <td>905</td>
      <td>Y</td>
      <td>Y</td>
      <td>1.281568e+07</td>
      <td>1.188998e+06</td>
      <td>7.689409e+06</td>
      <td>1.208498e+06</td>
      <td>18796.6266</td>
      <td>Y</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 특정 col만 보는 경우 : gender별 r3m_avg_bill_amt의 평균
print(gender_group.mean()[['r3m_avg_bill_amt']])

print(gender_group[['r3m_avg_bill_amt']].mean())   ## 두개가 동일한 결과가 됨
```

              r3m_avg_bill_amt
    sex_type                  
    F              9580.926307
    M              9839.707339
    _             40297.790077
              r3m_avg_bill_amt
    sex_type                  
    F              9580.926307
    M              9839.707339
    _             40297.790077


> ##### __1-3) 인덱스 설정(groupby) 후 데이터 추출하기__
- 성별 r3m_avg_bill_amt의 평균


```python
# groupby한 상태에서 가지고 오는 경우 
gender_group.mean()[['r3m_avg_bill_amt']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>r3m_avg_bill_amt</th>
    </tr>
    <tr>
      <th>sex_type</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>F</th>
      <td>9580.926307</td>
    </tr>
    <tr>
      <th>M</th>
      <td>9839.707339</td>
    </tr>
    <tr>
      <th>_</th>
      <td>40297.790077</td>
    </tr>
  </tbody>
</table>
</div>




```python
# groupby하기 전 원 DataFrame에서 가지고 오는 경우(같은 의미)
cust.groupby('sex_type').mean()[['r3m_avg_bill_amt']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>r3m_avg_bill_amt</th>
    </tr>
    <tr>
      <th>sex_type</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>F</th>
      <td>9580.926307</td>
    </tr>
    <tr>
      <th>M</th>
      <td>9839.707339</td>
    </tr>
    <tr>
      <th>_</th>
      <td>40297.790077</td>
    </tr>
  </tbody>
</table>
</div>



>##### __1-4) 복수 columns을 기준으로 Groupping 하기__
>- groupby에 column 리스트를 전달할 수 있고 복수개의 전달도 가능함
>- 통계함수를 적용한 결과는 multiindex를 갖는 DataFrame


```python
# cust_class 와 sex_type으로 index를 정하고 이에따른 r3m_avg_bill_amt의 평균을 구하기
cust.groupby(['cust_class', 'sex_type']).mean()[['r3m_avg_bill_amt']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>r3m_avg_bill_amt</th>
    </tr>
    <tr>
      <th>cust_class</th>
      <th>sex_type</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">C</th>
      <th>F</th>
      <td>3804.342244</td>
    </tr>
    <tr>
      <th>M</th>
      <td>3155.385796</td>
    </tr>
    <tr>
      <th>_</th>
      <td>4719.075980</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">D</th>
      <th>F</th>
      <td>7848.842709</td>
    </tr>
    <tr>
      <th>M</th>
      <td>7774.098954</td>
    </tr>
    <tr>
      <th>_</th>
      <td>8419.764574</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">E</th>
      <th>F</th>
      <td>11257.301485</td>
    </tr>
    <tr>
      <th>M</th>
      <td>11158.736812</td>
    </tr>
    <tr>
      <th>_</th>
      <td>12208.980550</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">F</th>
      <th>F</th>
      <td>14913.105272</td>
    </tr>
    <tr>
      <th>M</th>
      <td>15013.379957</td>
    </tr>
    <tr>
      <th>_</th>
      <td>16231.437767</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">G</th>
      <th>F</th>
      <td>16538.595017</td>
    </tr>
    <tr>
      <th>M</th>
      <td>16847.160637</td>
    </tr>
    <tr>
      <th>_</th>
      <td>20180.014811</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">H</th>
      <th>F</th>
      <td>20154.938768</td>
    </tr>
    <tr>
      <th>M</th>
      <td>21052.154088</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">_</th>
      <th>F</th>
      <td>4304.582332</td>
    </tr>
    <tr>
      <th>M</th>
      <td>4728.388010</td>
    </tr>
    <tr>
      <th>_</th>
      <td>65268.733884</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 위와 동일하게 groupby한 이후에 평균 구하기
multi_group=cust.groupby(['cust_class', 'sex_type'])
multi_group.mean()[['r3m_avg_bill_amt']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>r3m_avg_bill_amt</th>
    </tr>
    <tr>
      <th>cust_class</th>
      <th>sex_type</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">C</th>
      <th>F</th>
      <td>3804.342244</td>
    </tr>
    <tr>
      <th>M</th>
      <td>3155.385796</td>
    </tr>
    <tr>
      <th>_</th>
      <td>4719.075980</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">D</th>
      <th>F</th>
      <td>7848.842709</td>
    </tr>
    <tr>
      <th>M</th>
      <td>7774.098954</td>
    </tr>
    <tr>
      <th>_</th>
      <td>8419.764574</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">E</th>
      <th>F</th>
      <td>11257.301485</td>
    </tr>
    <tr>
      <th>M</th>
      <td>11158.736812</td>
    </tr>
    <tr>
      <th>_</th>
      <td>12208.980550</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">F</th>
      <th>F</th>
      <td>14913.105272</td>
    </tr>
    <tr>
      <th>M</th>
      <td>15013.379957</td>
    </tr>
    <tr>
      <th>_</th>
      <td>16231.437767</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">G</th>
      <th>F</th>
      <td>16538.595017</td>
    </tr>
    <tr>
      <th>M</th>
      <td>16847.160637</td>
    </tr>
    <tr>
      <th>_</th>
      <td>20180.014811</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">H</th>
      <th>F</th>
      <td>20154.938768</td>
    </tr>
    <tr>
      <th>M</th>
      <td>21052.154088</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">_</th>
      <th>F</th>
      <td>4304.582332</td>
    </tr>
    <tr>
      <th>M</th>
      <td>4728.388010</td>
    </tr>
    <tr>
      <th>_</th>
      <td>65268.733884</td>
    </tr>
  </tbody>
</table>
</div>




```python
# INDEX는 DEPTH가 존재함 (loc을 사용하여 원하는 것만 가지고 옴)
#cust.groupby(['cust_class', 'sex_type']).mean()
cust.groupby(['cust_class', 'sex_type']).mean().loc[[("D","M")]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>efct_svc_count</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
    </tr>
    <tr>
      <th>cust_class</th>
      <th>sex_type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>D</th>
      <th>M</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.00736</td>
      <td>1.045078</td>
      <td>7774.098954</td>
      <td>1742.249493</td>
      <td>4098.230598</td>
      <td>550.449533</td>
      <td>3054.969393</td>
    </tr>
  </tbody>
</table>
</div>



> ##### __1-5) index를 이용한 group by__
> - index가 있는 경우, groupby 함수에 level 사용 가능
> - level은 index의 depth를 의미하며, 가장 왼쪽부터 0부터 증가
> - **set_index** 함수
>  - column 데이터를 index 레벨로 변경하는 경우 사용
>  - 기존의 행 인덱스를 제거하고 데이터 열 중 하나를 인덱스로 설정
> - **reset_index** 함수 
>  - 인덱스 초기화
>  - 기존의 행 인덱스를 제거하고 인덱스를 데이터 열로 추가


```python
# heat DataFrame 다시 한번 확인 합니다.
cust.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>C</td>
      <td>F</td>
      <td>28</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>2640.0000</td>
      <td>792.00000</td>
      <td>1584.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>1</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>_</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>300.0000</td>
      <td>90.00000</td>
      <td>180.0000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>2</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>E</td>
      <td>F</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.0000</td>
      <td>2526.00000</td>
      <td>6983.0000</td>
      <td>0.0</td>
      <td>6981.0</td>
      <td>N</td>
    </tr>
    <tr>
      <th>3</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>F</td>
      <td>F</td>
      <td>32</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>15544.7334</td>
      <td>2331.71001</td>
      <td>6750.4666</td>
      <td>0.0</td>
      <td>6508.8</td>
      <td>N</td>
    </tr>
    <tr>
      <th>4</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>D</td>
      <td>M</td>
      <td>18</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>4700.0000</td>
      <td>0.00000</td>
      <td>4502.0000</td>
      <td>0.0</td>
      <td>4507.7</td>
      <td>N</td>
    </tr>
  </tbody>
</table>
</div>



> ##### __1-6) MultiIndex를 이용한 groupping__


```python
# set_index로 index셋팅(멀티도 가능)
cust.set_index(['cust_class','sex_type'])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
    <tr>
      <th>cust_class</th>
      <th>sex_type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>C</th>
      <th>F</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>28</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>2640.0000</td>
      <td>792.000000</td>
      <td>1584.0000</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>_</th>
      <th>_</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>300.0000</td>
      <td>90.000000</td>
      <td>180.0000</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>E</th>
      <th>F</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.0000</td>
      <td>2526.000000</td>
      <td>6983.0000</td>
      <td>0.0</td>
      <td>6981.0000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>F</th>
      <th>F</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>32</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>15544.7334</td>
      <td>2331.710010</td>
      <td>6750.4666</td>
      <td>0.0</td>
      <td>6508.8000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>D</th>
      <th>M</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>18</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>4700.0000</td>
      <td>0.000000</td>
      <td>4502.0000</td>
      <td>0.0</td>
      <td>4507.7000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>...</th>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>C</th>
      <th>F</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>15</td>
      <td>1</td>
      <td>N</td>
      <td>Y</td>
      <td>1296.0999</td>
      <td>194.414985</td>
      <td>643.1001</td>
      <td>0.0</td>
      <td>852.5499</td>
      <td>N</td>
    </tr>
    <tr>
      <th>G</th>
      <th>M</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>12</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>13799.6666</td>
      <td>2069.949990</td>
      <td>10605.9266</td>
      <td>0.0</td>
      <td>10603.9266</td>
      <td>N</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">C</th>
      <th>_</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10005</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>1396.2000</td>
      <td>1206.000000</td>
      <td>0.0000</td>
      <td>1212.0</td>
      <td>0.0000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>F</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>40</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>3140.0000</td>
      <td>942.000000</td>
      <td>1884.0000</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>F</th>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>59</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>2436.9000</td>
      <td>365.535000</td>
      <td>1839.9000</td>
      <td>0.0</td>
      <td>1919.7999</td>
      <td>N</td>
    </tr>
  </tbody>
</table>
<p>9930 rows × 13 columns</p>
</div>




```python
# reset_index활용하여 기존 DataFrame으로 변환  (set_index <-> reset_index)   
cust.set_index(['cust_class','sex_type']).reset_index()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_class</th>
      <th>sex_type</th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>age</th>
      <th>efct_svc_count</th>
      <th>dt_stop_yn</th>
      <th>npay_yn</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
      <th>termination_yn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>C</td>
      <td>F</td>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>28</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>2640.0000</td>
      <td>792.000000</td>
      <td>1584.0000</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>1</th>
      <td>_</td>
      <td>_</td>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>300.0000</td>
      <td>90.000000</td>
      <td>180.0000</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>2</th>
      <td>E</td>
      <td>F</td>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>24</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>16840.0000</td>
      <td>2526.000000</td>
      <td>6983.0000</td>
      <td>0.0</td>
      <td>6981.0000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>3</th>
      <td>F</td>
      <td>F</td>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>32</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>15544.7334</td>
      <td>2331.710010</td>
      <td>6750.4666</td>
      <td>0.0</td>
      <td>6508.8000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>4</th>
      <td>D</td>
      <td>M</td>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>18</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>4700.0000</td>
      <td>0.000000</td>
      <td>4502.0000</td>
      <td>0.0</td>
      <td>4507.7000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>9925</th>
      <td>C</td>
      <td>F</td>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>15</td>
      <td>1</td>
      <td>N</td>
      <td>Y</td>
      <td>1296.0999</td>
      <td>194.414985</td>
      <td>643.1001</td>
      <td>0.0</td>
      <td>852.5499</td>
      <td>N</td>
    </tr>
    <tr>
      <th>9926</th>
      <td>G</td>
      <td>M</td>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>12</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>13799.6666</td>
      <td>2069.949990</td>
      <td>10605.9266</td>
      <td>0.0</td>
      <td>10603.9266</td>
      <td>N</td>
    </tr>
    <tr>
      <th>9927</th>
      <td>C</td>
      <td>_</td>
      <td>202006</td>
      <td>20200630</td>
      <td>10005</td>
      <td>_</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>1396.2000</td>
      <td>1206.000000</td>
      <td>0.0000</td>
      <td>1212.0</td>
      <td>0.0000</td>
      <td>N</td>
    </tr>
    <tr>
      <th>9928</th>
      <td>C</td>
      <td>F</td>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>40</td>
      <td>0</td>
      <td>N</td>
      <td>N</td>
      <td>3140.0000</td>
      <td>942.000000</td>
      <td>1884.0000</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>Y</td>
    </tr>
    <tr>
      <th>9929</th>
      <td>C</td>
      <td>F</td>
      <td>202006</td>
      <td>20200630</td>
      <td>10001</td>
      <td>59</td>
      <td>1</td>
      <td>N</td>
      <td>N</td>
      <td>2436.9000</td>
      <td>365.535000</td>
      <td>1839.9000</td>
      <td>0.0</td>
      <td>1919.7999</td>
      <td>N</td>
    </tr>
  </tbody>
</table>
<p>9930 rows × 15 columns</p>
</div>




```python
# 멀티 인덱스 셋팅 후 인덱스 기준으로 groupby하기
# 'sex'와 'cp'를 기준으로 index를셋팅하고 index를 기준으로 groupby하고자 하는경우
# groupby의 level은 index가 있는 경우에 사용 
cust.set_index(['cust_class','sex_type']).groupby(level=[0]).mean()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>efct_svc_count</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
    </tr>
    <tr>
      <th>cust_class</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>C</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.347992</td>
      <td>1.019598</td>
      <td>3552.548591</td>
      <td>1689.963677</td>
      <td>1139.409155</td>
      <td>1236.575918</td>
      <td>623.090664</td>
    </tr>
    <tr>
      <th>D</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.122667</td>
      <td>1.047111</td>
      <td>7829.480212</td>
      <td>1590.890907</td>
      <td>4176.241962</td>
      <td>489.304579</td>
      <td>3309.849733</td>
    </tr>
    <tr>
      <th>E</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.075650</td>
      <td>1.189913</td>
      <td>11228.231434</td>
      <td>1795.634627</td>
      <td>6302.510076</td>
      <td>489.232177</td>
      <td>5371.352846</td>
    </tr>
    <tr>
      <th>F</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.077135</td>
      <td>1.433884</td>
      <td>14994.348233</td>
      <td>2047.064710</td>
      <td>8166.923501</td>
      <td>742.959676</td>
      <td>7389.011610</td>
    </tr>
    <tr>
      <th>G</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.013652</td>
      <td>1.523159</td>
      <td>16735.260101</td>
      <td>2005.347119</td>
      <td>9735.625736</td>
      <td>386.361783</td>
      <td>9617.168424</td>
    </tr>
    <tr>
      <th>H</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.000000</td>
      <td>2.113475</td>
      <td>20714.902939</td>
      <td>2282.967852</td>
      <td>10859.251396</td>
      <td>504.888362</td>
      <td>10836.495186</td>
    </tr>
    <tr>
      <th>_</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10002.797288</td>
      <td>3.306210</td>
      <td>21358.005450</td>
      <td>2518.150052</td>
      <td>11633.643589</td>
      <td>1945.066645</td>
      <td>2670.334370</td>
    </tr>
  </tbody>
</table>
</div>




```python
cust.set_index(['cust_class','sex_type']).groupby(level=[0,1]).mean()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>base_ym</th>
      <th>dpro_tgt_perd_val</th>
      <th>cust_ctg_type</th>
      <th>efct_svc_count</th>
      <th>r3m_avg_bill_amt</th>
      <th>r3m_A_avg_arpu_amt</th>
      <th>r3m_B_avg_arpu_amt</th>
      <th>r6m_A_avg_arpu_amt</th>
      <th>r6m_B_avg_arpu_amt</th>
    </tr>
    <tr>
      <th>cust_class</th>
      <th>sex_type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">C</th>
      <th>F</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.004711</td>
      <td>0.978799</td>
      <td>3804.342244</td>
      <td>1583.492691</td>
      <td>1326.369780</td>
      <td>1005.475117</td>
      <td>828.849523</td>
    </tr>
    <tr>
      <th>M</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.011278</td>
      <td>1.026316</td>
      <td>3155.385796</td>
      <td>1648.323176</td>
      <td>968.955465</td>
      <td>1237.865008</td>
      <td>556.026278</td>
    </tr>
    <tr>
      <th>_</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10004.977654</td>
      <td>1.173184</td>
      <td>4719.075980</td>
      <td>2442.474066</td>
      <td>1265.851368</td>
      <td>2325.028369</td>
      <td>45.812648</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">D</th>
      <th>F</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.003646</td>
      <td>1.040109</td>
      <td>7848.842709</td>
      <td>1377.127105</td>
      <td>4297.720359</td>
      <td>315.530984</td>
      <td>3761.540720</td>
    </tr>
    <tr>
      <th>M</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.007360</td>
      <td>1.045078</td>
      <td>7774.098954</td>
      <td>1742.249493</td>
      <td>4098.230598</td>
      <td>550.449533</td>
      <td>3054.969393</td>
    </tr>
    <tr>
      <th>_</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10005.000000</td>
      <td>1.196970</td>
      <td>8419.764574</td>
      <td>2651.074376</td>
      <td>3441.947276</td>
      <td>2370.593506</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">E</th>
      <th>F</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.000000</td>
      <td>1.148670</td>
      <td>11257.301485</td>
      <td>1623.670941</td>
      <td>6531.544954</td>
      <td>304.847684</td>
      <td>5998.054678</td>
    </tr>
    <tr>
      <th>M</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.000000</td>
      <td>1.222772</td>
      <td>11158.736812</td>
      <td>1905.210132</td>
      <td>6114.544589</td>
      <td>602.976972</td>
      <td>4923.250531</td>
    </tr>
    <tr>
      <th>_</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10005.000000</td>
      <td>1.458333</td>
      <td>12208.980550</td>
      <td>3607.386253</td>
      <td>4950.584995</td>
      <td>2526.413200</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">F</th>
      <th>F</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.000000</td>
      <td>1.275000</td>
      <td>14913.105272</td>
      <td>1935.092224</td>
      <td>8166.414828</td>
      <td>519.668193</td>
      <td>7656.897492</td>
    </tr>
    <tr>
      <th>M</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.000000</td>
      <td>1.560102</td>
      <td>15013.379957</td>
      <td>2081.920917</td>
      <td>8126.197332</td>
      <td>846.922216</td>
      <td>7423.372289</td>
    </tr>
    <tr>
      <th>_</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10004.733333</td>
      <td>1.533333</td>
      <td>16231.437767</td>
      <td>3527.225972</td>
      <td>9239.370660</td>
      <td>2796.554453</td>
      <td>778.444440</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">G</th>
      <th>F</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.000000</td>
      <td>1.435196</td>
      <td>16538.595017</td>
      <td>1941.946105</td>
      <td>9520.483640</td>
      <td>325.034607</td>
      <td>9461.716215</td>
    </tr>
    <tr>
      <th>M</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.000000</td>
      <td>1.583680</td>
      <td>16847.160637</td>
      <td>2032.943013</td>
      <td>9882.218237</td>
      <td>408.043516</td>
      <td>9777.235315</td>
    </tr>
    <tr>
      <th>_</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10004.111111</td>
      <td>1.666667</td>
      <td>20180.014811</td>
      <td>4247.300999</td>
      <td>10277.504440</td>
      <td>3223.738911</td>
      <td>2783.276289</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">H</th>
      <th>F</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.000000</td>
      <td>1.962264</td>
      <td>20154.938768</td>
      <td>2250.525648</td>
      <td>9926.724864</td>
      <td>289.192455</td>
      <td>9969.301691</td>
    </tr>
    <tr>
      <th>M</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.000000</td>
      <td>2.204545</td>
      <td>21052.154088</td>
      <td>2302.506907</td>
      <td>11420.886693</td>
      <td>634.796124</td>
      <td>11358.782177</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">_</th>
      <th>F</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.000000</td>
      <td>0.544248</td>
      <td>4304.582332</td>
      <td>910.064466</td>
      <td>2879.027895</td>
      <td>166.396450</td>
      <td>3301.780467</td>
    </tr>
    <tr>
      <th>M</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10001.007130</td>
      <td>0.618538</td>
      <td>4728.388010</td>
      <td>1124.726857</td>
      <td>2604.231501</td>
      <td>85.475068</td>
      <td>3039.238578</td>
    </tr>
    <tr>
      <th>_</th>
      <td>202006.0</td>
      <td>20200630.0</td>
      <td>10007.479381</td>
      <td>10.409794</td>
      <td>65268.733884</td>
      <td>6406.204426</td>
      <td>34887.732443</td>
      <td>6705.865106</td>
      <td>1401.342370</td>
    </tr>
  </tbody>
</table>
</div>



> ##### __1-7) aggregate(집계) 함수 사용하기__
> groupby 결과에 집계함수를 적용하여 그룹별(mean, max등) 데이터 확인 가능


```python
#그룹별로 한번에 데이터를 한번에 보는 경우
cust.set_index(['cust_class','sex_type']).groupby(level=[0,1]).aggregate([np.mean, np.max])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th></th>
      <th colspan="2" halign="left">base_ym</th>
      <th colspan="2" halign="left">dpro_tgt_perd_val</th>
      <th colspan="2" halign="left">cust_ctg_type</th>
      <th colspan="2" halign="left">efct_svc_count</th>
      <th colspan="2" halign="left">r3m_avg_bill_amt</th>
      <th colspan="2" halign="left">r3m_A_avg_arpu_amt</th>
      <th colspan="2" halign="left">r3m_B_avg_arpu_amt</th>
      <th colspan="2" halign="left">r6m_A_avg_arpu_amt</th>
      <th colspan="2" halign="left">r6m_B_avg_arpu_amt</th>
    </tr>
    <tr>
      <th></th>
      <th></th>
      <th>mean</th>
      <th>amax</th>
      <th>mean</th>
      <th>amax</th>
      <th>mean</th>
      <th>amax</th>
      <th>mean</th>
      <th>amax</th>
      <th>mean</th>
      <th>amax</th>
      <th>mean</th>
      <th>amax</th>
      <th>mean</th>
      <th>amax</th>
      <th>mean</th>
      <th>amax</th>
      <th>mean</th>
      <th>amax</th>
    </tr>
    <tr>
      <th>cust_class</th>
      <th>sex_type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">C</th>
      <th>F</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10001.004711</td>
      <td>10005</td>
      <td>0.978799</td>
      <td>3</td>
      <td>3804.342244</td>
      <td>6.815017e+04</td>
      <td>1583.492691</td>
      <td>4.810162e+04</td>
      <td>1326.369780</td>
      <td>1.443402e+04</td>
      <td>1005.475117</td>
      <td>1.031603e+04</td>
      <td>828.849523</td>
      <td>14432.0160</td>
    </tr>
    <tr>
      <th>M</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10001.011278</td>
      <td>10005</td>
      <td>1.026316</td>
      <td>5</td>
      <td>3155.385796</td>
      <td>2.306917e+04</td>
      <td>1648.323176</td>
      <td>1.477473e+04</td>
      <td>968.955465</td>
      <td>1.390940e+04</td>
      <td>1237.865008</td>
      <td>9.689333e+03</td>
      <td>556.026278</td>
      <td>14787.1166</td>
    </tr>
    <tr>
      <th>_</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10004.977654</td>
      <td>10005</td>
      <td>1.173184</td>
      <td>5</td>
      <td>4719.075980</td>
      <td>2.293453e+04</td>
      <td>2442.474066</td>
      <td>1.238933e+04</td>
      <td>1265.851368</td>
      <td>1.376072e+04</td>
      <td>2325.028369</td>
      <td>1.964850e+04</td>
      <td>45.812648</td>
      <td>8200.4640</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">D</th>
      <th>F</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10001.003646</td>
      <td>10005</td>
      <td>1.040109</td>
      <td>6</td>
      <td>7848.842709</td>
      <td>5.407650e+04</td>
      <td>1377.127105</td>
      <td>1.665367e+04</td>
      <td>4297.720359</td>
      <td>1.438200e+04</td>
      <td>315.530984</td>
      <td>8.964522e+03</td>
      <td>3761.540720</td>
      <td>14467.3334</td>
    </tr>
    <tr>
      <th>M</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10001.007360</td>
      <td>10005</td>
      <td>1.045078</td>
      <td>5</td>
      <td>7774.098954</td>
      <td>1.447397e+05</td>
      <td>1742.249493</td>
      <td>1.315815e+05</td>
      <td>4098.230598</td>
      <td>1.925570e+04</td>
      <td>550.449533</td>
      <td>2.749282e+04</td>
      <td>3054.969393</td>
      <td>18133.6304</td>
    </tr>
    <tr>
      <th>_</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10005.000000</td>
      <td>10005</td>
      <td>1.196970</td>
      <td>5</td>
      <td>8419.764574</td>
      <td>3.232967e+04</td>
      <td>2651.074376</td>
      <td>1.868697e+04</td>
      <td>3441.947276</td>
      <td>1.939780e+04</td>
      <td>2370.593506</td>
      <td>1.024273e+04</td>
      <td>0.000000</td>
      <td>0.0000</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">E</th>
      <th>F</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10001.000000</td>
      <td>10001</td>
      <td>1.148670</td>
      <td>6</td>
      <td>11257.301485</td>
      <td>5.226307e+04</td>
      <td>1623.670941</td>
      <td>1.637333e+04</td>
      <td>6531.544954</td>
      <td>1.753289e+04</td>
      <td>304.847684</td>
      <td>1.306933e+04</td>
      <td>5998.054678</td>
      <td>17306.4000</td>
    </tr>
    <tr>
      <th>M</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10001.000000</td>
      <td>10001</td>
      <td>1.222772</td>
      <td>7</td>
      <td>11158.736812</td>
      <td>1.055625e+05</td>
      <td>1905.210132</td>
      <td>3.797280e+04</td>
      <td>6114.544589</td>
      <td>4.347433e+04</td>
      <td>602.976972</td>
      <td>1.310073e+04</td>
      <td>4923.250531</td>
      <td>39802.3921</td>
    </tr>
    <tr>
      <th>_</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10005.000000</td>
      <td>10005</td>
      <td>1.458333</td>
      <td>5</td>
      <td>12208.980550</td>
      <td>1.644177e+04</td>
      <td>3607.386253</td>
      <td>8.696067e+03</td>
      <td>4950.584995</td>
      <td>9.865060e+03</td>
      <td>2526.413200</td>
      <td>8.704500e+03</td>
      <td>0.000000</td>
      <td>0.0000</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">F</th>
      <th>F</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10001.000000</td>
      <td>10001</td>
      <td>1.275000</td>
      <td>9</td>
      <td>14913.105272</td>
      <td>5.993527e+04</td>
      <td>1935.092224</td>
      <td>1.211230e+04</td>
      <td>8166.414828</td>
      <td>2.822429e+04</td>
      <td>519.668193</td>
      <td>1.295988e+04</td>
      <td>7656.897492</td>
      <td>29511.7824</td>
    </tr>
    <tr>
      <th>M</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10001.000000</td>
      <td>10001</td>
      <td>1.560102</td>
      <td>11</td>
      <td>15013.379957</td>
      <td>7.300037e+04</td>
      <td>2081.920917</td>
      <td>1.589153e+04</td>
      <td>8126.197332</td>
      <td>3.605447e+04</td>
      <td>846.922216</td>
      <td>1.706433e+04</td>
      <td>7423.372289</td>
      <td>33871.3333</td>
    </tr>
    <tr>
      <th>_</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10004.733333</td>
      <td>10005</td>
      <td>1.533333</td>
      <td>4</td>
      <td>16231.437767</td>
      <td>2.956300e+04</td>
      <td>3527.225972</td>
      <td>1.405020e+04</td>
      <td>9239.370660</td>
      <td>1.773780e+04</td>
      <td>2796.554453</td>
      <td>1.321063e+04</td>
      <td>778.444440</td>
      <td>11676.6666</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">G</th>
      <th>F</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10001.000000</td>
      <td>10001</td>
      <td>1.435196</td>
      <td>6</td>
      <td>16538.595017</td>
      <td>7.979563e+04</td>
      <td>1941.946105</td>
      <td>5.500240e+04</td>
      <td>9520.483640</td>
      <td>5.710153e+04</td>
      <td>325.034607</td>
      <td>1.559547e+04</td>
      <td>9461.716215</td>
      <td>48787.2333</td>
    </tr>
    <tr>
      <th>M</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10001.000000</td>
      <td>10001</td>
      <td>1.583680</td>
      <td>14</td>
      <td>16847.160637</td>
      <td>1.129005e+05</td>
      <td>2032.943013</td>
      <td>4.759945e+04</td>
      <td>9882.218237</td>
      <td>6.583656e+04</td>
      <td>408.043516</td>
      <td>1.954363e+04</td>
      <td>9777.235315</td>
      <td>64947.0920</td>
    </tr>
    <tr>
      <th>_</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10004.111111</td>
      <td>10005</td>
      <td>1.666667</td>
      <td>6</td>
      <td>20180.014811</td>
      <td>3.589550e+04</td>
      <td>4247.300999</td>
      <td>1.218147e+04</td>
      <td>10277.504440</td>
      <td>2.153730e+04</td>
      <td>3223.738911</td>
      <td>1.268773e+04</td>
      <td>2783.276289</td>
      <td>15642.2866</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">H</th>
      <th>F</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10001.000000</td>
      <td>10001</td>
      <td>1.962264</td>
      <td>6</td>
      <td>20154.938768</td>
      <td>7.471997e+04</td>
      <td>2250.525648</td>
      <td>1.120800e+04</td>
      <td>9926.724864</td>
      <td>1.826570e+04</td>
      <td>289.192455</td>
      <td>2.960000e+03</td>
      <td>9969.301691</td>
      <td>18233.2224</td>
    </tr>
    <tr>
      <th>M</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10001.000000</td>
      <td>10001</td>
      <td>2.204545</td>
      <td>9</td>
      <td>21052.154088</td>
      <td>9.613610e+04</td>
      <td>2302.506907</td>
      <td>1.442042e+04</td>
      <td>11420.886693</td>
      <td>3.036068e+04</td>
      <td>634.796124</td>
      <td>1.236263e+04</td>
      <td>11358.782177</td>
      <td>30402.5750</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">_</th>
      <th>F</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10001.000000</td>
      <td>10001</td>
      <td>0.544248</td>
      <td>4</td>
      <td>4304.582332</td>
      <td>3.024210e+04</td>
      <td>910.064466</td>
      <td>2.749282e+04</td>
      <td>2879.027895</td>
      <td>1.659055e+04</td>
      <td>166.396450</td>
      <td>2.302815e+04</td>
      <td>3301.780467</td>
      <td>16505.8102</td>
    </tr>
    <tr>
      <th>M</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10001.007130</td>
      <td>10005</td>
      <td>0.618538</td>
      <td>5</td>
      <td>4728.388010</td>
      <td>1.320952e+05</td>
      <td>1124.726857</td>
      <td>9.946849e+04</td>
      <td>2604.231501</td>
      <td>1.704006e+04</td>
      <td>85.475068</td>
      <td>4.409887e+03</td>
      <td>3039.238578</td>
      <td>16932.6252</td>
    </tr>
    <tr>
      <th>_</th>
      <td>202006</td>
      <td>202006</td>
      <td>20200630</td>
      <td>20200630</td>
      <td>10007.479381</td>
      <td>10010</td>
      <td>10.409794</td>
      <td>905</td>
      <td>65268.733884</td>
      <td>1.281568e+07</td>
      <td>6406.204426</td>
      <td>1.188998e+06</td>
      <td>34887.732443</td>
      <td>7.689409e+06</td>
      <td>6705.865106</td>
      <td>1.208498e+06</td>
      <td>1401.342370</td>
      <td>18796.6266</td>
    </tr>
  </tbody>
</table>
</div>



# __2. pivot / pivot_table 함수 활용__

### <b>2-1. pivot 은 뭘까?</b>
> - dataframe의 형태를 변경
> - 여러 분류로 섞인 **행 데이터를 열 데이터로 회전** 시키는 것
>   - pivot의 사전적의미 : (축을 중심으로)회전하다, 회전시키다. 
> - pivot형태 : pandas.pivot(index, columns, values) 로 사용할 컴럼을 명시


```python
import numpy as np
import pandas as pd
```


```python
data = pd.DataFrame({'cust_id': ['cust_1', 'cust_1', 'cust_1', 'cust_2', 'cust_2', 'cust_2', 'cust_3', 'cust_3', 'cust_3'],
                  'prod_cd': ['p1', 'p2', 'p3', 'p1', 'p2', 'p3', 'p1', 'p2', 'p3'],
                  'grade' : ['A', 'A', 'A', 'A', 'A', 'A', 'B', 'B', 'B'],
                  'pch_amt': [30, 10, 0, 40, 15, 30, 0, 0, 10]})
data
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_id</th>
      <th>prod_cd</th>
      <th>grade</th>
      <th>pch_amt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>cust_1</td>
      <td>p1</td>
      <td>A</td>
      <td>30</td>
    </tr>
    <tr>
      <th>1</th>
      <td>cust_1</td>
      <td>p2</td>
      <td>A</td>
      <td>10</td>
    </tr>
    <tr>
      <th>2</th>
      <td>cust_1</td>
      <td>p3</td>
      <td>A</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>cust_2</td>
      <td>p1</td>
      <td>A</td>
      <td>40</td>
    </tr>
    <tr>
      <th>4</th>
      <td>cust_2</td>
      <td>p2</td>
      <td>A</td>
      <td>15</td>
    </tr>
    <tr>
      <th>5</th>
      <td>cust_2</td>
      <td>p3</td>
      <td>A</td>
      <td>30</td>
    </tr>
    <tr>
      <th>6</th>
      <td>cust_3</td>
      <td>p1</td>
      <td>B</td>
      <td>0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>cust_3</td>
      <td>p2</td>
      <td>B</td>
      <td>0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>cust_3</td>
      <td>p3</td>
      <td>B</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 행(row)는 고객ID(cust_id), 열(col)은 상품코드(prod_cd), 값은 구매금액(pch_amt)을 pivot릏 활용하여 만들어보기
# (직접 타이핑해보세요)
data.pivot(index='cust_id', columns='prod_cd', values='pch_amt')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>prod_cd</th>
      <th>p1</th>
      <th>p2</th>
      <th>p3</th>
    </tr>
    <tr>
      <th>cust_id</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>cust_1</th>
      <td>30</td>
      <td>10</td>
      <td>0</td>
    </tr>
    <tr>
      <th>cust_2</th>
      <td>40</td>
      <td>15</td>
      <td>30</td>
    </tr>
    <tr>
      <th>cust_3</th>
      <td>0</td>
      <td>0</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.pivot('cust_id', 'prod_cd', 'pch_amt')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>prod_cd</th>
      <th>p1</th>
      <th>p2</th>
      <th>p3</th>
    </tr>
    <tr>
      <th>cust_id</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>cust_1</th>
      <td>30</td>
      <td>10</td>
      <td>0</td>
    </tr>
    <tr>
      <th>cust_2</th>
      <td>40</td>
      <td>15</td>
      <td>30</td>
    </tr>
    <tr>
      <th>cust_3</th>
      <td>0</td>
      <td>0</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>



### <b>2-2. Pivot_table은 뭘까?</b>
> pivot_table형태 : pandas.pivot_table(data, index, columns, aggfunc)


```python
# pivot_table을 활용하여 위와 동일하게 만들기
data.pivot_table(index = 'cust_id', columns ='prod_cd', values ='pch_amt')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>prod_cd</th>
      <th>p1</th>
      <th>p2</th>
      <th>p3</th>
    </tr>
    <tr>
      <th>cust_id</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>cust_1</th>
      <td>30</td>
      <td>10</td>
      <td>0</td>
    </tr>
    <tr>
      <th>cust_2</th>
      <td>40</td>
      <td>15</td>
      <td>30</td>
    </tr>
    <tr>
      <th>cust_3</th>
      <td>0</td>
      <td>0</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>



### <b>2-3. Pivot과 Pivot_table의 차이는뭘까 ?</b>

> pivot은 안되고 pivot_table만을 사용해야 하는 경우가 있음

#### <b>1) index가 2개 이상인 경우</b>


```python
data.pivot(index = ['cust_id','grade'], columns ='prod_cd', values ='pch_amt')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>prod_cd</th>
      <th>p1</th>
      <th>p2</th>
      <th>p3</th>
    </tr>
    <tr>
      <th>cust_id</th>
      <th>grade</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>cust_1</th>
      <th>A</th>
      <td>30</td>
      <td>10</td>
      <td>0</td>
    </tr>
    <tr>
      <th>cust_2</th>
      <th>A</th>
      <td>40</td>
      <td>15</td>
      <td>30</td>
    </tr>
    <tr>
      <th>cust_3</th>
      <th>B</th>
      <td>0</td>
      <td>0</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.pivot_table(index = ['cust_id','grade'], columns ='prod_cd', values ='pch_amt')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>prod_cd</th>
      <th>p1</th>
      <th>p2</th>
      <th>p3</th>
    </tr>
    <tr>
      <th>cust_id</th>
      <th>grade</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>cust_1</th>
      <th>A</th>
      <td>30</td>
      <td>10</td>
      <td>0</td>
    </tr>
    <tr>
      <th>cust_2</th>
      <th>A</th>
      <td>40</td>
      <td>15</td>
      <td>30</td>
    </tr>
    <tr>
      <th>cust_3</th>
      <th>B</th>
      <td>0</td>
      <td>0</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>



#### <b>2) columns가 2개 이상인 경우</b>



```python
data.pivot(index = 'cust_id', columns =['grade','prod_cd'], values ='pch_amt')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th>grade</th>
      <th colspan="3" halign="left">A</th>
      <th colspan="3" halign="left">B</th>
    </tr>
    <tr>
      <th>prod_cd</th>
      <th>p1</th>
      <th>p2</th>
      <th>p3</th>
      <th>p1</th>
      <th>p2</th>
      <th>p3</th>
    </tr>
    <tr>
      <th>cust_id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>cust_1</th>
      <td>30.0</td>
      <td>10.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>cust_2</th>
      <td>40.0</td>
      <td>15.0</td>
      <td>30.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>cust_3</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>10.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.pivot_table(index = 'cust_id', columns =['grade','prod_cd'], values ='pch_amt')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th>grade</th>
      <th colspan="3" halign="left">A</th>
      <th colspan="3" halign="left">B</th>
    </tr>
    <tr>
      <th>prod_cd</th>
      <th>p1</th>
      <th>p2</th>
      <th>p3</th>
      <th>p1</th>
      <th>p2</th>
      <th>p3</th>
    </tr>
    <tr>
      <th>cust_id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>cust_1</th>
      <td>30.0</td>
      <td>10.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>cust_2</th>
      <td>40.0</td>
      <td>15.0</td>
      <td>30.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>cust_3</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>10.0</td>
    </tr>
  </tbody>
</table>
</div>



#### <b>3) 중복 값이 있는 경우</b>

> - pivot은 중복 값이 있는 경우 valueError를 반환함
> - pivot_table은 aggregation 함수를 활용하여 처리


```python
#index로 쓰인 grade가 중복이 있음 이러면 에러가 남 pivot_table을 쓰면 aggregation이 적용됨
#data.pivot(index='grade', columns='prod_cd', values='pch_amt')  
```


```python
#index로 쓰인 grade가 중복이 있음
data.pivot_table(index='grade', columns='prod_cd', values='pch_amt')  
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>prod_cd</th>
      <th>p1</th>
      <th>p2</th>
      <th>p3</th>
    </tr>
    <tr>
      <th>grade</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>35.0</td>
      <td>12.5</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>10.0</td>
    </tr>
  </tbody>
</table>
</div>



### <b>2-4. pivot_table의 추가 살펴 보기</b>

>pivot_table은 aggregation 함수를 활용하여 처리


```python
# aggfunc를 sum으로 구하기 (직접 타이핑 해보세요)
data.pivot_table(index='grade', columns='prod_cd', values='pch_amt',  aggfunc=np.sum)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>prod_cd</th>
      <th>p1</th>
      <th>p2</th>
      <th>p3</th>
    </tr>
    <tr>
      <th>grade</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>70</td>
      <td>25</td>
      <td>30</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0</td>
      <td>0</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>




```python
# aggfunc를 sum으로 구하기 (직접 타이핑 해보세요)
data.pivot_table(index='grade', columns='prod_cd', values='pch_amt', aggfunc=np.sum)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>prod_cd</th>
      <th>p1</th>
      <th>p2</th>
      <th>p3</th>
    </tr>
    <tr>
      <th>grade</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>70</td>
      <td>25</td>
      <td>30</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0</td>
      <td>0</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 위와 같은결과(참고로 알아 두셔요)
pd.pivot_table(data, index='grade', columns='prod_cd', values='pch_amt', aggfunc=np.sum)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>prod_cd</th>
      <th>p1</th>
      <th>p2</th>
      <th>p3</th>
    </tr>
    <tr>
      <th>grade</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>70</td>
      <td>25</td>
      <td>30</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0</td>
      <td>0</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>




```python
# aggfunc를 mean으로 구하기(default가 mean임) (직접 타이핑 해보세요)
data.pivot_table(index='grade', columns='prod_cd', values='pch_amt', aggfunc=np.mean)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>prod_cd</th>
      <th>p1</th>
      <th>p2</th>
      <th>p3</th>
    </tr>
    <tr>
      <th>grade</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>35.0</td>
      <td>12.5</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>10.0</td>
    </tr>
  </tbody>
</table>
</div>



# __3. stack, unstack 함수 활용__


```python
df = pd.DataFrame({
    '지역': ['서울', '서울', '서울', '경기', '경기', '부산', '서울', '서울', '부산', '경기', '경기', '경기'],
    '요일': ['월요일', '화요일', '수요일', '월요일', '화요일', '월요일', '목요일', '금요일', '화요일', '수요일', '목요일', '금요일'],
    '강수량': [100, 80, 1000, 200, 200, 100, 50, 100, 200, 100, 50, 100],
    '강수확률': [80, 70, 90, 10, 20, 30, 50, 90, 20, 80, 50, 10]})

df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>지역</th>
      <th>요일</th>
      <th>강수량</th>
      <th>강수확률</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>서울</td>
      <td>월요일</td>
      <td>100</td>
      <td>80</td>
    </tr>
    <tr>
      <th>1</th>
      <td>서울</td>
      <td>화요일</td>
      <td>80</td>
      <td>70</td>
    </tr>
    <tr>
      <th>2</th>
      <td>서울</td>
      <td>수요일</td>
      <td>1000</td>
      <td>90</td>
    </tr>
    <tr>
      <th>3</th>
      <td>경기</td>
      <td>월요일</td>
      <td>200</td>
      <td>10</td>
    </tr>
    <tr>
      <th>4</th>
      <td>경기</td>
      <td>화요일</td>
      <td>200</td>
      <td>20</td>
    </tr>
    <tr>
      <th>5</th>
      <td>부산</td>
      <td>월요일</td>
      <td>100</td>
      <td>30</td>
    </tr>
    <tr>
      <th>6</th>
      <td>서울</td>
      <td>목요일</td>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <th>7</th>
      <td>서울</td>
      <td>금요일</td>
      <td>100</td>
      <td>90</td>
    </tr>
    <tr>
      <th>8</th>
      <td>부산</td>
      <td>화요일</td>
      <td>200</td>
      <td>20</td>
    </tr>
    <tr>
      <th>9</th>
      <td>경기</td>
      <td>수요일</td>
      <td>100</td>
      <td>80</td>
    </tr>
    <tr>
      <th>10</th>
      <td>경기</td>
      <td>목요일</td>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <th>11</th>
      <td>경기</td>
      <td>금요일</td>
      <td>100</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>



### <b>3-1. stack & unstack</b>

> - **stack** : 컬럼 레벨에서 인덱스 레벨로 dataframe 변경
>  - 즉, 데이터를 row 레벨로 쌓아올리는 개념으로 이해하면 쉬움
> - **unstack** : 인덱스 레벨에서 컬럼 레벨로 dataframe 변경
>  - stack의 반대 operation
> - 둘은 역의 관계에 있음


```python
# '지역'과 '요일'두개로 인덱스를 설정하고 별도의 DataFrame으로 설정 하기 - (직접 타이핑 해보세요)
new_df = df.set_index(['지역', '요일'])
new_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>강수량</th>
      <th>강수확률</th>
    </tr>
    <tr>
      <th>지역</th>
      <th>요일</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">서울</th>
      <th>월요일</th>
      <td>100</td>
      <td>80</td>
    </tr>
    <tr>
      <th>화요일</th>
      <td>80</td>
      <td>70</td>
    </tr>
    <tr>
      <th>수요일</th>
      <td>1000</td>
      <td>90</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">경기</th>
      <th>월요일</th>
      <td>200</td>
      <td>10</td>
    </tr>
    <tr>
      <th>화요일</th>
      <td>200</td>
      <td>20</td>
    </tr>
    <tr>
      <th>부산</th>
      <th>월요일</th>
      <td>100</td>
      <td>30</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">서울</th>
      <th>목요일</th>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <th>금요일</th>
      <td>100</td>
      <td>90</td>
    </tr>
    <tr>
      <th>부산</th>
      <th>화요일</th>
      <td>200</td>
      <td>20</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">경기</th>
      <th>수요일</th>
      <td>100</td>
      <td>80</td>
    </tr>
    <tr>
      <th>목요일</th>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <th>금요일</th>
      <td>100</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>




```python
new_df[['강수량']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>강수량</th>
    </tr>
    <tr>
      <th>지역</th>
      <th>요일</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">서울</th>
      <th>월요일</th>
      <td>100</td>
    </tr>
    <tr>
      <th>화요일</th>
      <td>80</td>
    </tr>
    <tr>
      <th>수요일</th>
      <td>1000</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">경기</th>
      <th>월요일</th>
      <td>200</td>
    </tr>
    <tr>
      <th>화요일</th>
      <td>200</td>
    </tr>
    <tr>
      <th>부산</th>
      <th>월요일</th>
      <td>100</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">서울</th>
      <th>목요일</th>
      <td>50</td>
    </tr>
    <tr>
      <th>금요일</th>
      <td>100</td>
    </tr>
    <tr>
      <th>부산</th>
      <th>화요일</th>
      <td>200</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">경기</th>
      <th>수요일</th>
      <td>100</td>
    </tr>
    <tr>
      <th>목요일</th>
      <td>50</td>
    </tr>
    <tr>
      <th>금요일</th>
      <td>100</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 첫번째 레벨의 인덱스(지역)를 컬럼으로 이동 / 인덱스도 레벨이 있음 
new_df.unstack(0)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="3" halign="left">강수량</th>
      <th colspan="3" halign="left">강수확률</th>
    </tr>
    <tr>
      <th>지역</th>
      <th>경기</th>
      <th>부산</th>
      <th>서울</th>
      <th>경기</th>
      <th>부산</th>
      <th>서울</th>
    </tr>
    <tr>
      <th>요일</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>금요일</th>
      <td>100.0</td>
      <td>NaN</td>
      <td>100.0</td>
      <td>10.0</td>
      <td>NaN</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>목요일</th>
      <td>50.0</td>
      <td>NaN</td>
      <td>50.0</td>
      <td>50.0</td>
      <td>NaN</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>수요일</th>
      <td>100.0</td>
      <td>NaN</td>
      <td>1000.0</td>
      <td>80.0</td>
      <td>NaN</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>월요일</th>
      <td>200.0</td>
      <td>100.0</td>
      <td>100.0</td>
      <td>10.0</td>
      <td>30.0</td>
      <td>80.0</td>
    </tr>
    <tr>
      <th>화요일</th>
      <td>200.0</td>
      <td>200.0</td>
      <td>80.0</td>
      <td>20.0</td>
      <td>20.0</td>
      <td>70.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 두번째 레벨의 인덱스를 컬럼으로 이동
new_df.unstack(1)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="5" halign="left">강수량</th>
      <th colspan="5" halign="left">강수확률</th>
    </tr>
    <tr>
      <th>요일</th>
      <th>금요일</th>
      <th>목요일</th>
      <th>수요일</th>
      <th>월요일</th>
      <th>화요일</th>
      <th>금요일</th>
      <th>목요일</th>
      <th>수요일</th>
      <th>월요일</th>
      <th>화요일</th>
    </tr>
    <tr>
      <th>지역</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>경기</th>
      <td>100.0</td>
      <td>50.0</td>
      <td>100.0</td>
      <td>200.0</td>
      <td>200.0</td>
      <td>10.0</td>
      <td>50.0</td>
      <td>80.0</td>
      <td>10.0</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>부산</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>100.0</td>
      <td>200.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>30.0</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>서울</th>
      <td>100.0</td>
      <td>50.0</td>
      <td>1000.0</td>
      <td>100.0</td>
      <td>80.0</td>
      <td>90.0</td>
      <td>50.0</td>
      <td>90.0</td>
      <td>80.0</td>
      <td>70.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
new_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>강수량</th>
      <th>강수확률</th>
    </tr>
    <tr>
      <th>지역</th>
      <th>요일</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">서울</th>
      <th>월요일</th>
      <td>100</td>
      <td>80</td>
    </tr>
    <tr>
      <th>화요일</th>
      <td>80</td>
      <td>70</td>
    </tr>
    <tr>
      <th>수요일</th>
      <td>1000</td>
      <td>90</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">경기</th>
      <th>월요일</th>
      <td>200</td>
      <td>10</td>
    </tr>
    <tr>
      <th>화요일</th>
      <td>200</td>
      <td>20</td>
    </tr>
    <tr>
      <th>부산</th>
      <th>월요일</th>
      <td>100</td>
      <td>30</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">서울</th>
      <th>목요일</th>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <th>금요일</th>
      <td>100</td>
      <td>90</td>
    </tr>
    <tr>
      <th>부산</th>
      <th>화요일</th>
      <td>200</td>
      <td>20</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">경기</th>
      <th>수요일</th>
      <td>100</td>
      <td>80</td>
    </tr>
    <tr>
      <th>목요일</th>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <th>금요일</th>
      <td>100</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>




```python
# new_df.unstack(0)상태에서 첫번째 레벨의 컬럼(강수량과 강수확률)을 인덱스로 이동(stack(0))
new_df.unstack(0).stack(0)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>지역</th>
      <th>경기</th>
      <th>부산</th>
      <th>서울</th>
    </tr>
    <tr>
      <th>요일</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">금요일</th>
      <th>강수량</th>
      <td>100.0</td>
      <td>NaN</td>
      <td>100.0</td>
    </tr>
    <tr>
      <th>강수확률</th>
      <td>10.0</td>
      <td>NaN</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">목요일</th>
      <th>강수량</th>
      <td>50.0</td>
      <td>NaN</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>강수확률</th>
      <td>50.0</td>
      <td>NaN</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">수요일</th>
      <th>강수량</th>
      <td>100.0</td>
      <td>NaN</td>
      <td>1000.0</td>
    </tr>
    <tr>
      <th>강수확률</th>
      <td>80.0</td>
      <td>NaN</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">월요일</th>
      <th>강수량</th>
      <td>200.0</td>
      <td>100.0</td>
      <td>100.0</td>
    </tr>
    <tr>
      <th>강수확률</th>
      <td>10.0</td>
      <td>30.0</td>
      <td>80.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">화요일</th>
      <th>강수량</th>
      <td>200.0</td>
      <td>200.0</td>
      <td>80.0</td>
    </tr>
    <tr>
      <th>강수확률</th>
      <td>20.0</td>
      <td>20.0</td>
      <td>70.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
new_df.unstack(0).stack(1)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>강수량</th>
      <th>강수확률</th>
    </tr>
    <tr>
      <th>요일</th>
      <th>지역</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">금요일</th>
      <th>경기</th>
      <td>100.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>서울</th>
      <td>100.0</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">목요일</th>
      <th>경기</th>
      <td>50.0</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>서울</th>
      <td>50.0</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">수요일</th>
      <th>경기</th>
      <td>100.0</td>
      <td>80.0</td>
    </tr>
    <tr>
      <th>서울</th>
      <td>1000.0</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">월요일</th>
      <th>경기</th>
      <td>200.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>부산</th>
      <td>100.0</td>
      <td>30.0</td>
    </tr>
    <tr>
      <th>서울</th>
      <td>100.0</td>
      <td>80.0</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">화요일</th>
      <th>경기</th>
      <td>200.0</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>부산</th>
      <td>200.0</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>서울</th>
      <td>80.0</td>
      <td>70.0</td>
    </tr>
  </tbody>
</table>
</div>



# 쉬운예제 : stack은 키가 커지고, unstack은 옆으로 커진다.ㅎㅎㅎㅎ (쉬운예지)
>- 밑에는 샘플


```python
sample = pd.DataFrame([['동민', '철수', '영희'], [176, 173, 160]],
                     index=['이름', '키'], columns=['조', '김', '이'])
sample
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>조</th>
      <th>김</th>
      <th>이</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>이름</th>
      <td>동민</td>
      <td>철수</td>
      <td>영희</td>
    </tr>
    <tr>
      <th>키</th>
      <td>176</td>
      <td>173</td>
      <td>160</td>
    </tr>
  </tbody>
</table>
</div>




```python
ex = sample.stack()
ex
```




    이름  조     동민
        김     철수
        이     영희
    키   조    176
        김    173
        이    160
    dtype: object




```python
# reset_index를 통해 index를 재정렬
ex.reset_index()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>level_0</th>
      <th>level_1</th>
      <th>0</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>이름</td>
      <td>조</td>
      <td>동민</td>
    </tr>
    <tr>
      <th>1</th>
      <td>이름</td>
      <td>김</td>
      <td>철수</td>
    </tr>
    <tr>
      <th>2</th>
      <td>이름</td>
      <td>이</td>
      <td>영희</td>
    </tr>
    <tr>
      <th>3</th>
      <td>키</td>
      <td>조</td>
      <td>176</td>
    </tr>
    <tr>
      <th>4</th>
      <td>키</td>
      <td>김</td>
      <td>173</td>
    </tr>
    <tr>
      <th>5</th>
      <td>키</td>
      <td>이</td>
      <td>160</td>
    </tr>
  </tbody>
</table>
</div>




```python
ux = sample.unstack()
ux
```




    조  이름     동민
       키     176
    김  이름     철수
       키     173
    이  이름     영희
       키     160
    dtype: object



# Chapter 3. DataFrame 병합하기

# __1. concat함수 활용__

두 개 이상의 데이터프레임을 하나로 합치는 데이터 병합(merge)이나 연결(concatenate)을 지원합니다. 


```python
import pandas as pd
import numpy as np
```

### <b>1-1. concat 함수 사용하여 DataFrame 병합하기</b>

> - pandas.concat 함수  (배열결합 : concatenate)
>  - 데이터의 속성 형태가 동일한 데이터 셋 끼리 합칠때 사용 (DataFrame을 물리적으로 붙여주는 함수)
> - 열 or 행 레벨로 병합하는 것

#### <b>1) column명이 같은 경우</b>
>  ignore_index, axis 활용


```python
df1 = pd.DataFrame({'key1' : [0,1,2,3,4], 'value1' : ['a', 'b', 'c','d','e']}, index=[0,1,2,3,4])
df2 = pd.DataFrame({'key1' : [3,4,5,6,7], 'value1' : ['c','d','e','f','g']}, index=[3,4,5,6,7])
```


```python
df1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>key1</th>
      <th>value1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>b</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>c</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>d</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>e</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>key1</th>
      <th>value1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>c</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>d</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>e</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>f</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>g</td>
    </tr>
  </tbody>
</table>
</div>



> ##### __concat함수 옵션__

> - **ignore_index** : 기존 index를 무시하고자 하는 경우
>   - False : 기존 index유지(default) / True : 기존 index무시(index재배열)
> - **axis**
>   - 0 : 위+아래로 합치기(row레벨) / 1 : 왼쪽+오른쪽으로 합치기(col레벨)


```python
# ignore_index에 대한이해  (직접 타이핑 해보세요)
# pd.concat([df1, df2], ignore_index=False)
pd.concat([df1,df2], ignore_index=False)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>key1</th>
      <th>value1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>b</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>c</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>d</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>e</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>c</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>d</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>e</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>f</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>g</td>
    </tr>
  </tbody>
</table>
</div>




```python
# axis=0,1 비교해 보기  (직접 타이핑 해보세요)
pd.concat([df1, df2], axis =1)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>key1</th>
      <th>value1</th>
      <th>key1</th>
      <th>value1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.0</td>
      <td>a</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.0</td>
      <td>b</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2.0</td>
      <td>c</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3.0</td>
      <td>d</td>
      <td>3.0</td>
      <td>c</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4.0</td>
      <td>e</td>
      <td>4.0</td>
      <td>d</td>
    </tr>
    <tr>
      <th>5</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>e</td>
    </tr>
    <tr>
      <th>6</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>f</td>
    </tr>
    <tr>
      <th>7</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.0</td>
      <td>g</td>
    </tr>
  </tbody>
</table>
</div>



#### <b>2) column명이 다른 경우</b>

> * concat함수중에 join에 대한이해
> * join 방식은 outer의 경우 합집합, inner의 경우 교집합을 의미


```python
df3 = pd.DataFrame({'a':['a0','a1','a2', 'a3'], 'b':['b0','b1','b2','b3'], 'c':['c0','c1','c2','c3']}, index = [0,1,2,3])
df4 = pd.DataFrame({'a':['a2','a3','a4', 'a5'], 'b':['b2','b3','b4','b5'], 'c':['c2','c3','c4','c5'], 'd':['d1','d2','d3','d4']}, index = [2,3,4,5])
```


```python
df3
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>a0</td>
      <td>b0</td>
      <td>c0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>a1</td>
      <td>b1</td>
      <td>c1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>a2</td>
      <td>b2</td>
      <td>c2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>a3</td>
      <td>b3</td>
      <td>c3</td>
    </tr>
  </tbody>
</table>
</div>




```python
df4
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>a2</td>
      <td>b2</td>
      <td>c2</td>
      <td>d1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>a3</td>
      <td>b3</td>
      <td>c3</td>
      <td>d2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>a4</td>
      <td>b4</td>
      <td>c4</td>
      <td>d3</td>
    </tr>
    <tr>
      <th>5</th>
      <td>a5</td>
      <td>b5</td>
      <td>c5</td>
      <td>d4</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 두개 df를 합치고 (합집합으로) 인덱스를 새로 구성
pd.concat([df3,df4],ignore_index=True)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>a0</td>
      <td>b0</td>
      <td>c0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>a1</td>
      <td>b1</td>
      <td>c1</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>a2</td>
      <td>b2</td>
      <td>c2</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>a3</td>
      <td>b3</td>
      <td>c3</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>a2</td>
      <td>b2</td>
      <td>c2</td>
      <td>d1</td>
    </tr>
    <tr>
      <th>5</th>
      <td>a3</td>
      <td>b3</td>
      <td>c3</td>
      <td>d2</td>
    </tr>
    <tr>
      <th>6</th>
      <td>a4</td>
      <td>b4</td>
      <td>c4</td>
      <td>d3</td>
    </tr>
    <tr>
      <th>7</th>
      <td>a5</td>
      <td>b5</td>
      <td>c5</td>
      <td>d4</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 두개 df를 교집합으로 붙이고 , 인덱스는 기존 인덱스 사용 (ignore_index=false) 가 기본값
pd.concat([df3,df4],join='inner')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>a0</td>
      <td>b0</td>
      <td>c0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>a1</td>
      <td>b1</td>
      <td>c1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>a2</td>
      <td>b2</td>
      <td>c2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>a3</td>
      <td>b3</td>
      <td>c3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>a2</td>
      <td>b2</td>
      <td>c2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>a3</td>
      <td>b3</td>
      <td>c3</td>
    </tr>
    <tr>
      <th>4</th>
      <td>a4</td>
      <td>b4</td>
      <td>c4</td>
    </tr>
    <tr>
      <th>5</th>
      <td>a5</td>
      <td>b5</td>
      <td>c5</td>
    </tr>
  </tbody>
</table>
</div>



#### <b>3) index 중복 여부 확인</b>

> * concat함수중에 verify_integrity에 대한 이해
> * verify_integrity=False가 default임으로 error발생을 하지 않음
> * verify_integrity=True인 경우 error 발생


```python
df5 = pd.DataFrame({'A':['A0','A1','A2'], 'B':['B0','B1','B2'], 'C':['C0','C1','C2'], 'D':['D0','D1','D2']}, index=['I0','I1','I2'])
df6 = pd.DataFrame({'A':['AA2','A3','A4'], 'B':['BB2','B3','B4'], 'C':['CC2','C3','C4'], 'D':['DD2','D3','D4']}, index=['I2','I3','I4'])
```


```python
df5
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
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
      <th>I0</th>
      <td>A0</td>
      <td>B0</td>
      <td>C0</td>
      <td>D0</td>
    </tr>
    <tr>
      <th>I1</th>
      <td>A1</td>
      <td>B1</td>
      <td>C1</td>
      <td>D1</td>
    </tr>
    <tr>
      <th>I2</th>
      <td>A2</td>
      <td>B2</td>
      <td>C2</td>
      <td>D2</td>
    </tr>
  </tbody>
</table>
</div>




```python
df6
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
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
      <th>I2</th>
      <td>AA2</td>
      <td>BB2</td>
      <td>CC2</td>
      <td>DD2</td>
    </tr>
    <tr>
      <th>I3</th>
      <td>A3</td>
      <td>B3</td>
      <td>C3</td>
      <td>D3</td>
    </tr>
    <tr>
      <th>I4</th>
      <td>A4</td>
      <td>B4</td>
      <td>C4</td>
      <td>D4</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.concat([df5, df6], verify_integrity=False)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
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
      <th>I0</th>
      <td>A0</td>
      <td>B0</td>
      <td>C0</td>
      <td>D0</td>
    </tr>
    <tr>
      <th>I1</th>
      <td>A1</td>
      <td>B1</td>
      <td>C1</td>
      <td>D1</td>
    </tr>
    <tr>
      <th>I2</th>
      <td>A2</td>
      <td>B2</td>
      <td>C2</td>
      <td>D2</td>
    </tr>
    <tr>
      <th>I2</th>
      <td>AA2</td>
      <td>BB2</td>
      <td>CC2</td>
      <td>DD2</td>
    </tr>
    <tr>
      <th>I3</th>
      <td>A3</td>
      <td>B3</td>
      <td>C3</td>
      <td>D3</td>
    </tr>
    <tr>
      <th>I4</th>
      <td>A4</td>
      <td>B4</td>
      <td>C4</td>
      <td>D4</td>
    </tr>
  </tbody>
</table>
</div>




```python
# index중복이있는 경우 error가 남 (인엑스 12가 중복)
pd.concat([df5, df6], verify_integrity=True)
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-101-26494bf41271> in <module>
          1 # index중복이있는 경우 error가 남 (인엑스 12가 중복)
    ----> 2 pd.concat([df5, df6], verify_integrity=True)
    

    /usr/local/lib/python3.6/dist-packages/pandas/core/reshape/concat.py in concat(objs, axis, join, ignore_index, keys, levels, names, verify_integrity, sort, copy)
        282         verify_integrity=verify_integrity,
        283         copy=copy,
    --> 284         sort=sort,
        285     )
        286 


    /usr/local/lib/python3.6/dist-packages/pandas/core/reshape/concat.py in __init__(self, objs, axis, join, keys, levels, names, ignore_index, verify_integrity, copy, sort)
        452         self.copy = copy
        453 
    --> 454         self.new_axes = self._get_new_axes()
        455 
        456     def get_result(self):


    /usr/local/lib/python3.6/dist-packages/pandas/core/reshape/concat.py in _get_new_axes(self)
        519         return [
        520             self._get_concat_axis() if i == self.bm_axis else self._get_comb_axis(i)
    --> 521             for i in range(ndim)
        522         ]
        523 


    /usr/local/lib/python3.6/dist-packages/pandas/core/reshape/concat.py in <listcomp>(.0)
        519         return [
        520             self._get_concat_axis() if i == self.bm_axis else self._get_comb_axis(i)
    --> 521             for i in range(ndim)
        522         ]
        523 


    /usr/local/lib/python3.6/dist-packages/pandas/core/reshape/concat.py in _get_concat_axis(self)
        578             )
        579 
    --> 580         self._maybe_check_integrity(concat_axis)
        581 
        582         return concat_axis


    /usr/local/lib/python3.6/dist-packages/pandas/core/reshape/concat.py in _maybe_check_integrity(self, concat_index)
        586             if not concat_index.is_unique:
        587                 overlap = concat_index[concat_index.duplicated()].unique()
    --> 588                 raise ValueError(f"Indexes have overlapping values: {overlap}")
        589 
        590 


    ValueError: Indexes have overlapping values: Index(['I2'], dtype='object')


# __2. merge & join 함수 활용__


### <b>2-1. DataFrame merge</b>

> - Database의 Table들을 Merge/Join하는 것과 유사함
> - 특정한 column(key)을 기준으로 병합
>   - join 방식: how 파라미터를 통해 명시(특정한 col을 바탕으로 join 하는 것)
     - inner: 기본 merge방법, 일치하는 값이 있는 경우 (Merge할 테이블의 데이터가 모두 있는 경우만 가지고 옴)
     - left: left outer join (왼쪽을 기준으로 오른쪽을 채움 - 오른쪽에 데이터 없으면 NaN)
     - right: right outer join
     - outer: full outer join  (Left와 Right를 합한 것)

merge 함수는 pandas 라이브러리에서 제공하는 DataFrame을 병합하는 함수입니다. 두 개의 DataFrame을 하나로 합치는 데 사용되며, SQL의 JOIN 연산과 유사한 방식으로 동작합니다. 이제 merge 함수의 각 인자를 설명하겠습니다.

left: (필수) 왼쪽으로 사용할 DataFrame입니다. 병합의 기준이 되는 DataFrame입니다.

right: (필수) 오른쪽으로 사용할 DataFrame입니다. 왼쪽 DataFrame과 병합될 DataFrame입니다.

how: (선택 사항, 기본값: 'inner') 병합 방법을 지정합니다. 'inner', 'outer', 'left', 'right' 등이 가능합니다.

  -'inner': 양쪽 DataFrame에 모두 존재하는 키 값만 병합합니다.
  -'outer': 양쪽 DataFrame에 있는 모든 키 값을 병합합니다.
  -'left': 왼쪽 DataFrame에 있는 키 값을 기준으로 병합합니다.
  -'right': 오른쪽 DataFrame에 있는 키 값을 기준으로 병합합니다.
  -on: (선택 사항) 병합에 사용할 열(키)의 이름이나 열의 이름을 담고 있는 리스트입니다. 만약 두 DataFrame의 열 이름이 다를 경우에는 여기서 왼쪽 DataFrame의 열 이름을 지정하고, right_on으로 오른쪽 DataFrame의 열 이름을 지정할 수 있습니다.

  -left_on: (선택 사항) 왼쪽 DataFrame의 병합에 사용할 열(키)의 이름입니다.

  -right_on: (선택 사항) 오른쪽 DataFrame의 병합에 사용할 열(키)의 이름입니다.

  -left_index: (선택 사항, 기본값: False) True로 설정하면 왼쪽 DataFrame의 인덱스를 사용하여 병합합니다.

  -right_index: (선택 사항, 기본값: False) True로 설정하면 오른쪽 DataFrame의 인덱스를 사용하여 병합합니다.

  -suffixes: (선택 사항, 기본값: ('_x', '_y')) 중복된 열 이름이 있는 경우 각 열 이름 뒤에 붙일 접미사를 지정합니다.

  -sort: (선택 사항, 기본값: False) True로 설정하면 병합된 결과를 열 이름 순서대로 정렬합니다.

  -merge 함수를 사용하면 두 개의 DataFrame을 특정 열을 기준으로 병합할 수 있습니다. 이를 통해 데이터를 조인하거나 결합하여 더 큰 데이터셋을 만들 수 있습니다.

```python
customer = pd.DataFrame({'cust_id' : np.arange(6), 
                    'name' : ['철수', '영희', '길동', '영수', '수민', '동건'], 
                    '나이' : [40, 20, 21, 30, 31, 18]})

orders = pd.DataFrame({'cust_id' : [1, 1, 2, 2, 2, 3, 3, 1, 4, 9], 
                    'item' : ['치약', '칫솔', '이어폰', '헤드셋', '수건', '생수', '수건', '치약', '생수', '케이스'], 
                    'quantity' : [1, 2, 1, 1, 3, 2, 2, 3, 2, 1]})

```


```python
customer
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_id</th>
      <th>name</th>
      <th>나이</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>철수</td>
      <td>40</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>영희</td>
      <td>20</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>길동</td>
      <td>21</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>영수</td>
      <td>30</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>수민</td>
      <td>31</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>동건</td>
      <td>18</td>
    </tr>
  </tbody>
</table>
</div>




```python
orders
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_id</th>
      <th>item</th>
      <th>quantity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>치약</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>칫솔</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>이어폰</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2</td>
      <td>헤드셋</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>수건</td>
      <td>3</td>
    </tr>
    <tr>
      <th>5</th>
      <td>3</td>
      <td>생수</td>
      <td>2</td>
    </tr>
    <tr>
      <th>6</th>
      <td>3</td>
      <td>수건</td>
      <td>2</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1</td>
      <td>치약</td>
      <td>3</td>
    </tr>
    <tr>
      <th>8</th>
      <td>4</td>
      <td>생수</td>
      <td>2</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>케이스</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



#### <b>1) merge함수의 on 옵션</b>

>  - join 대상이 되는 column 명시


```python
# 기본적인 Merge방식은 inner임 (직접 타이핑 해보세요)
# customer의 cust_id 5번과 orders의 cust_id 9번이 없는 것을 확인
# pd.merge(customer, orders)
pd.merge(customer, orders, on='cust_id') # 위의 내용과 같
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_id</th>
      <th>name</th>
      <th>나이</th>
      <th>item</th>
      <th>quantity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>영희</td>
      <td>20</td>
      <td>치약</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>영희</td>
      <td>20</td>
      <td>칫솔</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>영희</td>
      <td>20</td>
      <td>치약</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2</td>
      <td>길동</td>
      <td>21</td>
      <td>이어폰</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>길동</td>
      <td>21</td>
      <td>헤드셋</td>
      <td>1</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2</td>
      <td>길동</td>
      <td>21</td>
      <td>수건</td>
      <td>3</td>
    </tr>
    <tr>
      <th>6</th>
      <td>3</td>
      <td>영수</td>
      <td>30</td>
      <td>생수</td>
      <td>2</td>
    </tr>
    <tr>
      <th>7</th>
      <td>3</td>
      <td>영수</td>
      <td>30</td>
      <td>수건</td>
      <td>2</td>
    </tr>
    <tr>
      <th>8</th>
      <td>4</td>
      <td>수민</td>
      <td>31</td>
      <td>생수</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
# merge하고자 하는 컬럼 명칭을 on에 명시한다. 
# 여러개인 경우 리스트  일치하는 것만 가지고 옴
pd.merge(customer, orders, on='cust_id',how='inner')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_id</th>
      <th>name</th>
      <th>나이</th>
      <th>item</th>
      <th>quantity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>영희</td>
      <td>20</td>
      <td>치약</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>영희</td>
      <td>20</td>
      <td>칫솔</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>영희</td>
      <td>20</td>
      <td>치약</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2</td>
      <td>길동</td>
      <td>21</td>
      <td>이어폰</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>길동</td>
      <td>21</td>
      <td>헤드셋</td>
      <td>1</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2</td>
      <td>길동</td>
      <td>21</td>
      <td>수건</td>
      <td>3</td>
    </tr>
    <tr>
      <th>6</th>
      <td>3</td>
      <td>영수</td>
      <td>30</td>
      <td>생수</td>
      <td>2</td>
    </tr>
    <tr>
      <th>7</th>
      <td>3</td>
      <td>영수</td>
      <td>30</td>
      <td>수건</td>
      <td>2</td>
    </tr>
    <tr>
      <th>8</th>
      <td>4</td>
      <td>수민</td>
      <td>31</td>
      <td>생수</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 왼쪽 테이블을 기준으로 Merge (여기서는 customer기준)
pd.merge(customer, orders, on='cust_id', how='left')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_id</th>
      <th>name</th>
      <th>나이</th>
      <th>item</th>
      <th>quantity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>철수</td>
      <td>40</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>영희</td>
      <td>20</td>
      <td>치약</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>영희</td>
      <td>20</td>
      <td>칫솔</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>영희</td>
      <td>20</td>
      <td>치약</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>길동</td>
      <td>21</td>
      <td>이어폰</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2</td>
      <td>길동</td>
      <td>21</td>
      <td>헤드셋</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2</td>
      <td>길동</td>
      <td>21</td>
      <td>수건</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>3</td>
      <td>영수</td>
      <td>30</td>
      <td>생수</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>3</td>
      <td>영수</td>
      <td>30</td>
      <td>수건</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>4</td>
      <td>수민</td>
      <td>31</td>
      <td>생수</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>5</td>
      <td>동건</td>
      <td>18</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 오른쪽 테이블을 기준으로 Merge (여기서는 orders기준)
pd.merge(customer, orders, on='cust_id', how='right')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_id</th>
      <th>name</th>
      <th>나이</th>
      <th>item</th>
      <th>quantity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>영희</td>
      <td>20.0</td>
      <td>치약</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>영희</td>
      <td>20.0</td>
      <td>칫솔</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>영희</td>
      <td>20.0</td>
      <td>치약</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2</td>
      <td>길동</td>
      <td>21.0</td>
      <td>이어폰</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>길동</td>
      <td>21.0</td>
      <td>헤드셋</td>
      <td>1</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2</td>
      <td>길동</td>
      <td>21.0</td>
      <td>수건</td>
      <td>3</td>
    </tr>
    <tr>
      <th>6</th>
      <td>3</td>
      <td>영수</td>
      <td>30.0</td>
      <td>생수</td>
      <td>2</td>
    </tr>
    <tr>
      <th>7</th>
      <td>3</td>
      <td>영수</td>
      <td>30.0</td>
      <td>수건</td>
      <td>2</td>
    </tr>
    <tr>
      <th>8</th>
      <td>4</td>
      <td>수민</td>
      <td>31.0</td>
      <td>생수</td>
      <td>2</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>케이스</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
# outer : Left와 Right를 합친 것
pd.merge(customer, orders, on='cust_id', how='outer')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_id</th>
      <th>name</th>
      <th>나이</th>
      <th>item</th>
      <th>quantity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>철수</td>
      <td>40.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>영희</td>
      <td>20.0</td>
      <td>치약</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>영희</td>
      <td>20.0</td>
      <td>칫솔</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>영희</td>
      <td>20.0</td>
      <td>치약</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>길동</td>
      <td>21.0</td>
      <td>이어폰</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2</td>
      <td>길동</td>
      <td>21.0</td>
      <td>헤드셋</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2</td>
      <td>길동</td>
      <td>21.0</td>
      <td>수건</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>3</td>
      <td>영수</td>
      <td>30.0</td>
      <td>생수</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>3</td>
      <td>영수</td>
      <td>30.0</td>
      <td>수건</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>4</td>
      <td>수민</td>
      <td>31.0</td>
      <td>생수</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>5</td>
      <td>동건</td>
      <td>18.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>11</th>
      <td>9</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>케이스</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
</div>



#### <b>2) index 기준으로 join하기</b>




```python
#cust_id를 기준으로 인덱스 생성하기 (set_index활용)  (직접 타이핑 해보세요)
# set_index 입력된 column 값으로 인덱스를 다시 구성한다.

cust1 = customer.set_index('cust_id')
order1 = orders.set_index('cust_id')


```


```python
cust1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>나이</th>
    </tr>
    <tr>
      <th>cust_id</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>철수</td>
      <td>40</td>
    </tr>
    <tr>
      <th>1</th>
      <td>영희</td>
      <td>20</td>
    </tr>
    <tr>
      <th>2</th>
      <td>길동</td>
      <td>21</td>
    </tr>
    <tr>
      <th>3</th>
      <td>영수</td>
      <td>30</td>
    </tr>
    <tr>
      <th>4</th>
      <td>수민</td>
      <td>31</td>
    </tr>
    <tr>
      <th>5</th>
      <td>동건</td>
      <td>18</td>
    </tr>
  </tbody>
</table>
</div>




```python
order1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>item</th>
      <th>quantity</th>
    </tr>
    <tr>
      <th>cust_id</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>치약</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>칫솔</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>이어폰</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>헤드셋</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>수건</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>생수</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>수건</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>치약</td>
      <td>3</td>
    </tr>
    <tr>
      <th>4</th>
      <td>생수</td>
      <td>2</td>
    </tr>
    <tr>
      <th>9</th>
      <td>케이스</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
# on을 명시할 필요 없이 index를 merge 하고자 하는 경우 
pd.merge(cust1, order1, left_index=True, right_index=True)
# pd.merge(cust1, order1, on='cust_id') #위와 동일


#inner와 동일한 형태
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>나이</th>
      <th>item</th>
      <th>quantity</th>
    </tr>
    <tr>
      <th>cust_id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>영희</td>
      <td>20</td>
      <td>치약</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>영희</td>
      <td>20</td>
      <td>칫솔</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>영희</td>
      <td>20</td>
      <td>치약</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>길동</td>
      <td>21</td>
      <td>이어폰</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>길동</td>
      <td>21</td>
      <td>헤드셋</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>길동</td>
      <td>21</td>
      <td>수건</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>영수</td>
      <td>30</td>
      <td>생수</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>영수</td>
      <td>30</td>
      <td>수건</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>수민</td>
      <td>31</td>
      <td>생수</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>



#### <b>연습문제1) 가장 많이 팔린 아이템은?</b>
  - Hint : merge, groupby, sort_values 활용
  - 아이템이 중요함으로 orders DF이 중요


```python
# 1. customer, orders 를 merge (how는?)
# 2. group_by이용하여 item 을 grouping후 sum
# 직접 type 해보세요 

tot = pd.merge(customer, orders, on='cust_id', how='right').groupby('item').sum()
tot


```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_id</th>
      <th>나이</th>
      <th>quantity</th>
    </tr>
    <tr>
      <th>item</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>생수</th>
      <td>7</td>
      <td>61.0</td>
      <td>4</td>
    </tr>
    <tr>
      <th>수건</th>
      <td>5</td>
      <td>51.0</td>
      <td>5</td>
    </tr>
    <tr>
      <th>이어폰</th>
      <td>2</td>
      <td>21.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>치약</th>
      <td>2</td>
      <td>40.0</td>
      <td>4</td>
    </tr>
    <tr>
      <th>칫솔</th>
      <td>1</td>
      <td>20.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>케이스</th>
      <td>9</td>
      <td>0.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>헤드셋</th>
      <td>2</td>
      <td>21.0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 3. sort_values를 이용하여 quantity를기준으로 sort + 내림차순으로 정렬
# 직접 type 해보세요 

tot.sort_values('quantity', ascending=False)

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_id</th>
      <th>나이</th>
      <th>quantity</th>
    </tr>
    <tr>
      <th>item</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>수건</th>
      <td>5</td>
      <td>51.0</td>
      <td>5</td>
    </tr>
    <tr>
      <th>생수</th>
      <td>7</td>
      <td>61.0</td>
      <td>4</td>
    </tr>
    <tr>
      <th>치약</th>
      <td>2</td>
      <td>40.0</td>
      <td>4</td>
    </tr>
    <tr>
      <th>칫솔</th>
      <td>1</td>
      <td>20.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>이어폰</th>
      <td>2</td>
      <td>21.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>케이스</th>
      <td>9</td>
      <td>0.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>헤드셋</th>
      <td>2</td>
      <td>21.0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



#### <b>연습문제2) 영희가 가장 많이 구매한 아이템은?</b>
   - 1.우선 사람과 아이템 별로 sum을 해서(groupby시 "이름"과 "아이템"기준으로 합을 구하고)
   - 2.loc을 활용하여 (영희의 row의 quantity만 확인)


```python
# 직접 type 해보세요
tot = pd.merge(customer, orders, on='cust_id', how='right')
tot.groupby(['name','item']).sum().loc['영희']



```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cust_id</th>
      <th>나이</th>
      <th>quantity</th>
    </tr>
    <tr>
      <th>item</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>치약</th>
      <td>2</td>
      <td>40.0</td>
      <td>4</td>
    </tr>
    <tr>
      <th>칫솔</th>
      <td>1</td>
      <td>20.0</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>



### <b>2-2. join 함수</b>

 - index가 있는 경우 사용(행 인덱스를 기준으로 결합)
 - 내부적으로 pandas.merge 함수를 기반으로 만들어짐
 - 기본적으로 index를 사용하여 left join
 - 형태 : Dataframe1.join(Dataframe2. how='left')


```python
cust1.join(order1, how='inner')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>나이</th>
      <th>item</th>
      <th>quantity</th>
    </tr>
    <tr>
      <th>cust_id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>영희</td>
      <td>20</td>
      <td>치약</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>영희</td>
      <td>20</td>
      <td>칫솔</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>영희</td>
      <td>20</td>
      <td>치약</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>길동</td>
      <td>21</td>
      <td>이어폰</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>길동</td>
      <td>21</td>
      <td>헤드셋</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>길동</td>
      <td>21</td>
      <td>수건</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>영수</td>
      <td>30</td>
      <td>생수</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>영수</td>
      <td>30</td>
      <td>수건</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>수민</td>
      <td>31</td>
      <td>생수</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>


