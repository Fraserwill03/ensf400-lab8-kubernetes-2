# ensf400-lab8-kubernetes-2

## Objectives
This lab will teach us the scheduling, configmaps, canary and blue-green deployment strategies of Kubernetes. Through Minikube, a simplified Kubernetes engine running on a single computer, we practice the key concepts and usage of Kubernetes.

## Environment

### Set Up Your GitHub CodeSpaces Instance

Same as Lab 6, this lab will be performed in [GitHub CodeSpaces](https://github.com/codespaces). Create an instance using GitHub Codespaces. Choose repository `denoslab/ensf400-lab8-kubernetes-2`.


```bash
$ minikube start --nodes 3 -p ensf400
```

This step will start the Minikube service with 3 virtual nodes, stored in a profile called `ensf400`. If for some reason your Codespaces instance was stopped (e.g., not using it for a while). You can restart the minikube service using this profile by running:

```bash
$ minikube start -p ensf400
```

## Steps

Go to Section 7 - 10 and complete the steps for each section. The steps can be found in the `README.md` files in each subdirectory.

## Have Your Work Checked By a TA

The TA will check the completion of the following tasks:

- Output of Section 7.
- Output of Section 8.
- Output of Section 9.
- Output of Section 10.


Each member of the group should be able to answer all of the following questions. The TA will ask each person one question selected at random, and the student must be able to answer the question to get credit for the lab.

- Q1: Explain the scheduling strategy of Node Affinity and the scenarios to use it.
    - You essentially define hard and soft requirements that are used during scheduling that have key value pairs that define "affinities" that send pods to specific nodes. Good for when you have pods with specific hardware requirements or software requiremetns.
- Q2: Explain the scheduling strategy of Pod Anti-Affinity and the scenarios to use it.
    - Prevents pods with matching anti-affinity rules from being placed on certain nodes. Good for when load balancing, distribution is really important.
- Q3: Explain the deployment strategy of blue-green deployment. How to switch between the two versions of deployments?
    - It is a strategy where you have two deployments, one called blue and one called green. Only one will be up on production at a time, and you can easily update one, and then switch which is active, in order to update without downtime.
    We can switch with:
```bash
$ kubectl patch service  SERVICENAME -p '{"spec":{"selector":{"KEY": "VALUE"}}}'
``` 
- Q4: Explain the deployment strategy of canary deployment. How to adjust the ratio of users getting serviced by the canary deployment?
    - Rolled out to a small portion of users at a time. traffic gets directed to both canary versions. If successful the canary continues to roll out, if not it rolls back.
    In this configuration, nginx.ingress.kubernetes.io/canary: "true" enables canary deployment, and nginx.ingress.kubernetes.io/canary-weight: "20" directs 20% of the traffic to the canary version
