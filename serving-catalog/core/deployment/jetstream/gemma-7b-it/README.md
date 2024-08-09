$BUCKET_NAME must be replaced in `job-patch.yaml` and `patch.yaml`

The example can be deployed by issuing the commands:

```
kustomize build core/deployment/jetstream/gemma-7b-it/gke | kubectl apply -f - --selector prerequisite=model-load &&
kubectl wait --for=condition=complete --timeout=1000s job/gemma-7b-it-jetstream-data-loader &&
kustomize build core/deployment/jetstream/gemma-7b-it/gke | kubectl apply -f - --selector app=gemma-7b-it-jetstream-inference-server
```