# ObservIQ Logs

Implementation for [ObserveIQ](https://observiqlabs.com/) Kubernetes logs.  To use build out create oiq.env file.  This information can be obtained from the Template within the deployment instructions.  Make sure a "Kubernetes" source is attached.  **Note:** the BP_AGENT_SECRET_KEY will be base64 encoded, and will need to be decoded first.

```text
BP_AGENT_SECRET_KEY=uuid-secret
BP_CONFIGURATION_ID=uuid-configuration-id
```

Then to implement in your workflow:

```yaml
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization

secretGenerator:
  envs:
  - oiq.env

resources:
  - github.com/ssmiller25/blast-apps/observiq-logs?ref=v1.0.0
```