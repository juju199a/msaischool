### MS Azure Cloud, ML Designer

1. Lauch Studio

2. Data > Create
    - Name: rocket_launch_data
    - Type: mltable (표형식)
    - Next
    - From Local File
    - workspaceblobstore
    - File Upload
    - RocketLaunch.csv
    - 기본값으로 
    - Schema (4개 유형 변경: 소수 구분(점,'.'))
        - High Temp
        - Low Temp
        - Hist High Temp
        - Hist Low Temp
    - 다음
    - 만들기

3. Create Compute
    - Compute > Create
    - b043-ml-vm
    - CPU
    - Standard_D2_v3
    - 검토, 만들기 > 만들기 (5분 정도 걸림)

4. Designer
    - Crewate a new pipline using classic prebuilt components
    - Name: rocket_launch
    - Data > rocket_launch_data > 왼쪽으로 드래그 

5. Preview Data
    - 오른 클릭 > Profile

6. Dataset 
    - 구성요소
    - Select Columns in Dataset
    - 왼쪽으로 드래그
    - 선연결

7. 열 편집
    - 이름별
    - 26열 -> 16열만 남기기 (아래 삭제)
        - Name
        - Data
        - Time
        - Location
        - Hist Ave Max Wind Speed
        - Hist Ave Visibility
        - Sea Level Pressure
        - Hist Ave Sea Level Pressure
        - Day Length
        - Note

8. Preview Data
    - 구성 및 전송
    - 새로 만들기
    - rocket_lanch_prediction
    - 다음
    - 다음
    - 컴퓨팅 인스턴스: b043-ml-vm
    - 제출
    - 작업 (Job)
    - Select Columns in Dataset (5분 걸림)
    - 오른 클릭 > 데이터 미리보기 > Results dataset

9. Cleaning Missing Data (1)
    - Cleaning Mssing Data 드래그
    - 선긋기
    - Clean Missing Data 더블클릭
    - Columns to be cleaned: Crewed or Uncrewed
    - Replacement value: Uncrewed
    - 저장 > 구성 및 전송

10. Cleaning Missing Data (2)
    - Launched?
    - false

11. Cleaning Missing Data (3)
    - Wind Direction
    - Unknown

12. Cleaning Missing Data (4)
    - Condition
    - Fair

13. Cleaning Missing Data (all)
    - 모든 열 (All columns)
    - 0

14. Edit Metadata
    - Edit Metadata 드래그
    - 선연결
    - Crewed or Uncrewed, Wind Direction, Condition > Enter
    - DataType: Categorical
    - Fields: Features

15. Convert to Indicator Values
    - 인디케이터화 시킨다.
    - Overwrite Categorical: True
    - 결과: 16개에서 35로 늘어남

16. Split Data
    - 0.7 (학습데이터 어느정도  랜덤 70%)
    - Result_dataset1: 210행
    - Result_dataset2: 90행
    
17. Two-Class Decision Forest
    - Depth: 5
    
18. Train Model
    - Label: Launched?
    - Model explanations: True
    - 나머지는 다 Input 값

19. Score Model
    - Trained model
    - Results dataset

20. Evaluate Model
    - 임계값: 0.5 (하나를 제외하고 다 정확하게
    - 정확도: 0.989
    - 지표를 뽑느다.
    
EOF