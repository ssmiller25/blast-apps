# WikiJS

A powerful and extensible open source Wiki package.  See [manifest.yaml](manifest.yaml) for more details.

*Note:* Copied from my implementation in the [Civo Marketplace](https://github.com/civo/kubernetes-marketplace).  Adjust to run from a kustomization.yaml manifest, as well as to use an external KubeDB provider to provision the database.

## Usage

Use a kustomization file as below

```yaml
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization

namespace: wikijs 

## TODO: secret for actual postgres database


resources:
  - git::http://github.com/ssmiller25/blast-apps/wikijs?ref=v1.1.0
```


## Updating the application

Pull the pinned version of the installation yamls and assemble them into a unified `app.yaml`

```sh
make clean
make build
```

## Test the application

Requires that you the [the civo cli utility installed](https://github.com/civo/cli) and authentication setup correctly.  This will build out a small k3s cluster, deploy the app, then run any tests that are defined.  The cluster will be torn down upon successful completion.  If the build fails, the cluster will remain to assist in debugging the test failure.

```sh
make test # Will automatically clean cluster after success
make test-keep  # Will test, but keep the cluster with app and tests running
```


