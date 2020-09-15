## Description

Submit a Distributed Training (MPI) Run:AI job for execution

## Synopsis

    runai submit-mpi job-name  
        [--always-pull-image] 
        [--args stringArray] 
        [--backoffLimit int] 
        [--command stringArray] 
        [--cpu double] 
        [--cpu-limit double] 
        [--environment stringArray | -e stringArray] 
        [--gpu int | -g int] 
        [--host-ipc] 
        [--host-network] 
        [--image string | -i string] 
        [--interactive] 
        [--large-shm] 
        [--local-image] 
        [--memory string] 
        [--memory-limit string] 
        [--node-type string] 
        [--prevent-privilege-escalation]
        [--processes int] 
        [--pvc [StorageClassName]:Size:ContainerMountPath:[ro]]
        [--run-as-user] 
        [--volume stringArray | -v stringArray] 
        [--working-dir]  
        .
        [--loglevel string] 
        [--project string | -p string] 
        [--help | -h]

 Syntax notes:

*   Options with value type of stringArray mean that you can add multiple values. You can either separate values with a comma or add the flag twice.

## Options

<job-name\> the name of the job.

--always-pull-image stringArray

>  When starting a container, always pull the image from registry, even if cached on running node. This is useful when you are re-saving updates to the image using the same tag.

--args stringArray

>  Arguments to pass to the command run on container start. Use together with ``--command``.   
>  Example: ``--command sleep --args 10000`` 

--backoffLimit int
 
> The number of times the job will be retried before failing. Zero or larger. The default is 6. This flag will only work with training workloads (when the ``--interactive`` flag is not specified)

--command stringArray

>  Command to run at container start. Use together with ``--args``.

--cpu double

> CPU units to allocate for the job (0.5, 1, .etc). The Job will receive at least this amount of CPU. Note that the Job will __not__ be scheduled unless the system can guarantee this amount of CPUs to the job.

--cpu-limit double

> Limitations on the number of CPU consumed by the job (0.5, 1, .etc). The system guarantees that this Job will not be able to consume more than this amount of GPUs.

-e stringArray | --environment stringArray

>  Define environment variables to be set in the container. To set multiple values add the flag multiple times (``-e BATCH_SIZE=50 -e LEARNING_RATE=0.2``) or separate by a comma (``-e BATCH_SIZE:50,LEARNING_RATE:0.2``)

--gpu int | -g int

>  Number of GPUs to allocate to the Job. The default is no GPUs.

--host-ipc

>  Use the host's _ipc_ namespace. Controls whether the pod containers can share the host IPC namespace. IPC (POSIX/SysV IPC) namespace provides separation of named shared memory segments, semaphores and message queues.
> Shared memory segments are used to accelerate inter-process communication at memory speed, rather than through pipes or through the network stack
> 
> For further information see docker <a href="https://docs.docker.com/engine/reference/run/" target="_self">documentation</a>


--host-network

>  Use the host's networkstack inside the container
>  For further information see docker <a href="https://docs.docker.com/engine/reference/run/" style="background-color: #ffffff; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif;" target="_self">documentation</a>

--image string | -i string

>  Image to use when creating the container for this Job

--interactive

>  Mark this Job as Interactive. Interactive jobs are not terminated automatically by the system

--large-shm

> Mount a large /dev/shm device. _shm_ is a shared file system mounted on RAM

--local-image

>  Use a local image for this job. A local image is an image which exists on all local servers of the Kubernetes Cluster.

--memory string

> CPU memory to allocate for this job (1G, 20M, .etc).The Job will receive at least this amount of memory. Note that the Job will __not__ be scheduled unless the system can guarantee this amount of memory to the job.

--memory-limit string

>  CPU memory to allocate for this job (1G, 20M, .etc).The system guarantees that this Job will not be able to consume more than this amount of memory. The Job will receive an error when trying to allocate more memory than this limit.

--node-type string

