# 2023 교원그룹 AI 챌린지 - 손글씨 인식 AI 모델 개발

## 1. 작업 환경  
 Ubuntu 18.04.6 LTS  
 Cuda 11.2, V11.2.152  
 리눅스 환경에서 작업하는 것을 추천.  
 EasyOCR 사용
 
## 2. 대회 결과
 public Accuracy score: 0.87367 (상위 6.3%)  
 private Accuracy score: 0.87499 (상위 5.8%)  

## 3. Train
python3 train.py \
	--train_data '훈련 lmdb 경로' \
	--valid_data '검증 lmdb 경로' \
	--select_data / \
	--batch_ratio 1 \
	--batch_size 70 \
	--Transformation TPS \
	--FeatureExtraction ResNet \
	--SequenceModeling BiLSTM \
	--Prediction Attn \
	--imgH 64 \
	--imgW 224 \
	--data_filtering_off \
	--workers 0 \
	--batch_max_length 50 \
	--saved_model '사전 학습 모델' \
	--PAD \
	--FT
  
  
## 4. Predict
python3 demo.py \
	--image_folder '예측 이미지 경로'  \
	--Transformation TPS \
	--FeatureExtraction ResNet \
	--SequenceModeling BiLSTM \
	--Prediction Attn \
	--imgH 64 \
	--imgW 224 \
	--PAD \
	--saved_model '훈련 모델 경로'
