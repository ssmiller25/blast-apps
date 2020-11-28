# KubeDB

A Kubernetes Operator to manage databases.  See [manifest.yaml](manifest.yaml) for more details.


Note:* Copied from my implementation in the [Civo Marketplace](https://github.com/civo/kubernetes-marketplace).  Adjust to run from a kustomization.yaml manifest, as well as to use an external KubeDB provider to provision the database.

## Usage

Use a kustomization file as below

```yaml
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization

namespace: kubedb 

## TODO: secret for actual postgres database


resources:
  - git::http://github.com/ssmiller25/blast-apps/kubedb?ref=v1.1.0
```

