FROM mcr.microsoft.com/devcontainers/typescript-node:latest

WORKDIR /workspaces/ui5

RUN npm install -g @ui5/cli @sap/generator-fiori yo mbt rimraf

ADD zscaler.crt /usr/local/share/ca-certificates/
RUN update-ca-certificates 
RUN wget --no-check-certificate -q -O - https://packages.cloudfoundry.org/debian/cli.cloudfoundry.org.key | sudo apt-key add -
RUN echo "deb https://packages.cloudfoundry.org/debian stable main" | sudo tee /etc/apt/sources.list.d/cloudfoundry-cli.list
RUN sudo apt-get update
RUN sudo apt-get install cf8-cli libsecret-1-0 -y dbus -y dbus-x11 gnome-keyring -y
RUN sudo touch /etc/machine-id && chmod 777 /etc/machine-id && sudo dbus-uuidgen > /etc/machine-id
RUN sudo apt install curl software-properties-common apt-transport-https ca-certificates -y
RUN curl -fSsL https://dl.google.com/linux/linux_signing_key.pub | gpg --dearmor | sudo tee /usr/share/keyrings/google-chrome.gpg > /dev/null
RUN echo deb [arch=amd64 signed-by=/usr/share/keyrings/google-chrome.gpg] http://dl.google.com/linux/chrome/deb/ stable main | sudo tee /etc/apt/sources.list.d/google-chrome.list
RUN sudo apt update
RUN sudo apt install google-chrome-stable -y