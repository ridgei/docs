# Administrator

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.


# Introduction

The Admin User Interface allows:

*   The setup of Kubernetes GPU Clusters.
*   Create, Update and Delete of users
*   Create, Update and Delete Projects.
*   Review short term and long term dashboards
*   Review Node and Job-status

This document is about the Creation, Update, and Deletion of Users.

**Notes:**

*   With Run:AI you need to differentiate between the users of the Admin UI and Researcher users which submit workloads on the GPU Kubernetes cluster. This document is about the former.
*   It is possible to connect the Admin UI users module to the organization's LDAP directory. For further information please contact Run:AI customer support.

# Working with Users

## Create User

Note: to be able to manipulate users, you must have _Administrator_ access. if you do not have such access, please contact an administrator. The list of administrators is shown on the Users page (see below)

*   Log in to [https://app.run.ai](https://app.run.ai)
*   On the top left, open the menu and select "Users"
*   On the top right, select "Add New Users".

![mceclip2.png](/hc/article_attachments/360008635560/mceclip2.png)

*   Choose a user name and email. Leave password as blank, it will be set by the user
*   Select Roles. Note -- more than one role can be selected
*   Select a Cluster. This determines the Clusters accessible to this user
*   Press "Save"

The user will receive a join mail and will be able to set a password. 

## Update a User

*   Select an existing User. 
*   Right-click and press "Edit"
*   Update the values and press "Save"

## Delete an existing User

*   Select an existing User. 
*   Right-click and press "Delete"