!!! attention
    * `runai list` has been replaced by `runai list jobs`.
    * `runai clusters list` has been replaced by `runai list clusters`.
    * `runai project list` has been replaced by `runai list projects`.
    * `runai template list` has been replaced by `runai list templates`.

## Description

Show lists of Jobs, Projects, Clusters or Nodes.

## Synopsis

``` shell
runai list jobs 
    [--all-projects | -A]  

    [--loglevel value] 
    [--project string | -p string] 
    [--help | -h]

runai list projects 
    [--loglevel value] 
    [--help | -h]

runai list clusters  
    [--loglevel value] 
    [--help | -h]

runai list nodes [node-name]
    [--loglevel value] 
    [--help | -h]

runai list templates
    [--loglevel value] 
    [--help | -h]
```
## Options
`node-name` - Name of a specific node to list (optional).


--all-projects | -A
>  Show Jobs from all Projects.

### Global Flags

--loglevel (string)
>  Set the logging level. One of: debug | info | warn | error (default "info").

--project | -p (string)
>  Specify the project to which the command applies. By default, commands apply to the default project. To change the default Project use``runai config project <project-name>``.

--help | -h

>  Show help text.

## Output

* A list of Jobs, Nodes, Projects, Clusters, or Templates. 
* To filter 'runai list nodes' for a specific Node, add the Node name.

## See Also
To show details for a specific Job, Node or Template see [runai describe](runai-describe.md).


