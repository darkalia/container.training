# Setting up Kubernetes

- How did we set up these Kubernetes clusters that we're using?

--

- We used `kubeadm` on freshly installed VM instances running Ubuntu 16.04 LTS

    1. Install Docker

    2. Install Kubernetes packages

    3. Run `kubeadm init` on the master node

    4. Set up Weave (the overlay network)
       <br/>
       (that step is just one `kubectl apply` command; discussed later)

    5. Run `kubeadm join` on the other nodes (with the token produced by `kubeadm init`)

    6. Copy the configuration file generated by `kubeadm init`

- Check the [prepare VMs README](https://github.com/jpetazzo/container.training/blob/master/prepare-vms/README.md) for more details

---

## `kubeadm` drawbacks

- Doesn't set up Docker or any other container engine

- Doesn't set up the overlay network

- Scripting is complex
  <br/>
  (because extracting the token requires advanced `kubectl` commands)

- Doesn't set up multi-master (no high availability)

--

- "It's still twice as many steps as setting up a Swarm cluster 😕" -- Jérôme

---

## Other deployment options

- If you are on Azure:
  [AKS](https://azure.microsoft.com/services/container-service/)

- If you are on Google Cloud:
  [GKE](https://cloud.google.com/kubernetes-engine/)

- If you are on AWS:
  [EKS](https://aws.amazon.com/eks/)
  or
  [kops](https://github.com/kubernetes/kops)

- On a local machine:
  [minikube](https://kubernetes.io/docs/getting-started-guides/minikube/),
  [kubespawn](https://github.com/kinvolk/kube-spawn),
  [Docker4Mac](https://docs.docker.com/docker-for-mac/kubernetes/)

- If you want something customizable:
  [kubicorn](https://github.com/kubicorn/kubicorn)

  Probably the closest to a multi-cloud/hybrid solution so far, but in development

- Also, many commercial options!