>  Allows defining specific Nodes (machines) or a group of Nodes on which the workload will run. To use this feature your administrator will need to label nodes as explained here: [Limit a Workload to a Specific Node Group](../../Administrator/Researcher-Setup/limit-to-node-group.md)
> This flag can be used in conjunction with Project-based affinity. In this case, the flag is used to refine the list of allowable node groups set in the project. For more information see: [Working with Projects](../../Administrator/Admin-User-Interface-Setup/Working-with-Projects.md)

--prevent-privilege-escalation

> Prevent the job’s container and all launched processes from gaining additional privileges after the job starts. Default is ``false``. For more information see [Privilege Escalation](https://kubernetes.io/docs/concepts/policy/pod-security-policy/#privilege-escalation).

--processes int

> Number of distributed training processes. The default is 1.

--pvc `[Storage_Class_Name]:Size:Container_Mount_Path:[ro]`

--pvc `Pvc_Name:Container_Mount_Path:[ro]`

> Mount a persistent volume claim into a container
>
> The 2 syntax types of this command are mutually exclusive. You can either use the first or second form, but not a mixture of both.

> __Storage_Class_Name__ is a storage class name which can be obtained by running ``kubectl get storageclasses.storage.k8s.io``. This parameter may be omitted if there is a single storage class in the system, or you are using the default storage class. 

>    __Size__ is the volume size you want to allocate. See [Kubernetes documentation](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/) for how to specify volume sizes

>    __Container_Mount_Path__. A path internal to the container where the storage will be mounted

>    __Pvc_Name__. The name of a pre-existing [Persistent Volume Claim](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#dynamic) to mount into the container
> 
> Examples:

> ``--pvc :3Gi:/tmp/john:ro``  - Allocate `3GB` from the default Storage class. Mount it to `/tmp/john` as read-only 

> ``--pvc my-storage:3Gi:/tmp/john:ro``  - Allocate `3GB` from the `my-storage` storage class. Mount it to /tmp/john as read-only 

> ``--pvc :3Gi:/tmp/john`` - Allocate `3GB` from the default storage class. Mount it to `/tmp/john` as read-write 

> ``--pvc my-pvc:/tmp/john`` - Use a Persistent Volume Claim named `my-pvc`. Mount it to `/tmp/john` as read-write 

> ``--pvc my-pvc-2:/tmp/john:ro`` - Use a Persistent Volume Claim named `my-pvc-2`. Mount it to `/tmp/john` as read-only

--run-as-user

>  Run in the context of the current user running the Run:AI command rather than the root user. While the default container user is _root_ (same as in Docker), this command allows you to submit a job running under your Linux user. This would manifest itself in access to operating system resources, in the owner of new folders created under shared directories etc.

--volume stringArray | -v stringArray

>  Volume to mount into the container. Example ``-v /raid/public/john/data:/root/data:ro`` The flag may optionally be suffixed with ``:ro`` or ``:rw`` to mount the volumes in read-only or read-write mode, respectively.

--working-dir string

>  Starts the container with the specified directory

### Global Flags

--loglevel (string)

>  Set the logging level. One of: debug|info|warn|error (default "info")

--project | -p (string)

>  Specify the project to which the command applies. Run:AI Projects are used by the scheduler to calculate resource eligibility. By default, commands apply to the default project. To change the default project use ``runai project set <project-name>``.

--help | -h

>  Show help text

## Examples

start an unattended mpi training job of name dist1, based on project _team-a_ using a _quickstart-distributed_ image:

    runai submit-mpi dist1 --num-processes=2 -g 1 \
        -i gcr.io/run-ai-demo/quickstart-distributed 

## Output

The command will attempt to submit an _mpi_ job. You can follow up on the job by running ``runai list`` or ``runai get job-name``

## See Also

*   See Walk-through document [Walk-through: Running Distributed Training](../Walkthroughs/walkthrough-distributed-training.md).