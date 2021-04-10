#feature #1: APM with ISTIO
#feature #2: Auto-Configure IDE Debugger on "kubify debug"  
#more features that come to mind:
- fix WSL2 windows
- make sure CICD linux is stable, add example entrypoint files for cicd systems to run the cicd scripts
- add example 'hello kubify world' services in various languages
- auto configure vscode eclipse and pycharm move versions to one file
- ensure virtual env everywhere
- brew to use virtualenv
- python to use virtualenv (with full automation and coverage)
- serial number filtering 
- waf
- istio with APM by default!!
- service mesh
- UI
- Multi-Cloud (Checkmark and BAM you are backed by another cloud)
	- MCDS (coined fun phrase by Kubify OS): Multi-Cloud Distributed Services !!!! Super Awesomeness !!!!!! Should be as easy as a checkmark (bool) to enable multiple cloud providers and Kubify would automatically know what to do (focus on your code, you amazing coder, because we love you)..
- DR by default 
- convertor from ecs, heroku, ..
- Versioning to one file paramerized everywhere else. 
- Code listening on remote cluster
- https://kubernetes.io/blog/2021/03/09/the-evolution-of-kubernetes-dashboard/
- Kubeproxy with Hybrid Development rapid testing (develop a service locally and it to be part of a remote k8s cluster)
- CICD should run e2e full integration test daily on each important branch with pagerduty notifications on broken anything
- Add one of these to each cli function (or similar)
```
  if [ "$KUBIFY_DEBUG" != "0" ]; then
    echo "DEBUG: RUNNING THIS CLI FUNCTION: "
  fi
```
- Add a super cool progress bar for "kubify up" (when running outside of debug mode): https://laptrinhx.com/use-images-as-progress-bars-in-the-terminal-86135668/