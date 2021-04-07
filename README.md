💻💻💻💻💻💻💻💻💻💻

Kubify is a CLI tool to manage the development and deployment lifecycle of microservices.

# Setup
```
#add kubify cli tool the path (so you can type kubify commands)
export PATH=$PATH:$(pwd)/tools/kubify/cli #or add this to your ~/.profile

#install/configure/re-configure your local workstation with a proper cluster (including all pre-reqs automated)
kubify up
```

# Local Testing

```
#start all services locally (entire infra running locally)
kubify start-all 

#cd into a specific service
cd fe-svc

#listens for code changes, shows logs, runs unit tests (on each code save), opens and auto-configures IDE
kubify start
```

# Please Note

Compatible with Linux, Mac and Windows (with WSL2)

If you are on Windows, please use Debian for Windows (on the Windows App Store) to run this

# Questions Answered

If you want to learn the commands that the kubify wrapper is running: `KUBIFY_DEBUG=1 kubify {args}`

# Secrets Editing Examples

To use default editor:
```
cd backend/be-svc
kubify secrets create dev
```
To use alternative editor:
```
brew install cask sublime-text
export EDITOR="subl -w"
cd backend/be-svc
kubify secrets create dev
```
# How to contribute

If you find any bugs, have built and added any cool new features please open a PR.
If you are new to open source, this link helps get you started with your first PR to an OS repo.

https://github.com/firstcontributions/first-contributions

# Why

Calibration of this tool: If a developer on day 1 can do all of these things without DevOps support, then we have suceeded:
- run the entire infrastructure on workstation matching exactly how it's ran in production
- make a 1 line change to a service, test it and deploy it
- docs being self-sufficient with no manual intervention (fix all edge cases)

Service delivery frameworks are programming langauges. This is a 'best practices' perscription (automated turn-key framework) for smooth SDLC, to cover most of the pain points in DevEx, produce high quality code, enable rapid testing, enable rapid self service for devs and make all your hard working developers super happy!
Kubernetes can be complex (see below examples), so let's automate+organize and in turn simplify it. Let's Kubify it!
https://k8s.af/
https://news.ycombinator.com/item?id=26106080
https://www.trendmicro.com/en_us/research/21/b/threat-actors-now-target-docker-via-container-escape-features.html
	https://news.ycombinator.com/item?id=26121877


# Details

The point of this tool is to make Kubernetes easy for Developers. 
A developer (or devops) only has to fill out a yaml file to bring in any service.
Databases are automated with KubeDB and controlled from the same yaml file.
Crons are defined in the same yaml.
Seeding/Migration configuration is also defined in the same yaml.
Defaults are in place, in case a developer wants to provide a minimal yaml.

Secrets are securely versioned in the same mono repo. Each time a developer runs `kubify secrets edit dev`, AWS IAM first checks wether the user still has access.
The Environments folder has 1 yaml file per environment. controlling what is deployed where. 
 A developer can control what version tag of the service, what secrets bundle git tag or commit sha to use and what config git tag or commit sha to use where. Rolling back secrets, service version and config version are as easy as a 3 line PR in GitHub.

Automatic tagging, artifact bundling, container building, deployments and release flows are in place using GitHub Actions CICD and are developed inside the same mono repo.
Route53 is controlled using Kubernetes integration, for cloud Blue-Green tested deployments.

Terraform changes are made in an infrastructure folder and are visible/controlled with 2 approvers using Atlantis and GitHub integration. All AWS resources are automated for deploying the same stack (as your laptop) to the cloud (EKS,…).

When a developer wants to run all services on their laptop, all they need to run is `kubify run-all`. Kubernetes using Docker Desktop (Mac/Linux/Windows) will install/re-instal/configure/re-configure itself, pull the latest pushed containers and start the stack, without using a lot of resources (developer machine remains fast). When a developer wants to edit a specific service’s code, they are developing on an environment deployed automatically to their laptop (Kube DBs, Queues, Crons, Services,.. and all). Live code reload is used to develop and test at a rapid pace.

All in all, the tool is revolutionary and is a solid prescription for full Kubernetes automation, that would fit in most situations, make developers super efficient and reduce the burden on devops for release engineering.

The final result is a developer on day 1 can bring up the entire stack on their laptop, deploy to environments visibly (in a simple PR) and on-boarding becomes a breeze!

In the Kubernetes world, this is truly revolutionary and was *super* fun to build!

💻💻💻💻💻💻💻💻💻💻