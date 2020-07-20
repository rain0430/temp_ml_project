## I. 데이콘 머신러닝 경진대회 소개 및 개요
- 주제: AI 알고리즘 활용 카드 사용 금액 예측
- 목표: 신용카드 사용 내역 데이터를 활용한 지역별, 업종별 월간 카드 사용 총액 예측
- 주최 / 주관
    + 주최: 제주특별자치도청, 제주테크노파크
    + 주관: DACON
- 웹사이트: [제주 신용카드 빅데이터 경진대회](https://dacon.io/competitions/official/235615/overview/)

## II. 데이터 구성
### (1) 데이터셋 개요
- 훈련 데이터: 201901-202003.csv (2.07 GB)
    + 임의추출 후 1000개만 저장
- 테스트 데이터 202004.csv (116 MB)
    + 데이터 공개일: 7/28 공개
- 제출양식: submission.csv (64 KB)

### (2) 데이터 정의서
- REG_YYMM: 년월
- ...
- ...

### (3) 참고
- 모든 데이터는 [구글 클라우드 빅쿼리](https://cloud.google.com/bigquery/)는 적재하였고, 아래와 같이 불러와서 머신러닝 프로젝트 수행

```python
import pandas

sql = """
    SELECT name
    FROM `bigquery-public-data.usa_names.usa_1910_current`
    WHERE state = 'TX'
    LIMIT 100
"""

# Run a Standard SQL query using the environment's default project
df = pandas.read_gbq(sql, dialect='standard')

# Run a Standard SQL query with the project set explicitly
project_id = 'your-project-id'
df = pandas.read_gbq(sql, project_id=project_id, dialect='standard')
```