You need to have docker desktop installed on your machine.
https://docs.docker.com/desktop/install/mac-install/

On docker desktop you need to enable kubernetes.
https://docs.docker.com/desktop/kubernetes/

You need to install skaffold:
# For macOS on x86_64 (amd64)
curl -Lo skaffold https://storage.googleapis.com/skaffold/releases/latest/skaffold-darwin-amd64 && \
sudo install skaffold /usr/local/bin/

Need to get an ingress controller up and running. 
https://github.com/kubernetes/ingress-nginx
https://kubernetes.github.io/ingress-nginx/deploy/
or just run this command: kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.5.1/deploy/static/provider/cloud/deploy.yaml

Note:
These resources require the use of Node LTS v16. The most current Node v18 is still not widely supported and will introduce bugs and incompatibilities. We recommend the use of NVM to manage your environment if you require support for multiple versions:
NVM for macOS & Linux - https://github.com/nvm-sh/nvm
NVM for Windows - https://github.com/coreybutler/nvm-windows

You need to go into auth directory and run (note the period for local directory): docker build -t <yourdockerid>/auth .
Right now we need to push builds to docker hub. An issue I need to resolve.
You need to go into the client directory and run: docker build -t <yourdockerid>/client
You need to creat the jwt-secret: kubectl create secret generic jwt-secret --from-literal=JWT_KEY='afda'
You need to create an env variable for JWT_KEY: export JWT_KEY='afad'
Go the root directory and run: skaffold dev

When running on chrome you need to click on the screen and type: thisisunsafe

kubernetes cheatsheet: https://kubernetes.io/docs/reference/kubectl/cheatsheet/
