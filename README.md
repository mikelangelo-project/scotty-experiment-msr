My experiment
=============

An experiment is a skelleton for scotty to deploy resources and run workloads for one experiment. 
It contains the experiment.yaml, customer directorys and files for the experiment workloads and resources.
Workloads and resources can access this files.

Directory structure
-------------------

| Path              | Description |
| ----------------- | ----------- |
| ./experiment.yaml | Experiment definition, contains workload and resource definitions for the experiment. <br> Scotty also use this as a marker for the experiment root directory |

