
# IMDB review sentiment analysis

# Cosmetic review sentiment analysis

현재 당면한 문제(지속적 해결중. history 관리)
@ (해결)네이버 영화 감성분석.ipynb처럼 리뷰 입력하면 긍정, 부정 분류해주는 모델을 만들고자 합니다. 그런데 learning()을 하면 에러가 납니다...  
-> 문자열 데이터에 섞여 있는 이모티콘 문제였습니다. 이모티콘을 제거해주니 에러가 안납니다. 
   하지만 이모티콘 이외에 특수문자( :), ^o^ ) 등에서 간혹 에러가 났다가 안났다가 합니다. 그런 특수문자들을 최대한 제거하였습니다.


리뷰 데이터(cos27.csv)를 넣고 learning을 할 때마다 에러가 나기도 했다가 안나기도 했다가 그럽니다.
아마도 한글 자연어처리 상 문제인거 같아서 다양한 테스트를 해보다 보니 파일명이 27이 되었습니다.(실제로는 더 테스트를 해보았습니다...읔...)
지금까지 다양한 테스트를 해보며 예측한 에러 후보군들은 다음과 같습니다.

1. 이모티콘(😍) 제거
- 이모티콘은 주로 문장 맨 끝에 있다.
- 파이썬 코드1 : 이모티콘 중에 없어지는 것도, 안 없어지는 것도 있다.
- 파이썬 코드2 : 이모티콘과 단어가 붙어있을 경우 붙어있는 단어도 제거된다…
2. 하트 제거(♡♥)   ->   .하트.
3. 👍 ->   .굿굿.
4. 오타 수정(한글 형태 파괴 주범들)
- 기름기 좌ㄹ좌ㄹ -> 기름기 좔좔
- 와우 피부인지 사막인지 앍ㅎ챠냗ㅃㄴㄹ호갸늌 -> 삭제
- 띄어쓰기 무시 : 샘플 받아서쓰고있는데뭐랄까은근겉도는느낌이랄까요시간좀지나면흡수되긴하는데엄청촉촉한것두아니고  -> 띄어쓰기화!

지속적인 한글 데이터 전처리 작업을 통해서 에러율을 낮추고 정확도(현재 80%)를 높여나갈 예정입니다.
감사합니다.!


1. 사전 주제 목표 : 화장품 리뷰 감성분석

데이터 수집
- 화장품 정보 플랫폼(글로우픽)에서 고객 후기와 평점을 크롤링한다.

분석 알고리즘
- konlpy를 사용하여 한글 형태소 분석을 한 후, sentiment 분석을 한다.
- Okt로 한글 형태소 분석을 한다.

분석 의의
- 화장품 리뷰 기반으로 화장품의 긍정, 부정 감성예측
- 화장품 회사의 리뷰 데이터 확보의 중요성
- 향후 화장품 추천 모델에 적용

