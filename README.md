💻💻💻💻💻💻💻💻💻💻



# Description



Kubify is a CLI tool to manage the development and deployment lifecycle of microservices.



# But Why



This tool allows you to (with only 2 terminal commands: kubify up && kubify start-all) have the ENTIRE infra running on your laptop (yes, the ENTIRE infra, amazing, revolutionary), then you simply cd into the microservice (cd into a backend/[] or frontend/[] folder) folder you want to work on (then run kubify start) to start rapid testing (listens for code changes, also runs your unit tests on each save and auto-configures vscode for breakpoint configuration)!!

Imagine this new world: A developer in the first few minutes (even on day 1) can easily ^^ (and then can focus on their actual code)!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Run the exact environment you are running in the deployed k8s env locally (so you can be super super your commit won't break anything, rapid test and that it looks pretty)!!!!

This is really important in the DevOps industry (so please contribute). Our devs should get a proper full turn key solution on day 1 that is battle tested. Think cloud, but open source. DevOps needs to evolve into DevOps 4.0 and fast.. 


✅✅✅✅✅✅✅✅

Mult-Cloud is important. Really important. Think site/api/microservice/mlops multi-cloud redundancy turn key!!

Local testing (with the ENTIRE infra running locally perfectly) should be a click of a button (THIS FEATURE IS LIVE)!!

✅✅✅✅✅✅✅✅


![FAST9000](./docs/img/README_md_imgs/fast.gif)



# Setup

```

# add kubify cli tool the path (so you can type kubify commands)
# or add this to your ~/.profile
# TODO: automate this with ansible auto add to path
# TODO: or put in alias in root of repo and change all the references to relative paths
export PATH=$PATH:$(pwd)/tools/kubify/cli 

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

Example: `KUBIFY_DEBUG=1 KUBIFY_CONTAINER_REGISTRY=ecr kubify up`



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

# How to contribute to the OS repo



https://github.com/willyguggenheim/kubify is the official OS repo (combination of the 2015 and 2017 versions of Willy's OS kubify_com repo and refactored in 2021 to the offical OS repo, so this is the main official repo to contribute to)

If you find any bugs, have built and added any cool new features please open a PR.

If you are new to open source, this link helps get you started with your first PR to an OS repo.

For more information on the contribution PR review flow: https://github.com/firstcontributions/first-contributions



# Tell me again why



Because DevOps loves super hard working Developers and genius Data Scientists (so let's make it easy for them).



Calibration of this tool: If a developer on day 1 can do all of these things without DevOps support, then we have suceeded:

1) run the entire infrastructure on workstation matching exactly how it's ran in production

2) make a 1 line change to a service, test it and deploy it

3) docs being self-sufficient with no manual intervention (fix all edge cases)



![FAST9002](./docs/img/README_md_imgs/fast2.gif)



I think we all know what kind of justice that would serve for our hard working devs..

This way a developer on day 1 can be effective, up and running, as well as all devs can rapid test the entire infra locally and be super confident in the quality of their deployments (runs the same way locally as in the deployed env)



Service delivery frameworks are programming langauges. This is a 'best practices' perscription (automated turn-key framework) for smooth SDLC, to cover most of the pain points in DevEx, produce high quality code, enable rapid testing, enable rapid self service for devs and make all your hard working developers super happy!

Kubernetes can be complex (see below examples), so let's automate+organize and in turn simplify it. Let's Kubify it!

https://k8s.af/

https://news.ycombinator.com/item?id=26106080

https://www.trendmicro.com/en_us/research/21/b/threat-actors-now-target-docker-via-container-escape-features.html

	https://news.ycombinator.com/item?id=26121877



# Important Notes



The "dev" environment is the same environment when running locally as the deployed environment (both local and the actual dev deployed k8s env use the "environments/dev.yaml" file, by careful design)



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



Let's make kubernetes the most important devops tool on the planet (because it's portability and interfaces are ❤️ pure love ❤️)!

Let's make our hard working devs super happy together (because all devops things will be automated as much as possible)!

Let's automate as much as possible together (the more contributors, the better devops 4.0 will be)!

Let's make DevOps 4.0 portable, flexible, automated and open source!!!

Let's build DevOps 4.0 together!!!



Version 1 of Kubify is live in and in master branch. 

Let me know if it works nicely on your Apple and Linux things.
I will fix WSL2 support drift for Windows sooooon.



This is what it feels like to run `kubify up`:



![LEVELOVER9000](./docs/img/README_md_imgs/bugs-fixed-v1-ready.gif)



Want a rush? Run `kubify up`! Hey, that rhymes!



So let's build awesome stuff together!!!



![AUTOMATION9000](./docs/img/README_md_imgs/iron-person.gif)



In the Kubernetes world, this is truly revolutionary, one of a kind (due to local testing automations matching deployed environment automations turn key and hybrid k8s portable interfaces) and was *super* fun to build!!!



![LEVELOVER9000](./docs/img/README_md_imgs/level-up.gif)



💻💻💻💻💻💻💻💻💻💻