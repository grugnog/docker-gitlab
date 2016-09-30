Gitlab Kubernetes on GCE

# One time setup

To create secrets, run the following command (replacing [] params):
```
kubectl create secret generic gitlab --from-literal=dbkeybase=$(pwgen -Bsv1 64) --from-literal=secretkeybase=$(pwgen -Bsv1 64) --from-literal=otpkeybase=$(pwgen -Bsv1 64) --from-literal=rootpassword=[ROOT_PASS] --from-literal=dbpass=[DB_PASS]
```

Create persistent volumes:
```
gcloud compute disks create --size=100GB --zone=us-central1-b --type=pd-ssd gitlab-data
gcloud compute disks create --size=5GB --zone=us-central1-b --type=pd-ssd gitlab-postgres
gcloud compute disks create --size=5GB --zone=us-central1-b --type=pd-ssd gitlab-redis
```
