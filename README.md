# ckad

### Create a Pod with Specified Container Name, Image, and Labels

<details><summary>show</summary>
<p>
You can create a pod with the specified container name, image, and labels using the `kubectl run` command. Here's an example:

```bash
kubectl run my-pod --image=nginx:latest --restart=Never --labels=app=my-app,env=production
```
</p>
</details>


### Create a Secret and Mount it as an Environment Variable into a Pod
<details><summary>show</summary>
<p>
To create a secret and mount it as an environment variable into a pod, you can use the kubectl create secret and kubectl run commands. Here's an example:

```bash
kubectl create secret generic my-secret --from-literal=secret-key=my-secret-value
```
</p>
</details>

### Create a pod and mount the secret as an environment variable
<details><summary>show</summary>
<p>
  
```bash
kubectl run my-pod-with-secret --image=nginx:latest --restart=Never --labels=app=my-app,env=production --env=SECRET_KEY=my-secret-value --dry-run=client -o yaml > pod-with-secret.yaml
```
</p>
</details>

### Create a Deployment with X Image and Y Tag, Change the Y Tag to Z, and Record the Changes

<details><summary>show</summary>
<p>
```bash
kubectl create deployment my-nginx --image=nginx:X
```
```bash
kubectl set image deployment/my-nginx nginx=nginx:Z --record=true
```

## View the rollout history to record the changes:
```bash

kubectl rollout history deployment/my-nginx

```bash
kubectl rollout undo deployment/my-nginx --to-revision=2
```
</p>
</details>
Set Memory Request for a Pod's Container to XMi and Limit It to Half of the Maximum Allowed for Pods in the Namespace
<details><summary>show</summary>
<p>
To set the memory request for a Pod's container to XMi and limit it to half of the maximum allowed for Pods in the namespace, you need to define resource requests and limits in the Pod's YAML configuration. Here's how to do it:

Create or update a Pod YAML file (e.g., my-pod.yaml) with the following content:
```yaml
Copy code
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
  - name: my-container
    image: your-image:your-tag
    resources:
      requests:
        memory: "XMi"
      limits:
        memory: "50%"
Replace XMi with your desired memory request (e.g., "256Mi").
Replace your-image:your-tag with the actual container image.

Apply the Pod configuration using kubectl:
```bash
Copy code
kubectl apply -f my-pod.yaml
This will create or update the Pod with the specified memory request and limit.

Ensure that you have the appropriate permissions to set resource limits in the namespace. Also, note that resource limits are subject to the namespace's resource quotas and cluster policies, so make sure your configuration aligns with those restrictions.

</p>
</details>
Please feel free to copy and paste these examples into your Markdown file as needed.
