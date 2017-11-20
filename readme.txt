
# Install
brew update && brew install kubectl && brew cask install docker minikube virtualbox

# Use minikube docker version
eval $(minikube docker-env)

# Setup local registry
docker run -d -p 5000:5000 --restart=always --name registry registry:2

# Be able to use insecure registry
minikube start --insecure-registry="localhost:5000"


# The very first time, create namespaces and services
kubectl apply -f <FILENAME>.yaml


# Build container
docker build . -t localhost:5000/<PROJECTNAME>:<PROJECTVERSION>

PROJECTNAME - bolan, forsakra, spara etc
PROJECTVERSION - 0.0.1, 0.0.2, ...

# Push container to registry
docker push localhost:5000/<PROJECTNAME>:<PROJECTVERSION>

# To deploy, change deployment.yaml file so that the new deployment contains the new version
kubectl apply -f production/<PROJECTNAME>/deployment.yaml
