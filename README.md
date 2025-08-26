# ansible-capi-autoscaler

This repo is to update/replace the service account used during a CAPI migration from an old management cluster to a new one

This will update the service account with the correct roles and generate a new kubeconfig for the cluster-autoscaler


The values that need to be updated when running this are within the ansible playbook `autoscaller-sa.yml`

```
    cluster_name: "kahus-workload-cluster"
    cluster_namespace: "default"
    tmp_dir: "/tmp/{{ cluster_name }}"
    mgmt_cluster_config: /home/kanderson/.kube/config-kahu-test-new
```

`cluster_name` is the name of the migrated workload cluster

`cluster_namespace` if its in a different namespace than default

`tmp_dir` the dir where we will stage all the files from

`mgmt_cluster_config` the new management cluster kubeconfig location


With the updated vars you can now run it using the following command

```
ansible-playbook autoscaller-sa.yml
```

