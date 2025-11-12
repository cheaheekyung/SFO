# SFO Project: Plastic Injection Molding Product Demand Prediction Model Development

## Project Overview
이 프로젝트는 플라스틱 사출성형 제품의 수요를 예측하는 모델을 개발하는 것을 목표로 합니다. Jupyter Notebook 중심의 워크플로우를 통해 데이터 탐색, 피처 엔지니어링, 모델 튜닝 및 평가, 그리고 SHAP 분석을 수행합니다.

## Project Structure
 Jupyter 중심 워크플로우에 따른 SFO 프로젝트의 권장 파일 구조입니다.

```
SFO/
├─ .venv/
├─ data/
├─ image/
├─ notebooks/
│  ├─ EDA/
│  │  ├─ 00_baseline_processed.ipynb
│  │  ├─ 01_time_series.ipynb
│  │  └─ 03_dtw_clustering.ipynb
│  ├─ Model/
│  │  ├─ autodl_logs/
│  │  ├─ 00_baseline_model.ipynb
│  │  ├─ 01_dtw_model.ipynb
│  │  └─ autoKeras.ipynb
│  └─ Plot/
│     ├─ 00_baseline_plot_XAI.ipynb
│     └─ 00_plot.ipynb
├─ src/
│   ├─ 00_baseline_processed.ipynb          # 원천 데이터 읽기, 클린업/정규화/기초 EDA, 베이스라인 입력 데이터 저장
│   ├─ 01_baseline_model.ipynb              # 간단한 모델(BL) 구축, 기본 성능 확보
│   ├─ 02_time_series(feature_engineering).ipynb  # 시계열 파생변수/캘린더/롤링 통계 등
│   ├─ 03_hyperparams(optuna).ipynb         # Optuna 기반 LightGBM 하이퍼파라미터 튜닝
│   └─ 04_final_model.ipynb                 # 최종 학습/검증, SHAP 해석, 결과 산출
├─ .gitignore
├─ config.py
├─ readme.md
└─ requirements.txt

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

## Run Order (실행 순서)

아래 순서대로 **`src/` 폴더**의 노트북을 실행하세요.

1. **`00_baseline_processed.ipynb`**  
   - 데이터 로딩 → 결측/이상치 처리 → dtype 캐스팅 → 기초 EDA  
   - **산출:** 전처리 테이블(예: `baseline_processed.csv`)

2. **`01_baseline_model.ipynb`**  
   - 시간 기반 분할(train/val) → BL 모델(LGBM 기본값 등) 학습 → MAE/RMSE/R² 산출

3. **`02_time_series(feature_engineering).ipynb`**  
   - lag/rolling/캘린더/외생변수 등 피처 추가 → 성능 향상 검증

4. **`03_hyperparams(optuna).ipynb`**  
   - Optuna로 LightGBM 튜닝 → Best params / Study 저장(선택)

5. **`04_final_model.ipynb`**  
   - 최적 파라미터 적용 최종 학습 → 지표 산출 → SHAP( bar / summary / dependence / force )  
   - **산출:** `final_model.pkl`, `predictions.csv`, `figures/*.png`(선택)



## Notes

민감 데이터는 리포지토리에 포함하지 않습니다.


경로/키 등은 config.py 또는 환경변수로 관리하세요.



raw_data(사출성형.csv)는 아래 사이트에서 다운받을 수 있습니다. 


[사출성형 데이터셋 (KAMP AI 포털)](https://www.kamp-ai.kr/aidataDetail?AI_SEARCH=%EC%82%AC%EC%B6%9C%EC%84%B1%ED%98%95&page=1&DATASET_SEQ=40&DISPLAY_MODE_SEL=CARD&EQUIP_SEL=&GUBUN_SEL=&FILE_TYPE_SEL=&WDATE_SEL=)
