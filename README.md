# 2023 교원그룹 AI 챌린지 - 손글씨 인식 AI 모델 개발

## 1. 작업 환경  
Ubuntu 18.04.6 LTS  
Cuda 11.2, V11.2.152
- 리눅스 환경에서 작업하는 것을 추천.  

## 2. Train
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
  ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d6ccef1b-c16c-4308-8543-b1109a68cfe4/Untitled.png)
  
  
  
## 3. Predict
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
  ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cb529402-5981-4e43-9369-cbb645ad7cb2/Untitled.png)
