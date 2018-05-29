# CI/CD to Kubernetes using Jenkins and Helm
This project is an example of a complete CI/CD pipeline of a simple static web application from sources to deployed Kubernetes pods.

## Docker.io as Docker registry
This project uses [Docker Cloud](https://cloud.docker.com) as its Docker registry.
### Here is a code change for Dev

## Verify Narcisuss Branch for Dallas

Follow the documentation for setting up your Docker registry.

## Local Helm Serve as Helm repository
This project uses [Localhost](http://localhost:8338) as its Helm repository.

Follow the documentation for setting up your Helm repository.

## Jenkins
Setup a [Jenkins](https://jenkins.io/) running with
- [Docker](https://www.docker.com/). Can build and push images
- [Kubectl](https://kubernetes.io/). Kubernetes CLI that will link Jenkins with the Kubernetes cluster
- [Helm](https://helm.sh/). Kubernetes package manager to simplify deployment of your Docker containers to Kubernetes

There is a [GitHub example](https://github.com/mmaheu/jenkins-k8s) of such a Docker image, to be used in Kubernetes.

### Jenkins in Kubernetes
Jenkins running in Kubernetes can be found in this [GitHub example](https://github.com/mmaheu/jenkins-k8s).
- This project is used to build a Jenkins master that has the required tools (`docker`, `kubectl` and `helm`) already installed
- You can deploy this Jenkins to Kubernetes using the helm chart in the same repository
- Notice that this is an example, and should not be used for production

### General notes
- The Jenkins pipeline example ([Jenkinsfile](Jenkinsfile)) is using calls to external cli tools such as `docker`, `kubectl`, `curl` and other shell commands.
Some of these can be replaced with groovy code and functions or built in pipeline steps, but are implemented like this to demonstrate the simple use of these tools.
- The `kubectl` and `helm` clients are **not** configured in this example. It's assumed the Jenkins instance is pre-configured, or run it in your Kubernetes cluster,
where it picks up the local pod credentials to access the Kubernetes API.

## Build the Nostromo web application
You can build the web application directly by running `build.sh`. You can create the Docker image and run it locally. See the [build.sh](build.sh) options.
```bash
# See options
$ ./build.sh --help
```

You can also pack and push the Docker image and Helm chart.
