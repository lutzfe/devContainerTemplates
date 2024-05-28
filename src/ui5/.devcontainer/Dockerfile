FROM mcr.microsoft.com/devcontainers/typescript-node:latest

WORKDIR /workspaces/ui5

RUN npm install -g @ui5/cli @sap/generator-fiori yo mbt rimraf

USER root

ADD zscaler.crt /usr/local/share/ca-certificates/
RUN update-ca-certificates 
RUN wget --no-check-certificate -q -O - https://packages.cloudfoundry.org/debian/cli.cloudfoundry.org.key | sudo apt-key add -
RUN echo "deb https://packages.cloudfoundry.org/debian stable main" | sudo tee /etc/apt/sources.list.d/cloudfoundry-cli.list
RUN sudo apt-get update
RUN sudo apt-get install cf8-cli
RUN cf install-plugin -f https://github.com/cloudfoundry-incubator/multiapps-cli-plugin/releases/latest/download/multiapps-plugin.linux32