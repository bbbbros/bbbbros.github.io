![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.002.png)

**pandas**는 핵심라이브러리로, 고유한 자료구조인 **Series**와 **DataFrame**으로 **빅데이터 분석에 높은 수준의 퍼포먼스 를 발휘**한다.

Series와 DataFrame는 앞서 공부한 numpy의 1차원과 2차원 array과 매우 유사하다.

**pandas Series 살펴보기**

pandas를 사용하기에 앞서 **numpy 와 pandas 패키지를 모두 import해야한다.**
![Aspose Words 4aa250e5-22dc-4079-8e25-08c677ddcbf9 003](https://github.com/bbbbros/bbbbros.github.io/assets/161530952/3250974b-da62-4532-8927-a52a05435f3b)


Series를 정의할 때, **pd**.**Series()**함수를 이용하는데,  **python의 list**나 **numpy의 array가 인자**로 입력된다.

![Aspose Words 4aa250e5-22dc-4079-8e25-08c677ddcbf9 004](https://github.com/bbbbros/bbbbros.github.io/assets/161530952/30336640-9377-4fd7-befa-2f7311bd2fc4)


- series를 확인해보면, index와 values가 동시에 확인된다.

  이 때, **리스트의 성분 갯수 = index의 갯수**가 되는 것을 알 수 있다.
  
  **series변수.values**를 호출하면 **값(values)만 따로 array로 확인**할 수 있고, .**index**를 이용하면 **index 범위 값**만 얻을 수 있다.

  **데이터형을** **확인**하려면, **obj.dtypes**를 통해 확인할 수 있다.

![Aspose Words 4aa250e5-22dc-4079-8e25-08c677ddcbf9 006](https://github.com/bbbbros/bbbbros.github.io/assets/161530952/bfdf68fa-caa0-4370-9379-9c6f28149927)


  Series의 특징은 값과 함께, **우리가 원하는 index를 입력할 수 있다는 것**이다. list나 array인자 이외에 추가로 index=[ ]를 이용해서 입력해준다. obj2 = pd.Series( [ 4, 7, -5, 3], **index=["d", "b", "a", "c"]**)

  \*\*\* 인덱스의 성분을 줄 때는 ‘’ 작은 따옴표로 주고, 그외에 키값, 시리즈이름, 시리즈인덱스이름은 다 “”쌍따옴 표

  `     `확인 결과 “”쌍따옴표로 줘도 상관없다. 왜 확인 했냐면..

  **\*\*\* DataFrame에서 인자에 인덱스를 정의해줄 때는, “”쌍따옴표로..**

![Aspose Words 4aa250e5-22dc-4079-8e25-08c677ddcbf9 007](https://github.com/bbbbros/bbbbros.github.io/assets/161530952/102485a7-54b5-477c-9620-f92ee0dc949b)


  이것은 **python에서 중괄호로 {  “키값” : 벨류값 ,  “키값” : 벨류값 } 형식으로 만든 딕셔너리와 비슷**하며, Series를 만들 때 인자를 (arr , index=[ , , ] ) 가 아니라 **딕셔너리를 줘서 원하는 index**를 줄 수 도 있다.

![Aspose Words 4aa250e5-22dc-4079-8e25-08c677ddcbf9 008](https://github.com/bbbbros/bbbbros.github.io/assets/161530952/53cdd3fb-84f9-4892-87ab-4e318facc5bd)


  즉, pd.Series( )의 인자에는 [ , , ] list / np.array() / 파이썬의 딕셔너리가 들어갈 수 있다. 또다른 Series의 특징은, **Series의 이름과 index에 이름을 지정**해줄 수 있다는 것이다. **series변수.name = “ 시리즈이름”,  series변수.index.name = “인덱스이름”**

  비슷하게, 위에서 직접 입력한 index의 값을 바꿔 줄 수 도 있다. **series변수.index = [ ‘새’, ‘로’, ‘운’, ‘인덱스’]


**pandas DataFrame 살펴보기**

dataFrame은 먼저, **python의 딕셔너리 형태로 data를 정의**해준 뒤 ===> **dataFrame을 정의**한다. 그외에 인자로 **numpy의 array**도 들어갈 수 있다.

먼저, 딕셔너리형태로 데이터를 정의해주는데, { “키값” : value }에서  **values자리에 [  리,스,트 ] 형태로 입력** 을 해준다.

![Aspose Words 4aa250e5-22dc-4079-8e25-08c677ddcbf9 010](https://github.com/bbbbros/bbbbros.github.io/assets/161530952/19d287d8-383a-4900-8bb5-4a6d71f5c832)


그렇게 하면, **키값들의 갯수**가은 **열(Columns)의 갯수**이 될 것이고, **리스트의 성분들의 갯수**은 각 **행의 갯수 (index)를 담당**할 것이다.

만들어진 딕셔너리를 **pd.DataFrame( )**인자에 넣어준다.

![Aspose Words 4aa250e5-22dc-4079-8e25-08c677ddcbf9 011](https://github.com/bbbbros/bbbbros.github.io/assets/161530952/1bcce75b-eb88-4f1c-b2ad-4579aaa5954d)


세로로는 index(리스트 성분의 갯수)가, 가로로는 키값(columns) 들이 둘러싸고 있는 표형태의 데이터를 얻을 수 있다. 엑셀의 table모양과 아주 흡사하다.이 때, 키값이 자동으로 Colums의 이름이되며, 키값의 갯수가 열의 갯수가 된다.

`       `밸류값인 리스트의 성분갯수가  행의 index를 결정한다.

이렇게 dataFrame에서는 2종류의 index가 존재한다. 가로의 index를 columns라고 한다.

df.index / df.columns / df.values 를 통해 값을 확인해보자. values는 2차원 넘파이의 array형태로 값을 얻

![Aspose Words 4aa250e5-22dc-4079-8e25-08c677ddcbf9 012](https://github.com/bbbbros/bbbbros.github.io/assets/161530952/7271f9e0-2dac-4a7d-b1d2-86d57b7e0bc8)

을 수 있다.

![Aspose Words 4aa250e5-22dc-4079-8e25-08c677ddcbf9 014](https://github.com/bbbbros/bbbbros.github.io/assets/161530952/3dd268e3-2adb-4c67-a6ed-49cff8946884)


Series와 마찬가지로 DataFrame의 index와 columns에도 이름을 붙힐 수 있다

![Aspose Words 4aa250e5-22dc-4079-8e25-08c677ddcbf9 015](https://github.com/bbbbros/bbbbros.github.io/assets/161530952/8a4ee731-3efd-4bf1-a3ef-819735f4f275)


많은 DataFrame 함수를 자동완성해주는 기능도 있다. **dataFrame변수. [TAB]**키를 눌러서 확인하자.

![Aspose Words 4aa250e5-22dc-4079-8e25-08c677ddcbf9 016](https://github.com/bbbbros/bbbbros.github.io/assets/161530952/8ac146b2-9efe-4412-a81e-7e8c4c9d3f59)

pd.DataFrame( 딕셔너리data)로 정의할 때,

**키값**이 자동으로 **Columns의 이름**이되며, **키값의 갯수**가 **열의 갯수**가 된다. 

밸류값인 **리스트의 성분갯수**가  **행의 index**를 결정한다.

하지만, **딕셔너리에서 정의한 키값**을 인자로 **columns에 직접 넣어** **columns의 순서를 새롭게 정의**할 수 있으며,

만약 **키값이 미리 존재하지 않는 이름을 columns인자의 성분으로 넣는다면, 그 칼럼은 NaN**으로 표시가 된다. 또 인자로서, **index를 입력**하면, 리스트성분의 개수로 자동설정되어 0부터 시작하던 **index의 이름**을 줄 수 있 다.

![Aspose Words 4aa250e5-22dc-4079-8e25-08c677ddcbf9 018](https://github.com/bbbbros/bbbbros.github.io/assets/161530952/0013216c-a38f-4e15-8a35-37c4f969305a)


이 때, **NaN라는 것은 Not a Number를 의미한다. 해당하는 값이 없다는** 뜻이다.

다음 강의에서 이 값을 메꾸는 방법을 배울 것이다.

마찬가지로, df2라는 칼럼과 인덱스 이름을 정의한 DataFrame에 칼럼과 인덱스의 이름을 확인할 수 있다.

![Aspose Words 4aa250e5-22dc-4079-8e25-08c677ddcbf9 019](https://github.com/bbbbros/bbbbros.github.io/assets/161530952/fb39e16b-ea5c-4fc2-893f-57389df8d875)


- 또다른 유용함수로 **df.describe()**라는 함수가 있다**. 연산이 가능한 숫자를 가진 컬럼을 뽑아내고**  그 칼럼들에 대해


**기본 통계량(총 개수, 평균, 표준편차, 최소값, 퍼센트, 최대값)을 산출**하여 표시해준다.

이는 어떤 dataset를 가져온 뒤, DataFrame으로 바꾼 다음 전체적으로 살펴볼 때 아주 좋다.

![Aspose Words 4aa250e5-22dc-4079-8e25-08c677ddcbf9 021](https://github.com/bbbbros/bbbbros.github.io/assets/161530952/8d660e33-56dc-47d9-99d7-66496ce2d151)


