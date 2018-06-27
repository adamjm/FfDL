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

#ARG REPO
ARG IMAGE_NAME
ARG VERSION_ID
FROM ${IMAGE_NAME}:${VERSION_ID}

RUN mkdir -p /scripts
RUN mkdir -p /scripts/log_collectors
RUN mkdir -p /scripts/log_collectors/training_data_service_client
RUN mkdir -p /scripts/log_collectors/training_data_service_client/certs

ADD src/*.* /scripts/
ADD training_data_service_client/*.* /scripts/log_collectors/training_data_service_client/
ADD training_data_service_client/certs/*.* /scripts/log_collectors/training_data_service_client/certs/

RUN mkdir -p /scripts/log_collectors/training_data_service_client/certs

WORKDIR /scripts

RUN echo python=python3 > /root/.bashrc

