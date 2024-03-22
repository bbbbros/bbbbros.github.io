24. 3. 22. 오전 10:50 10. pandas의 자료구조 Series와 DataFrame 살펴보기

[**1100. . ppaannddaass의의  자자료료구구조조  SSeerriieess와와  DDaattaaFFrraameme  살살펴펴보보기기**](https://nittaku.tistory.com/110)![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.001.png)

2018\. 2. 23. 23:32

![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.002.png)

**pandas**는 핵심라이브러리로, 고유한 자료구조인 **Series**와 **DataFrame**으로 **빅데이터 분석에 높은 수준의 퍼포먼스 를 발휘**한다.

Series와 DataFrame는 앞서 공부한 numpy의 1차원과 2차원 array과 매우 유사하다.

**pandas Series 살펴보기**

pandas를 사용하기에 앞서 **numpy 와 pandas 패키지를 모두 import해야한다.**

![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.003.png)

Series를 정의할 때, **pd**.**Series()**함수를 이용하는데,  **python의 list**나 **numpy의 array가 인자**로 입력된다.

![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.004.png)

- series를 확인해보면, index와 values가 동시에 확인된다.

  이 때, **리스트의 성분 갯수 = index의 갯수**가 되는 것을 알 수 있다.![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.005.png)

  **series변수.values**를 호출하면 **값(values)만 따로 array로 확인**할 수 있고, .**index**를 이용하면 **index 범위 값**만 얻을 수 있다.

  **데이터형을** **확인**하려면, **obj.dtypes**를 통해 확인할 수 있다.

  ![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.006.png)

  Series의 특징은 값과 함께, **우리가 원하는 index를 입력할 수 있다는 것**이다. list나 array인자 이외에 추가로 index=[ ]를 이용해서 입력해준다. obj2 = pd.Series( [ 4, 7, -5, 3], **index=["d", "b", "a", "c"]**)

  \*\*\* 인덱스의 성분을 줄 때는 ‘’ 작은 따옴표로 주고, 그외에 키값, 시리즈이름, 시리즈인덱스이름은 다 “”쌍따옴 표

  `     `확인 결과 “”쌍따옴표로 줘도 상관없다. 왜 확인 했냐면..

  **\*\*\* DataFrame에서 인자에 인덱스를 정의해줄 때는, “”쌍따옴표로..**

  ![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.007.png)

  이것은 **python에서 중괄호로 {  “키값” : 벨류값 ,  “키값” : 벨류값 } 형식으로 만든 딕셔너리와 비슷**하며, Series를 만들 때 인자를 (arr , index=[ , , ] ) 가 아니라 **딕셔너리를 줘서 원하는 index**를 줄 수 도 있다.

  ![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.008.png)

  즉, pd.Series( )의 인자에는 [ , , ] list / np.array() / 파이썬의 딕셔너리가 들어갈 수 있다. 또다른 Series의 특징은, **Series의 이름과 index에 이름을 지정**해줄 수 있다는 것이다. **series변수.name = “ 시리즈이름”,  series변수.index.name = “인덱스이름”**

  비슷하게, 위에서 직접 입력한 index의 값을 바꿔 줄 수 도 있다. **series변수.index = [ ‘새’, ‘로’, ‘운’, ‘인덱스’]![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.009.png)**

  ![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.010.png)

**pandas DataFrame 살펴보기**

dataFrame은 먼저, **python의 딕셔너리 형태로 data를 정의**해준 뒤 ===> **dataFrame을 정의**한다. 그외에 인자로 **numpy의 array**도 들어갈 수 있다.

먼저, 딕셔너리형태로 데이터를 정의해주는데, { “키값” : value }에서  **values자리에 [  리,스,트 ] 형태로 입력** 을 해준다.

그렇게 하면, **키값들의 갯수**가은 **열(Columns)의 갯수**이 될 것이고, **리스트의 성분들의 갯수**은 각 **행의 갯수 (index)를 담당**할 것이다.

만들어진 딕셔너리를 **pd.DataFrame( )**인자에 넣어준다.

![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.011.png)

세로로는 index(리스트 성분의 갯수)가, 가로로는 키값(columns) 들이 둘러싸고 있는 표형태의 데이터를 얻을 수 있다. 엑셀의 table모양과 아주 흡사하다.이 때, 키값이 자동으로 Colums의 이름이되며, 키값의 갯수가 열의 갯수가 된다.

`       `밸류값인 리스트의 성분갯수가  행의 index를 결정한다.

이렇게 dataFrame에서는 2종류의 index가 존재한다. 가로의 index를 columns라고 한다.

df.index / df.columns / df.values 를 통해 값을 확인해보자. values는 2차원 넘파이의 array형태로 값을 얻

É![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.012.png)

https://nittaku.tistory.com/110 4/9
24. 3. 22. 오전 10:50 10. pandas의 자료구조 Series와 DataFrame 살펴보기

을 수 있다.![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.013.png)

![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.014.png)

Series와 마찬가지로 DataFrame의 index와 columns에도 이름을 붙힐 수 있다

![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.015.png)

많은 DataFrame 함수를 자동완성해주는 기능도 있다. **dataFrame변수. [TAB]**키를 눌러서 확인하자.

![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.016.png)

pd.DataFrame( 딕셔너리data)로 정의할 때,

**키값**이 자동으로 **Columns의 이름**이되며, **키값의 갯수**가 **열의 갯수**가 된다. É

밸류값인 **리스트의 성분갯수**가  **행의 index**를 결정한다.

하지만, **딕셔너리에서 정의한 키값**을 인자로 **columns에 직접 넣어** **columns의 순서를 새롭게 정의**할 수 있으 ![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.017.png)며,

만약 **키값이 미리 존재하지 않는 이름을 columns인자의 성분으로 넣는다면, 그 칼럼은 NaN**으로 표시가 된다. 또 인자로서, **index를 입력**하면, 리스트성분의 개수로 자동설정되어 0부터 시작하던 **index의 이름**을 줄 수 있 다.

![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.018.jpeg)

이 때, **NaN라는 것은 Not a Number를 의미한다. 해당하는 값이 없다는** 뜻이다.

다음 강의에서 이 값을 메꾸는 방법을 배울 것이다.

마찬가지로, df2라는 칼럼과 인덱스 이름을 정의한 DataFrame에 칼럼과 인덱스의 이름을 확인할 수 있다.

![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.019.jpeg)

- 또다른 유용함수로 **df.describe()**라는 함수가 있다**. 연산이 가능한 숫자를 가진 컬럼을 뽑아내고**  그 칼럼들에 대해

https://nittaku.tistory.com/110 7/9
24. 3. 22. 오전 10:50 10. pandas의 자료구조 Series와 DataFrame 살펴보기

**기본 통계량(총 개수, 평균, 표준편차, 최소값, 퍼센트, 최대값)을 산출**하여 표시해준다.![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.020.png)

이는 어떤 dataset를 가져온 뒤, DataFrame으로 바꾼 다음 전체적으로 살펴볼 때 아주 좋다.

![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.021.png)

9 구독하기

**'[빅데이터 관련 프로그래밍 > P](https://nittaku.tistory.com/category/%EB%B9%85%EB%8D%B0%EC%9D%B4%ED%84%B0%20%EA%B4%80%EB%A0%A8%20%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D)yt[hon - bigdata(pandas 기초)' 카테](https://nittaku.tistory.com/category/%EB%B9%85%EB%8D%B0%EC%9D%B4%ED%84%B0%20%EA%B4%80%EB%A0%A8%20%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D/Python%20-%20bigdata%28pandas%20%EA%B8%B0%EC%B4%88%29)고리의 다른 글**

[12. pandas DataFrame 조작하기(datatime데이터형 / 결측값,이상치(NaN)/열 조작/ 행 조작)  (5) ](https://nittaku.tistory.com/112)2018.02.24

[11. pandas DataFrame 인덱싱(열 / 행 / boolean 인덱싱)  (7)](https://nittaku.tistory.com/111) 2018.02.24

[9. Numpy 데이터분석 해보기(파일읽기, 분석하기(고난도), 파일쓰기)  (0)](https://nittaku.tistory.com/109) 2018.02.23

[8. Numpy array 함수( 특정계산, 통계함수, 정렬함수)  (0)](https://nittaku.tistory.com/108) 2018.02.23

[7. Numpy array 인덱싱( 기본인덱싱, boolean인덱싱(마스크))  (2)](https://nittaku.tistory.com/107) 2018.02.23

[우아 한의원 | 조재성 원장의 한의학, 의학통계, 프로그래밍](https://nittaku.tistory.com/)

[평생 공부할 한의학, 의학, 통계, 프로그래밍을 기록하여 동료, 환자, 친구, 가족들에게 나누고 싶습 니다.](https://nittaku.tistory.com/)

구독하기

NÉAME

https://nittaku.tistory.com/110 8/9
24. 3. 22. 오전 10:50 10. pandas의 자료구조 Series와 DataFrame 살펴보기

PASSWORD![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.022.png)

HOMEPAGE http://

SECRET WRITE

[+ Recent posts](https://nittaku.tistory.com/category)

np.random.shuffle 과 [원격용] 윈도우키, 한영키, 알트탭 윈도우에서 markdown 파일을 우 jupyter notebook 브라우저 크롬

[Rss  Feed ](https://nittaku.tistory.com/rss) and [ Twitter,](https://www.twitter.com/)[  Facebook](https://www.facebook.com/),[  Youtube](https://www.youtube.com/),[  Google+](https://plus.google.com/) Powered  by[  Tistory](http://www.tistory.com/),  Designed  by[  wallel](http://wallel.com/)
É![](Aspose.Words.4aa250e5-22dc-4079-8e25-08c677ddcbf9.023.png)

https://nittaku.tistory.com/110 9/9
