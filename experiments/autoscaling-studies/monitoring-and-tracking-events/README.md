# Various Timings for pending pod, container pulling, instance addition
The purpose of this [file](application_ca_hpa_metrics.py) is to monitor and collect application and system metrics. 
The prerequisite is that, we have a kubernetes cluster with cluster autoscaling and horizontal pod autoscaling (HPA) or workload-driven autoscaling enabled. The metrics and logs this file capture are -

1. How long a POD is in pending state due to resource unavailability
2. How long it takes to run the container once the pod is scheduled
3. When does HPA take action by seeing the CPU Utilization
4. When there's pending pod, how long it takes for cluster autoscaler to take action
5. when does the cluster autoscaler add new nodes?
6. when cluster autoscaler request for new nodes, how long it takes to get the nodes?
7. when the load is decreased, how long it takes for HPA to scale down pods
8. When there's no load, how long it takes for CA to remove nodes?
9. when do the nodes are actually removed?

We can answer the above questions and many more by collecting the metrics. This file will save the results in the data directory.
In the paper, we showed the pod pending scheduling timing, and container pulling from registry timings for fully automatic autoscaling 
and workload driven autoscaling. 

- After setting up fully automatic scaling or workload driven autoscaling, 
- In a separate terminal and run the script to record various timings mentioned above. 
- 
```console
python application_ca_hpa_metrics.py --outdir <output-directory>
```

Instructions and input parameters
```console
python3 application_ca_hpa_metrics.py -h
usage: application_ca_hpa_metrics.py [-h] [--flux-namespace FLUX_NAMESPACE] [--autoscaler-namespace AUTOSCALER_NAMESPACE] [--hpa-namespace HPA_NAMESPACE] [--kubeconfig KUBECONFIG] [--outdir OUTDIR]

Program to collect various metrics from kubernetes

optional arguments:
  -h, --help
    show this help message and exit

  --flux-namespace FLUX_NAMESPACE
    Namespace of the flux operator

  --autoscaler-namespace AUTOSCALER_NAMESPACE
    Namespace of the cluster autoscaler

  --hpa-namespace HPA_NAMESPACE
    Namespace of the horizontal pod autoscaler

  --kubeconfig KUBECONFIG
     config file name, full path if the file is not in the current directory
```

This script will save the logs and metrics into a file for further processing. 