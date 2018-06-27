#
# Copyright 2017-2018 IBM Corporation
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

REPO ?= docker.io/ffdl
WHOAMI ?= $(shell whoami)
IMAGE_TAG ?= user-$(WHOAMI)

IMAGE_NAME?=logcollector_base:${IMAGE_TAG}

DOCKER_OPTIONS ?=

build-base-docker:
	echo "Building ${IMAGE_NAME}"
	docker build -q ${DOCKER_OPTIONS} -t ${IMAGE_NAME} -f Dockerfile .
	echo "Success building ${IMAGE_NAME}"

push-base-docker:
	echo "Pushing ${IMAGE_NAME}"
	docker push ${IMAGE_NAME}

all: build push

build: build-base-docker build-simple_log_collector build-emetrics_file build-regex_extractor #build-tensorboard-all

push: push-simple_log_collector push-emetrics_file push-regex_extractor #push-tensorboard-all

build-simple_log_collector:
	$(MAKE) -C ./simple_log_collector build

build-emetrics_file:
	$(MAKE) -C ./emetrics_file build

build-regex_extractor:
	$(MAKE) -C ./regex_extractor build

push-simple_log_collector:
	$(MAKE) -C ./simple_log_collector push

push-emetrics_file:
	$(MAKE) -C ./emetrics_file push

push-regex_extractor:
	$(MAKE) -C ./regex_extractor push

build-tensorboard-all:
	$(MAKE) -C ./tensorboard build

push-tensorboard-all:
	$(MAKE) -C ./tensorboard push

imagename:
	$(MAKE) -C ./simple_log_collector imagename
	$(MAKE) -C ./emetrics_file imagename
	$(MAKE) -C ./regex_extractor imagename
	$(MAKE) -C ./tensorboard imagename
