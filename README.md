# ckad

Certainly! I'll provide you with examples of how to perform the tasks you mentioned using `kubectl` imperative commands for the Certified Kubernetes Application Developer (CKAD) exam.

### 1. Create a Pod with Specified Container Name, Image, and Labels:

You can create a pod with the specified container name, image, and labels using the `kubectl run` command. Here's an example:

```bash
kubectl run my-pod \
  --image=nginx:latest \
  --restart=Never \
  --labels=app=my-app,env=production
```

In this command:
- `my-pod` is the name of the pod.
- `nginx:latest` is the container image.
- `--restart=Never` specifies that this is a pod (not a deployment or other controller).
- `--labels` sets the labels for the pod.

### 2. Create a Secret and Mount it as an Environment Variable into a Pod:

To create a secret and mount it as an environment variable into a pod, you can use the `kubectl create secret` and `kubectl run` commands. Here's an example:
```bash
# Create a secret
kubectl create secret generic my-secret \
  --from-literal=secret-key=my-secret-value

# Create a pod and mount the secret as an environment variable
kubectl run my-pod-with-secret \
  --image=nginx:latest \
  --restart=Never \
  --labels=app=my-app,env=production \
  --env=SECRET_KEY=my-secret-value \
  --dry-run=client \
  -o yaml > pod-with-secret.yaml
```

In this example:
- We first create a secret named `my-secret` with a key-value pair.
- Then, we create a pod named `my-pod-with-secret` using the `kubectl run` command.
- We specify the container image, labels, and set an environment variable `SECRET_KEY` with the value from the secret.

We use the `--dry-run=client` and `-o yaml` options to generate the YAML configuration for the pod, which you can save to a file (e.g., `pod-with-secret.yaml`) and apply it later using `kubectl apply -f pod-with-secret.yaml`.

Remember to adapt the image name, secret name, key-value pairs, and other parameters according to your specific CKAD exam requirements.

These examples should help you get started with the specified tasks for the CKAD exam using `kubectl` imperative commands.
