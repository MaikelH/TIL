# Retrieve all secrets in a yaml file

Sometimes it is needed to retrieve all the secrets inside a kubernetes cluster (for backup purpopes for example). The 
following command will retrieve all secrets in `yaml` format and write them to `secrets.yaml`. This file can then be used with
`kubernetes apply` to restore all the secrets.

```bash
kubectl get secret | awk '{if(NR>1)print $1}' | xargs -0 -I name kubectl get secret -o yaml > secrets.yaml
```
