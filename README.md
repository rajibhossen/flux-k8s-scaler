# Study autoscaling for MPI-based ensemble applications
Summary of experiments 

EKS cluster creation
```console
eksctl create cluster -f 
```

### Autoscaling Study 

Applications Utilized 
- LAMMPS
- AMG
- Kripke
- Laghos

Strategies
- Static with various instance numbers (8, 16, 32, 64)
- Fully automatic autoscaling (Horizontal pod autoscaling + cluster autoscaling)
- Workload-Driven Autoscaling


#### Experiments
- Comparison of autoscaling strategies with four application in fixed ensemble jobs (20 members)
- Comparison of autoscaling strategies with AMG application in variable ensemble jobs (20 members)
- Comparison of autoscaling strategies with AMG application in Large ensemble jobs (100 members)
- Comparison of workload-driven and fully automatic strategies with AMG application with downsizing enabled and fixed ensemble jobs (20 members)
- Scale out by increments of various sizes to study scale-out policy
- Study timings of cluster creation and deletion components, facilitated by Kubescaler
