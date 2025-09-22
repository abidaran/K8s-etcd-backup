In this project, I create a backup from the etcd Database for the k8s cluster and also the k8s master certificates, which are necessary parts for backup and restore.
Here is a PVC that mounts to a storage class and a cron job that runs every day at 2 AM to take a snapshot from the etcd and save it in the PVC. For the saving directory permission issue, I created an init container so that before the main container starts, it grants the necessary permissions.
And finally, there is a job that creates k8s master node certificates backup and copies them to the PVC.
