FROM mcr.microsoft.com/devcontainers/typescript-node:20

WORKDIR /workspaces/ui5

RUN npm install -g @ui5/cli @sap/generator-fiori yo
RUN npm install mbt rimraf

ADD zscaler.crt /usr/local/share/ca-certificates/
RUN update-ca-certificates 
RUN wget --no-check-certificate -q -O - https://packages.cloudfoundry.org/debian/cli.cloudfoundry.org.key | sudo apt-key add -
RUN echo "deb https://packages.cloudfoundry.org/debian stable main" | sudo tee /etc/apt/sources.list.d/cloudfoundry-cli.list
RUN sudo apt-get update
RUN sudo apt-get install -y cf8-cli libsecret-1-0 dbus dbus-x11 gnome-keyring
RUN sudo touch /etc/machine-id && chmod 777 /etc/machine-id && sudo dbus-uuidgen > /etc/machine-id