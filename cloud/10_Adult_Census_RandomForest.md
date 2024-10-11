###분류(범주 예측) 개인수입예측 랜덤포레스트 (income: >50K;<=50K)
1. Download CSV
    - adult_census.csv

2. 컬럼명을 수정
    - . -> _로 수정

3. Dataset 등록
    - 데이터 > 만들기 > adult_census_data > 다음
    - 로컬 파일에서 > Azure Blob Storage > workspaceblobstore > 다음
    - Upload file (adult_census.csv) > 다음 > 다음 > 다음 > Create

3. Designer 시작
    - 새 파이프 라인 만들기 > 이름 변경: adult_census
    - Data > adult_census_data 드래그
    - Select Columns in Dataset 드래그
    - Edit Columns > With rules > All columns
    - Exclude > 열이름 > workclass, native_country

4. 누락값 처리
    - Clean Missing Data 드래그
    - Edit Columns > 모든열
    - Clean mode > Remove entire row

5. 범주형 데이터로 변경
    - Edit Metadata 드래그
    - Edit Columns > education, marital_status, occupation, relationship, race, sex
    - Data type: String
    - Categorical: Categorical
    - Fields: Features

6. 데이터 변환
    - Convert to Indicator Values 드래그
    - Edit Columns > education, marital_status, occupation, relationship, race, sex
    - Overwrite categorical columns: True

7. 학습 데이터와 테스트 데이터로 분리
    - Split Data 드래그
    - Fraction of rows in the first output dataset: 0.7

8. 모델링 알고리즘 선택 (Two-Class Decision Forest)
    - Two-Class Decision Forest 드래그
    - Create trainer mode: SingleParameter
    - Number of decision trees: 8
    - Maximum depth of the decision trees: 32
    - Resampling method: Bagging Resampling

9. 모델 훈련
    - Train Model 드래그
    - Label column: income (>50K;<=50K)

10. 모델 테스트
    - Score Model 드래그
    - Append score columns to output: True

11. 모델 평가
    - Evaluate Model 드래그

12. Job 실행
    - Configure & Submit > Create new
    - Name: adultCensusPrediction > 다음 > 다음
    - 컴퓨팅 인스턴스
    - b043_vm_vm 실행 중
    - 다음 > 제출
    - Jobs > adultCensusPrediction > 확인


    