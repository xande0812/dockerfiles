# リポジトリの主要設定
NAME    := jupyter
VERSION := 0.0.1
LATEST  := false

# docker周り
DOCKER_IMAGE_NAME := xande0812/$(NAME)
DOCKER_IMAGE := $(DOCKER_IMAGE_NAME):$(VERSION)

# dockerのコンテナをビルド
.PHONY: docker-build
docker-build:
	docker build -t $(DOCKER_IMAGE) .
ifeq ($(LATEST), true)
	docker tag $(DOCKER_IMAGE) $(DOCKER_IMAGE_NAME):latest
endif
