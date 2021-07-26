# 20210726

2. numpy array와 phthon list의 차이점
  1) 문법 차이
    - 덧셈: 
          numpy - 각 인덱스 별로 더함.
          list - 이어붙임.
    - 뺄셈, 곱셈, 나눗셈: 
          numpy - 잘 동작
          list - 오류. (+5도 오류)
   
    - +5: 
          numpy - 각 인덱스 별로 더함.
          list - 오류
    - * 3:
          numpy - 각 인덱스 별로 곱함.
          list - 3번 이어붙임.
   2) 성능 차이
      numpy 만들어진 이유: 데이터를 효율적으로 다루기 위해서-> [ 문법 간단 + 성능 좋음(소요시간) ]     : 값들이 저장되는 방식 때문에 생김.
   3) 언제 어떤 걸 사용?
      - python list: 값을 추가하고 제거하는 일만 있을 때
      - numpy: 수치 계산이 많고 복잡할 때
      
          
3. numpy 라이브러리의 기본적인 통계 기능

  1) 최댓값, 최솟값
       
    import numpy as np
    
    array1 = np.array([14, 6, 13, 21, 23, 31, 9, 5])
    
    print(array1.max()) // 31
    print(array1.min()) // 5

2> 평균값
 
    import numpy as np
    array1 = np.array([14, 6, 13, 21, 23, 31, 9, 5])
    
    print(array1.mean()) // 15.25
    
3> 중앙값

    import numpy as np
    
    array1 = np.array([14, 6, 13, 21, 23, 9, 5])
    
    print(np.median(array1)) // 13.5
    
4> 표준편차, 분산
    
    import numpy as np
    array1 = np.array([14, 6, 13, 21, 23, 31, 9, 5])
    
    print(array1.std()) // 8.496322733983215 (표준편차)
    print(array1.var()) // 72.1875 (분산)
    
    
1. Pandas
  : numpy 포함. 외부 데이터 읽고 쓰기, 데이터 분석, 정리, 시각화 등이 추가로 포함되어 있음.
  : 특히 표형식을 이용하는데 능함. (2차원)
  
  1> Dataframe: 표 형식의 데이터를 담는 자료형
    - 열(column): 가로, 데이터의 특징(ex. 이름, 국적 출생년도 등)
    - 행(row, index): 세로, 레코드(ex. 사람)
    - numpy array는 숫자형만 담을 수 있지만, pandas Dataframe에서는 다양한 자료형 담을 수 O.


      import pandas as pd
      
      two_dimensional_list = [['dongwook', 50, 86], ['sineui', 89, 31], 'ikjoong', 68, 91], ['yoonsoo', 88, 75]]
      
      my_df = pd.Dataframe(two_dimensional_list, columns = ['name', 'english_score', 'math_score'], index = ['a', 'b', 'c', 'd'])
      
      my_df.dtypes // 각 column이 어떤 자료형을 담고 있는지가 나옴. -> 같은 column 내에서는 같은 자료형이어야 함. 
      
 
 2. DataFrame을 만드는 다양한 방법
 1> List of lists, Array of arrays, List of series // 모두 동일

      import numpy as np
      import pandas as pd
      
      #1
      two_dimensional_list = [['dongwook', 50, 86], ['sineui', 89, 31], ['ikjoong', 68, 91], ['yoonsoo', 88, 75]]
      df1 = pd.DataFrame(two_dimensional_list)
      
      #2
      two_dimensional_array = np.array(two_dimensional_list)
      df2 = pd.DataFrame(two_dimensional_array)
      
      #3
      list_of_series = [
        pd.Series(['dongwook', 50, 86]), 
        pd.Series(['sineui', 89, 31]), 
        pd.Series(['ikjoong', 68, 91]), 
        pd.Series(['yoonsoo', 88, 75])
      ]
      df3 = pd.DataFrame(list_or_series)

  2> Dict of lists, Dict of arrays, Dict of series // 모두 동일, 파이썬 사전 이용
     
    import numpy as np
    import pandas as pd
     
      names = ['dongwook', 'sineui', 'ikjoong', 'yoonsoo']
      english_scores = [50, 89, 68, 88]
      math_scores = [86, 31, 91, 75]
      
      #1
      dict1 = {
          'name':names,
          'english_score': english_scores,
          'math_score': math_scores
      }
      
      #2
      dict2 = {
          'name': np.array(names),
          'english_score': np.array(english_scorces),
          'math_scores': np.array(math_scores)
      }
      
      #3
      dict3 = {
          'name': pd.Series(names),
          'english_score': pd.Series(english_scores),
          'math_score': pd.Series(math_scores)
      }
      
      df1 = pd.DataFrame(dict1)
      df2 = pd.DataFrame(dict2)
      df3 = pd.DataFrame(dict3)
      
      print(df1)
 
/*     name  english_score  math_score
0  dongwook             50          86
1    sineui             89          31
2   ikjoong             68          91
3   yoonsoo             88          75 */

  3> List of dicts
  
    import numpy as np
    import pandas as pd
      
    my_list = [
        {'name': 'dongwook', 'english_score': 50, 'math_score': 86},
        {'name': 'sineui', 'english_score': 89, 'math_score': 31},
        {'name': 'ikjoong', 'english_score': 68, 'math_score': 91},
        {'name': 'yoonsoo', 'english_score': 88, 'math_score': 75}
      ]

    df = pd.DataFrame(my_list)
    print(df)

3. 실습과제
#1

    import pandas as pd

    #코드를 작성하세요.
    two_dimensional_list = [['Taylor Swift', 'December 13, 1989', 'Singer-songwriter'], ['Aaron Sorkin', 'June 9, 1961', 'Screenwriter'], ['Harry Potter', 'July 31, 1980', 'Wizard'], ['Ji-Sung Park', 'February 25, 1981', 'Footballer']]
    df = pd.DataFrame(two_dimensional_list, columns = ['name', 'birthday', 'occupation'])
    #정답 출력
    df
    
4. pandas의 데이터 타입
1> dtypes

    print(my_df.dtypes)

2> 담을 수 있는 데이터형의 종류
    : 정수(int64), 소수(float64), 텍스트(object), 불린(bool), 날짜와 시간(datetime64), 카테고리(category)
