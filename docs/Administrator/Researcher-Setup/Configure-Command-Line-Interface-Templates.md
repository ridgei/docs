## What are Templates?

Templates are a way to reduce the number of flags required when using the Command Line Interface to start workloads. Using Templates the researcher can:

*   Review list of templates by running ``runai template list``
*   Review the contents of a specific template by running ``runai template get <template-name>``
*   Use a template by running ``runai submit --template <template-name>``

The purpose of this document is to provide the administrator with guidelines on how to create templates.

## The Template Implementation

CLI Templates are implemented as_ Kubernetes <a href="https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/" target="_self">ConfigMaps</a>. A Kubernetes ConfigMap is the standard way to save cluster-wide settings.

To create a Run:AI CLI Template, you will need to save a ConfigMap on the cluster. The Run:AI CLI is then looking for ConfigMaps marked as Run:AI templates.

### Template Usage

The Researcher can use the Run:AI CLI to

Show a list of templates:

    runai template list

Showing the properties of a specific template:

    runai template get <my-template>

Use the template when submitting a workload

    runai submit <my-job> --template <my-template>

For further details, see the Run:AI command line reference <a href="https://support.run.ai/hc/en-us/articles/360011548039-runai-template" target="_self">template</a>&nbsp;&nbsp;and <a href="https://support.run.ai/hc/en-us/articles/360011436120-runai-submit" target="_self">submit</a> functions.

## Template Syntax

A template looks as follows:

    apiVersion: v1
    kind: ConfigMap
    data:
    name: cli-template1
    description: "my first template"
    values: |
        image: gcr.io/run-ai-demo/quickstart
        gpu: 1
        elastic: true
    metadata:
    name: cli-template1
    namespace: runai
    labels:
        runai/template: "true"

Notes:

*   The template above set 3 defaults: a specific image, a default of 1 gpu and sets the "elastic" flag to true
*   The label runai/template marks the ConfigMap as a Run:AI template.
*   The name and description will show when using the _runai template list_ command

To store this template run:

    kubectl apply -f <template-file-name>

For a complete list of template values, see the end of this document

## The Default Template

The administrator can also set a default template that is always used on runai submit whenever a template is __not__ specified. To create a default template use the annotation runai/default: "true". Example:

    apiVersion: v1
    kind: ConfigMap
    data:
    name: cli-template1
    description: "my first template"
    values: |
        volume:
        - '/path/on/host:/dest/container/path'
    metadata:
    name: cli-template1
    namespace: runai
    annotations:
        runai/default: "true"
    labels:
        runai/template: "true"

## Syntax of all Values

The following template sets all runai submit flags.

    apiVersion: v1
    kind: ConfigMap
    data:
    name: "all-cli-flags"
    description: "A sample showing all possible flag overrides via a template"
    values: |
        project: "team-ny"
        image: ubuntu
        gpu: 1
        cpu: 0.5
        memory: 1G
        elastic: false
        interactive: true
        node_type: "dgx-1"              # --node-type
        hostIPC: false                  # --host-ipc 
        shm: false                      # --large-shm 
        localImage: false               # --local-image
        serviceType: "loadbalancer"     # -- service-type
        ttlSecondsAfterFinished: 30     # --ttl-after-finish
        environmentDefault:
        - 'LEARNING_RATE=0.25'
        - 'TEMP=302'
        portsDefault:
        - '80:8888'
        - 9090
        command:
        - 'sleep'
        args:
        - 'infinity'
        volumeDefault:
        - '/etc:/dest/container/path'
        workingDir: "/etc".             # --working-dir
    metadata:
    name: cli-all-flags
    namespace: runai
    labels:
        runai/template: "true"