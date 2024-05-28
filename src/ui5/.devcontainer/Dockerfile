FROM mcr.microsoft.com/devcontainers/typescript-node:latest

WORKDIR /workspaces/ui5

RUN npm install -g @ui5/cli @sap/generator-fiori;

USER root

ADD zscaler.crt /usr/local/share/ca-certificates/
RUN update-ca-certificates
