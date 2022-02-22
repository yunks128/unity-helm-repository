# Unity Helm Repository

Welcome to the Unity Helm Repository.

This repository allows for deployment of Helm charts to the Unity Kubernetes Cluster.

## What is Helm?

Helm is an application manager for Kubernetes. Think, Brew, Apt, or other package managers for servers, but for Kubernetes resources.
Kubernetes applications can become complicated in a hurry. 

- Pods
- Configmaps
- Secrets
- Environment variables
- L oad balancers
- Services 
and so on. Quite often you'll need some or all of the above. Helm can help you manage these resources, upgrade and update in lockstep with one another and extend your application capabilities with clever templates and run time configuration options that can set variables and similar without them being hardcoded into your pod or config definitions.

The other important thing we can do with Helm charts and the Unity platform is combine services from different parts of the Cloud infrastructure. For example, it might be easier for a project to allow AWS to manage Elasticsearch via their service, so rather than deploy an Elasticsearch pod, you might want to deploy Elasticsearch via the Unity specification and then link that Elasticsearch to the Kubernetes Pods in your Helm chart. This level of abstraction adds additional power to the Unity deployments, and interactions between Kubernetes and non Kubernetes services seamlessly.

## How do I install Helm?

As there a number of ways to install Helm to develop against, we'll just link you to the docs rather than trying to rewrite them for this page. 

To install Helm check [this page](https://helm.sh/docs/intro/install/) from the Helm Documentation

## How do I write a Helm chart?

A Helm chart is really just a collection of text files which explains to Helm how to install a selection of Kubernetes resources. In the simplest form they will have a Chart.yaml and a templates folder with various files in them. Templates are written to the chart install directory at run time and at that point are materialized, so any parameters passed in can be written to the template at that time. For example, you want a chart that can deploy a different version of a specific container, so you may want to pass the container tag in as a variable at which point its then added to the template to become a valid Kubernetes pod spec.

Of course, also, if your deployment is really simple, you don't need any templated variables at all, but Helm will also clean down used resources nicely, tell you whats installed on a cluster, where and which version, which can make managing these systems much cleaner.

The easiest way to get started is to use a template: `helm create my-unity-chart` and modify its contents from there!

## How do I add my Helm chart to the repository?

To deploy your Chart to Unity, you need to have supplied it to our repository. This will make it available to our deployment service and to other consumers. The easiest way to do that is to 

- Fork this repository
- Create a branch in your fork and add your chart and all the associated files to the charts directory, ensure your chart has a unique name.
- Create a Pull Request
- Notify the Unity CS team that your PR is awaiting review.

Once the pull request is merged, your chart will then be available for installation on the Unity platform.
