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
FROM docker.wso2.com/wso2is:5.8.0

# set dependant files directory
ARG FILES=./files
# build arguments for external artifacts
ARG POSTGRESQL_CONNECTOR_VERSION=9.4.1212
ARG WEBLOGIC_AUTHENTICATOR_VERSION=1.0.0
ARG CUSTOM_AUTHENTICATION_REQUEST_HANDLER=1.0.0

# add PostgreSQL JDBC connector to server home as a third party library
ADD --chown=wso2carbon:wso2 https://jdbc.postgresql.org/download/postgresql-${POSTGRESQL_CONNECTOR_VERSION}.jar ${WSO2_SERVER_HOME}/repository/components/dropins/

# copy non-downloadable custom artifacts
# copy Weblogic custom authenticator
COPY --chown=wso2carbon:wso2 ${FILES}/org.wso2.carbon.identity.application.authenticator.weblogic.oauth2-${WEBLOGIC_AUTHENTICATOR_VERSION}.jar ${WSO2_SERVER_HOME}/repository/components/dropins/
COPY --chown=wso2carbon:wso2 ${FILES}/org.wso2.carbon.identity.application.authentication.framework.custom-${CUSTOM_AUTHENTICATION_REQUEST_HANDLER}.jar ${WSO2_SERVER_HOME}/repository/components/dropins/
# copy customized web applications
COPY --chown=wso2carbon:wso2 ${FILES}/accountrecoveryendpoint.war ${WSO2_SERVER_HOME}/repository/deployment/server/webapps/
COPY --chown=wso2carbon:wso2 ${FILES}/authenticationendpoint.war ${WSO2_SERVER_HOME}/repository/deployment/server/webapps/
# copy resource files
COPY --chown=wso2carbon:wso2 ${FILES}/oauth_response.html ${WSO2_SERVER_HOME}/repository/resources/identity/pages/
