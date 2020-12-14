# Pandas

> 판다스는 파이썬에서 가장 널리 사용되는 데이터 분석 라이브러리로 **Data Frame** 과 **Series** 자료구조를 사용한다.

## Series

> One-dimensional ndarray with axis labels (including time series).

### Attributes

| Name         | description                           |
| ------------ | ------------------------------------- |
| Series.index | The index (axis labels) of the Series |

### Methods

| name               | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Series.tolist()    | Return a list of the values                                  |
| Series.iteritems() | Lazily iterate over (index, value) tuples.<br />Lazily 하게 iterate 한다는 것은 for 문 같은 반복문에서 Series 의 (idx, val) 튜플을 하나씩 꺼내쓰기 위함인 것<br />row 가 index 가 되는 Series 특성상 `for idx, val in enumerate():` 에서는 row 쓸 수 없기 때문에 필요한 것 같다. |

## DataFrame

> Two-dimensional, size-mutable, potentially heterogeneous tabular data.

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

| Name     | description                                                  |
| -------- | ------------------------------------------------------------ |
| df.shape | Return a tuple representing the dimensionality of the DataFrame.<br />=> (how many row, how many columes) |
| df.index | return index (row labels) of the df<br />RangeIndex(start = [num], stop = [num], step= [num]) |

### Methods

| Command                                   | description                                                  |
| ----------------------------------------- | ------------------------------------------------------------ |
| df.value_counts([subset, normalize, ...]) | Return a Series containing counts of unique rows in the DataFrame.<br />같은 행이 몇개인지 갯수의 내림차순 Series 를 반환하며, 순서 숫자 뿐만 아니라, 해당 행의 이름으로 인덱싱할 수 있다.<br />인자로 column 을 써도 되고<br />df[column] 으로 인덱싱한 df 에 인자없는 매서드를 걸어도 된다. |
| df.info()                                 | Print a concise summary of a DataFrame.                      |
| df.head([n])                              | Return the first *n* rows                                    |
| df.groupby([by])                          | Group DataFrame using a mapper or by a Series of columns.    |

## DataFrame.groupby

> df.groupby([by]) 함수에 의해 생성된 객체. 인자 별로 그룹화되어 있으며, 인자 별로 그룹된 것들의 어떤 column 을 어떤 연산한 결과를 value 로 가질 것인지
>
> df.groupby('그룹화인자')[대상column].어떤연산함수()

### Methods

| name    | description                                                |
| ------- | ---------------------------------------------------------- |
| Count() | 그냥 갯수 셈 (중복에 상관없이 그냥 행이 몇개인지 세는 듯?) |
| Sum()   | 대상 column 의 val 들을 누적 합 함                         |

