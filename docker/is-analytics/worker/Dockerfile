# ------------------------------------------------------------------------
#
# Copyright 2019 WSO2, Inc. (http://wso2.com)
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
# limitations under the License
#
# ------------------------------------------------------------------------

# set base Docker image to latest WSO2 Identity Server version 5.8.0 Docker image from WSO2's Private Docker Registry
FROM docker.wso2.com/wso2is-analytics-worker:5.8.0

# build arguments for external artifacts
ARG POSTGRESQL_CONNECTOR_VERSION=9.4.1212

# add PostgreSQL JDBC connector to server home as a third party library
ADD --chown=wso2carbon:wso2 https://jdbc.postgresql.org/download/postgresql-${POSTGRESQL_CONNECTOR_VERSION}.jar ${WSO2_SERVER_HOME}/lib/
