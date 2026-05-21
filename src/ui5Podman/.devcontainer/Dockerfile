FROM mcr.microsoft.com/devcontainers/typescript-node:24

WORKDIR /workspaces/ui5

RUN npm i -g npm@11
RUN npm config set min-release-age 7 --global
RUN npm config set engine-strict true --global
RUN npm install -g @ui5/cli @sap/generator-fiori yo
RUN npm install mbt rimraf

ADD zscaler.crt /usr/local/share/ca-certificates/
RUN update-ca-certificates 
RUN wget --no-check-certificate -q -O - https://packages.cloudfoundry.org/debian/cli.cloudfoundry.org.key | gpg --dearmor | sudo tee /usr/share/keyrings/cloudfoundry-archive-keyring.gpg > /dev/null
RUN echo "deb [signed-by=/usr/share/keyrings/cloudfoundry-archive-keyring.gpg] https://packages.cloudfoundry.org/debian stable main" | sudo tee /etc/apt/sources.list.d/cloudfoundry-cli.list
RUN sudo apt-get update
RUN sudo apt-get install -y cf8-cli libsecret-1-0 dbus dbus-x11 gnome-keyring
RUN sudo touch /etc/machine-id && chmod 777 /etc/machine-id && sudo dbus-uuidgen > /etc/machine-id
RUN sudo apt-get update && sudo apt-get install -y curl apt-transport-https ca-certificates
RUN curl -fSsL https://dl.google.com/linux/linux_signing_key.pub | gpg --dearmor | sudo tee /usr/share/keyrings/google-chrome.gpg > /dev/null
RUN echo deb [arch=amd64 signed-by=/usr/share/keyrings/google-chrome.gpg] http://dl.google.com/linux/chrome/deb/ stable main | sudo tee /etc/apt/sources.list.d/google-chrome.list
RUN sudo apt-get update
RUN sudo apt-get install -y google-chrome-stable