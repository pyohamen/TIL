# Pandas

> 판다스는 파이썬에서 가장 널리 사용되는 데이터 분석 라이브러리로 **Data Frame** 과 **Series** 자료구조를 사용한다.



## Series

> One-dimensional ndarray with **axis labels** (including time series).
>
> Ex) df[피처]

### Attributes

| Name         | description                           |
| ------------ | ------------------------------------- |
| Series.index | The index (axis labels) of the Series |

### Methods

| name               | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Series.tolist()    | Return a list of the values                                  |
| Series.iteritems() | Lazily iterate over (index, value) tuples.<br />Lazily 하게 iterate 한다는 것은 for 문 같은 반복문에서 Series 의 (idx, val) 튜플을 하나씩 꺼내쓰기 위함인 것<br />row 가 index 가 되는 Series 특성상 `for idx, val in enumerate():` 에서는 row 쓸 수 없기 때문에 필요한 것 같다. |
| Series.unique()    | Return unique values of Series object.<br />type 은 넘파이배열이다. |



## DataFrame

> Two-dimensional, size-mutable, potentially heterogeneous tabular data.
>
> 인덱스에 조건문을 넣어서 인덱스 할 수 있음 Ex) results = chipo_orderid_group[chipo_orderid_group.item_price >= 10]

### Getting data in/out

#### csv

- Writing to a csv file

  ```python
  df.to_csv('[name].csv')
  ```

- Reading frome a csv file

  ```python
  # file_path = '../파일명'
  # sep
  # csv 는 ','(default) tsv 는 '\t' 
  df = pd.read_csv(file_path, sep)
  ```

### Attributes

> Ref) df[피처] == df.피처
>
> DafaFrame 은 인덱싱 안에 조건문을 넣을 수 있다.
> Ex) df[df.피처 >= num] => df 중 조건문에 해당하는 row 만 취하는 df 를 반환

| Name     | description                                                  |
| -------- | ------------------------------------------------------------ |
| df.shape | Return a tuple representing the dimensionality of the DataFrame.<br />=> (how many row, how many 피처) |
| df.index | return index (row labels) of the df<br />RangeIndex(start = [num], stop = [num], step= [num]) |

### Methods

| Command                                   | description                                                  |
| ----------------------------------------- | ------------------------------------------------------------ |
| df.value_counts([subset, normalize, ...]) | Return a Series containing counts of unique rows in the DataFrame.<br />같은 행이 몇개인지 갯수의 내림차순 Series 를 반환하며, 순서 숫자 뿐만 아니라, 해당 행의 이름으로 인덱싱할 수 있다.<br />인자로 피처를 써도 되고<br />df[피처] 로 인덱싱한 df 에 인자없는 매서드를 걸어도 된다. |
| df.info()                                 | Print a concise summary of a DataFrame.                      |
| df.head([n])                              | Return the first *n* rows                                    |
| [df.groupby([by])](#DataFrame.groupby)    | Group DataFrame using a mapper or by a Series of columns.    |
| df.apply()                                | 이건 뭐... apply 안에서 적용되는 함수가 더 중요한데 따로 써야하나 고민이네<br />데이터전처리를 위해 사용함 |
| df.sort_values([by, ascending...])        | Sort by the values along either axis.                        |
| Df.drop_duplicates()                      | Return DataFrame with duplicate rows removed.                |
| df.fillna()c                              | 결측치들을 인자 값으로 바꿔준다.                             |
| df.corr()                                 | 상관관계 함수 인자로 method 가 있고 'pearson' 을 많이 쓴다.  |

### Property

| Command   | description                                                  |
| --------- | ------------------------------------------------------------ |
| df.iloc[] | 위치 정수를 기반으로 인덱싱한다 [] 는 열(column) 을 선택하지만, .loc, .iloc 은 행(row) 를 선택한다 |



## DataFrame.groupby

> df.groupby([by]) 함수에 의해 생성된 객체. 인자 별로 그룹화되어 있으며, 인자 별로 그룹된 것들의 어떤 피처를 어떤 연산한 결과를 value 로 가질 것인지
>
> df.groupby('그룹화인자')[대상 피처].어떤연산함수()

### Methods

| name    | description                                                |
| ------- | ---------------------------------------------------------- |
| Count() | 그냥 갯수 셈 (중복에 상관없이 그냥 행이 몇개인지 세는 듯?) |
| Sum()   | 대상 피처의 val 들을 누적 합 함                            |

