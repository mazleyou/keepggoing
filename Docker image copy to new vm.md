### docker image 복사

1. docker 이미지 tar파일로 저장

	- docker save [옵션] <파일명> [이미지명]
```bash
docker save -o gcrContainer.tar gcr.io/automl-vision-ondevice/gcloud-container-1.12.0:latest
```

2. tar파일로 만들어진 이미지를 다시 docker image로 되돌리기
	
	- docker load -i tar파일명
	
```bash
docker load -i gcrContainer.tar
```
3. docker 실행

```bash
export CPU_DOCKER_GCR_PATH=gcr.io/automl-vision-ondevice/gcloud-container-1.12.0
export CONTAINER_NAME=automl_high_accuracy_model_cpu
export PORT=8501
export MODEL_PATH=/home/userid/20200213122318

sudo docker run --rm --name ${CONTAINER_NAME} -p ${PORT}:8501 -v ${MODEL_PATH}:/tmp/mounted_model/0001 -t ${CPU_DOCKER_GCR_PATH}
```
