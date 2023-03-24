# Testing the [_Kubernetes Reference Highlighter_](https://marketplace.visualstudio.com/items?itemName=dag-andersen.kubernetes-reference-highlighter)

These 4 small challenges/scenarios will test how many and how fast users of the [_Kubernetes Reference Highlighter_](https://marketplace.visualstudio.com/items?itemName=dag-andersen.kubernetes-reference-highlighter) (_KRH_) find and fix bugs caused by broken references in Kubernetes manifests.

Each challenge will run until the participant has either found and fixed all the issues or 5 minutes have passed.

---
## How long does it take?

Around 30 minutes 

- 5 minutes introduction
- 4 scenarios, 5 minutes each.
- 5 minutes of questions.

---
## Rules
- You are allowed to read this README, before starting the challenges.
- You are allowed to read the [marketplace page](https://marketplace.visualstudio.com/items?itemName=dag-andersen.kubernetes-reference-highlighter) before starting the challenges.
- You are *not* allowed to add, delete, rename, or move files
- You are *not* allowed to change the yaml-structure or add/delete new fields in the Kubernetes manifests
- You are *not* allowed to change the namespace or name of resources. 
- You can use a terminal all you want. 
- Each challenge should be opened as a new window - So workspace only contains the files for that specific challenge.

### Rules for participants using the [_KRH_](https://marketplace.visualstudio.com/items?itemName=dag-andersen.kubernetes-reference-highlighter):
- All features are allowed during the tests.
- All features can be enabled and disabled during the test if needed.

---
## After the experiment
After completing the 4 challenges, run `git diff > my.patch` and send me the `my.patch` file.

---
## Examples

## Correct Reference

<p float="left"><img src="/images/assignments_correct.png" width="800" /></p>

## Broken Reference

<p float="left"><img src="/images/assignments_broken.png" width="800" /></p>

---

# Challenges

## 1) A simple website

<!---
Scanning Technique: Workspace
References: ingress ref, service, configMap|secret ref, free service)
--->

### Descriptions
You want to deploy your 3 layered stack to Kubernetes. The system contains a *frontend*, *backend*, and *database*; Each containing one or more Kubernetes resources.

Users report that they can't access the frontend. You investigate and notice that the frontend doesn't receive any requests. Furthermore, you check the logs and see that the frontend prints the error message: "_Can't access data._"

You want to check if there are issues related to broken references between the Kubernetes resources.

The files can be seen in `./challenge1`. There is only one resource per file. Each resource in the diagram below has its own file. 

### Task (Max 5 minutes)
- Find and fix the broken references

### Diagram

Your company has a diagram that shows how the Kubernetes resources are supposed to depend on each other. Each Kubernetes resource exists in its own file. 

<p float="left"><img src="/images/assignments_as1.png" width="1100" /></p>
<!-- <p float="left"><img src="/images/assignments_as1-answ.png" width="1100" /></p> -->

<!---
## Answer
- fix ingress service pointer
- fix selector for service
- fix configMap|secret ref reference
- fix free 
--->

---

## 2) Kubernetes resources across multiple teams

<!---
Scanning Technique: Cluster
References: free service, configMap|secret ref, service)
--->

### Descriptions
You are a software developer in a large company.

Your team (Team A) is building a new system that depends on another team's (Team B) services. The new system only consists of a single `Deployment` that needs to access a system called ***worker*** and a system called ***producer***. Both are owned by Team B.

The ***Worker***-deployment does not have a `Service` yet, so you are going to create one for Team B so that you can access their service.

You have read access to a cluster to investigate the other team's resources.
All Team B's Kubernetes resources are located in the `team-b`-namespace.

A diagram of the final result can be seen in the diagram below.

The files needed can be seen in `./challenge2`. There is only one resource per file.

### Task (max 5 minutes)
- Find and fix the broken references

### Diagram
Your company has a diagram that shows how the Kubernetes resources are supposed to depend on each other.

<p float="left"><img src="/images/assignments_as2.png" width="1100" /></p>
<!-- <p float="left"><img src="/images/assignments_as2-answ.png" width="1100" /></p> -->


<!---
### Answer
- fix reference to configMap in cluster
- fix selector in service in workspace
- fix free service ref to deployment in cluster.
--->

---

## 3) Integrating with two systems

<!---
Scanning Technique: Kustomize
References: kustomize build, free service, configMap|secret ref)
--->

### Descriptions
Your team has 2 systems running in ***production***. The systems are named `Database` and `Worker` and their Kubernetes configuration is built using *Kustomize*.

The team needs to build a simple integration between the two systems. The new system is named *middleware*, and it is your job to create the Kubernetes manifests for the new system.

The files can be seen in `./challenge3/middleware`. There is only one resource per file. Each resource in the diagram below has its own file. 

### Task (max 5 minutes)
- Find and fix the broken references

### Diagram
Your company has a diagram that shows how the Kubernetes resources are supposed to depend on each other. Each Kubernetes resource exists in its own file.

<p float="left"><img src="/images/assignments_as3.png" width="1100" /></p>
<!-- <p float="left"><img src="/images/assignments_as3-answ.png" width="1100" /></p> -->

<!---
### Answer
- fix deployment arguments
- fix broken config map issues.
- fix wrong filename in kustomize
--->
---

## 4) Two interconnected systems

### Descriptions
Your team is new to Kubernetes, and they don't know any good practices regarding the naming and folder structure of Kubernetes resources.
They are currently working on a few projects and experimenting with some new systems in the same repository. This means there are a lot of unused files and incomplete systems in the repository.

Luckily you don't need to worry about that since you will only be working in two isolated folders, `./challenge4/system-a` and `./challenge4/system-b`.

A diagram of the final result can be seen in the diagram below.

### Note
- None of the resources have a namespace specified. Keep it that way.

### Task (max 5 minutes)
- Find and fix the broken references

### Diagram

Your company has a diagram that shows how the Kubernetes resources are supposed to depend on each other. Each Kubernetes resource exists in its own file. 

<p float="left"><img src="/images/assignments_as4.png" width="1100" /></p>
<!-- <p float="left"><img src="/images/assignments_as4-answ.png" width="1100" /></p> -->

<!---
### Answer
- something
--->



<!---
# Questions after
- What did help you the most?
- Did the extension help?
- Do you find the diagram useful?
  - maybe if you had more time?
- Years of professional experience
- Years of professional experience with Kubernetes
- How likely are you to recommend this extension to others working with VS Code and Kubernetes? Scales go from 1:“very unlikely” to 5:“very likely”.

---

## things to include

### Features
- kustomize reference
- kustomize build
- Cluster
- normal workspace
- namespace sensitive free service ref

### Resources
1. ingress ref to service
2. service ref to deployment
3. free ref to service
4. deployment to secret
5. deployment to config map

--->