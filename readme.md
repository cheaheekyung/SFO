# SFO Project: Plastic Injection Molding Product Demand Prediction Model Development

## Project Overview
이 프로젝트는 플라스틱 사출성형 제품의 수요를 예측하는 모델을 개발하는 것을 목표로 합니다. Jupyter Notebook 중심의 워크플로우를 통해 데이터 탐색, 피처 엔지니어링, 모델 튜닝 및 평가, 그리고 SHAP 분석을 수행합니다.

## Project Structure
이 섹션에서는 Jupyter 중심 워크플로우에 따라 SFO 프로젝트의 권장 파일 구조를 설명합니다.

```
SFO/
├── .git/
├── README.md
├── requirements.txt
├── data/
│   └── SFO_data_raw.csv
├── config.py                 # (동일) 모든 설정값
├── src/                      # 재사용 가능한 핵심 로직 (Python 모듈)
│   ├── __init__.py           # 이 폴더를 Python 패키지로 인식하게 함
│   ├── data_processor.py     # 데이터 로드, 전처리, 피처 엔지니어링 관련 클래스/함수
│   ├── model_trainer.py      # 모델 정의, 튜닝, 학습, 평가 관련 클래스/함수
│   ├── analyzer.py           # SHAP 분석 및 시각화 관련 클래스/함수
│   └── utils.py              # 공통 유틸리티 함수 (폰트 설정 등)
├── notebooks/                # Jupyter Notebook 기반의 테스트, 실험, 최종 실행 파일
│   ├── EDA/ #탐색적 데이터 분석 노트북
│   │   ├── 00_EDA_humidity.ipynb          # 탐색적 데이터 분석
│   ├── Model/
|   │   ├── 00_Model_Experiments.ipynb # 다양한 모델 및 하이퍼파라미터 실험
│   ├── Plot/ #시각화 관련
|   |   ├── image/  #시각화 이미지 저장 경로
|   |   ├──00_plot.ipynb # 시각화 관련
│   └── README.md             # 각 노트북 파일의 목적 설명
```

## Getting Started (환경 설정)

### 1. Python 환경 설정
이 프로젝트는 Python 3.11.14 버전을 기반으로 합니다. 원활한 개발을 위해 가상 환경을 설정하는 것을 권장합니다.

*   **가상 환경 생성**:
    ```bash
    conda create -n SFO_env python=3.11.14
    # 또는
    python3.11 -m venv venv
    ```

*   **가상 환경 활성화**:
    ```bash
    conda activate SFO_env
    # 또는
    source venv/bin/activate  # Linux/macOS
    .\venv\Scripts\activate   # Windows
    ```

*   **의존성 설치**:
    `requirements.txt` 파일에는 프로젝트에 필요한 모든 Python 패키지 의존성이 명시되어 있습니다. 다음 명령어를 사용하여 의존성을 설치합니다:
    ```bash
    pip install -r requirements.txt
    ```
