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

Getting Started
---------------

Describe your experiment in the experimernt.yaml. The experiment.yaml contains the following sections

| Section           | Optional | Description |
| ----------------- | -------- | ----------- |
| describtion       |          | Short describtion for the experiment |
| tags              |    x     | List of tags for experiment (scotty use this for monitoring etc.) |
| resources         |    x     | List of resource for the experiment (scotty/resource/demo for more information) |
| workload          |          | List of workloads for the experiment (scotty/workload/demo for more information) |

You can test the experiment localy with scotty

    scotty experiment perform

After this run you find your scotty data under the directory ./.scotty. You can clean it by calling:

    scotty experiment clean
    
Sample experiment.yaml

    description: my experiment with my workload
    tags:
      - my_tag
    resources:
      - name: my_resource_def
        generator: git:git@gitlab.gwdg.de:scotty/resource/demo.git
        params:
          user: myuser
          passwd: <%= ENV['mysecret'] %>
    workloads:
      - name: myworkload
        generator: file:.
        params:
          greeting: Hallo
        resource:
          my_resource: my_resource_def

