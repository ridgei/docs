## November 25th, 2020

Syntax changes in CLI:

* `runai <object> list`  has been replaced by `runai list <object>`.
* `runai get` has been replaced by `runai describe`.
* `runai <object> set` has been replaced by `runai config <object>`.

The older style will still work with a deprecation notice.

`runai top node` has been revamped.



## November 12th, 2020
An Admin can now create __templates__ for the Command-line interface. Both a default template and specific templates that can be used with the --template flag. The new templates allow for mandatory values, defaults and run-time environment variable resolution.
See [here](../Administrator/Researcher-Setup/template-config.md) for more.

It is now also possible to pass __Secrets__ to jobs. see [here](../Administrator/Researcher-Setup/use-secrets.md)

## November 2nd, 2020

Several changes and additions to the Command-line interface:

* __Passing a command__ and arguments is now done docker-style by adding `--` at the end of the command
* You no longer need to __provide a job name__. If you don't, a job name will be generated automatically. You can also control the job-name prefix using an additional flag. 
* New `--image-pull-policy` flag, allowing Researcher support for updating images without tagging.

For further information see [runai submit](../Researcher/cli-reference/runai-submit/)

## September 6th, 2020

We released a module that helps the Researcher perform __Hyperparameter optimization__ (HPO). HPO is about running many smaller experiments with varying parameters to help determine the optimal parameter set [Hyperparameter Optimization Quickstart](../Researcher/Walkthroughs/walkthrough-hpo.md)

<!-- ## September 3rd, 2020

__GPU Fractions__ now run in training and not only interactive. GPU Fractions training jobs can be preempted, bin-packed and consolidated like any integer jobs. See [Run:AI Scheduler Fraction](../../Researcher/Scheduling/The-Run-AI-Scheduler/#gpu-fractions) for more. -->


## August 10th, 2020

Run:AI Now supports __Distributed Training__ and __Gang Scheduling__. For further information , see the [Launch Distributed Training Workloads](../Researcher/Walkthroughs/walkthrough-distributed-training.md) quickstart.

## August 4th, 2020

There is now an optional second level of Project hierarchy called __Departments__. For further information on how to configure and use Departments, see [Working with Departments](../Administrator/Admin-User-Interface-Setup/Working-with-Departments.md) 

## July 28th, 2020

You can now enforce a cluster-wise setting that mandates all containers running using the Run:AI CLI to run as __non root__. For further information, see [Enforce non-root Containers](../Administrator/Cluster-Setup/enforce-run-as-user.md)

## July 21th, 2020

It is now possible to mount a __Persistent Storage Claim__ using the Run:AI CLI. See the ``--pvc`` flag in the [runai submit](../Researcher/cli-reference/runai-submit.md) CLI flag


## June 13th, 2020

#### New Settings for the Allocation of CPU and Memory

It is now possible to __set limits for CPU and memory__ as well as to establish defaults based on the ratio of GPU to CPU and GPU to memory. 

For further information see: [Allocation of CPU and Memory](../Researcher/Scheduling/Allocation-of-CPU-and-Memory.md)

## June 3rd, 2020

#### Node Group Affinity

Projects now support _Node Affinity._ This feature allows the administrator to assign specific projects to run only on specific nodes (machines). Example use cases:

*   The project team needs specialized hardware (e.g. with enough memory)
*   The project team is the owner of specific hardware which was acquired with a specialized budget
*   We want to direct build/interactive workloads to work on weaker hardware and direct longer training/unattended workloads to faster nodes

For further information see: [Working with Projects](../Administrator/Admin-User-Interface-Setup/Working-with-Projects.md)

#### Limit Duration of Interactive Jobs

Researchers frequently forget to close Interactive jobs. This may lead to a waste of resources. Some organizations prefer to limit the duration of interactive jobs and close them automatically. 

For further information on how to set up duration limits see: [Working with Projects](../Administrator/Admin-User-Interface-Setup/Working-with-Projects.md)

## May 24th, 2020

#### Kubernetes Operators

Cluster installation now works with Kubernetes _Operators_. Operators make it easy to install, update, and delete a Run:AI cluster. 

For further information see: [Upgrading a Run:AI Cluster Installation](../Administrator/Cluster-Setup/cluster-upgrade.md) and [Deleting a a Run:AI Cluster Installation](../Administrator/Cluster-Setup/cluster-delete.md)

## March 3rd, 2020

#### Admin Overview Dashboard

A new admin overview dashboard which shows a more holistic view of multiple clusters. Applicable for customers with more than one cluster.