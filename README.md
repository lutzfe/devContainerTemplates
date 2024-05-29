# UI5 Dev Container Image
**Do the following before you start developing your UI5 Application**

- If not already there, add a new script in the `package.json` called `start-local` copy the `npm run start` cmd into it, but still use the `ui5-local.yaml` config. Add `--accept-remote-connections` at the end. 
- Copy the content from your `ui5.yaml` into your `ui5-local.yaml`. If you are using On Premise Services, change the `ignoreCertError` to `true` and replace the backend `url` to the reachable domain name and port.

[**Do the following if you use rootless Podman**](https://code.visualstudio.com/remote/advancedcontainers/docker-options#:~:text=Podman,Podman%20Compose.)
- Open devcontainer.json and add the following commands: 
    - `"runArgs": ["--userns=keep-id"],`
    - `"containerEnv": {"HOME": "/home/node"}`