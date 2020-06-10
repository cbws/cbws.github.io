A resources on the CBWS platform are part of a project, they help bundle related resources for a specific goal.

This guide describes how to create and use them to organize your resources.

## Creating a project

Creating projects requires the `Project creator` role on an organization, after creation you will get the
`Project owner` role allowing to fully manage resources in the newly created project.

!!! hint
    Since project names are unique across the entire CBWS platform it might be useful to for example prepend them
    with a abbreviation of your organization or product name.

=== "Panel"
    1. Click on the project selection button
    2. Click on create project

=== "CLI"
    ```bash
    cbws projects create test-project
    ```

=== "Golang"
    ```go
    package main
    
    import (
        "context"
        "log"
    
        projects "github.com/cbws/go-cbws/cbws/projects/v1alpha1"
        
    )
    func main() {
        p, err := projects.NewClient(context.Background())
        if err != nil {
            log.Fatalf("Error: %+v", err)
        }
    
        project, err := p.CreateProject(context.Background(), "//organizations.cloudbear.nl/organizations/908e6132-1eb9-11ea-939b-9c81b2f6bed2", "test-project")
        if err != nil {
            log.Fatalf("Error: %+v", err)
        }
        
        log.Printf("Project: %+v", project)
    }
    ```

=== "PHP"
    ```php
    <?php
    $projects = new \Cbws\API\Projects\V1alpha1\Client();
    $project = $projects->createProject('//organizations.cloudbear.nl/organizations/908e6132-1eb9-11ea-939b-9c81b2f6bed2', 'test-project');
    ```

## Listing projects

You generally have quite a few projects, listing all of them can be doing as follows:

=== "Panel"

=== "CLI"
    List all the projects you have access to, this will also include projects from organizations you've been given
    access to.

    ```bash
    cbws projects list
    ```

=== "Golang"
    This example uses the `PaginateProjects` helper method and the `Iterate` function of the CBWS pagination library
    to iterate through all the projects and handles pagination on the background.

    ```go
    package main
    
    import (
        "context"
        "log"
    
        projects "github.com/cbws/go-cbws/cbws/projects/v1alpha1"
        
    )
    func main() {
        p, err := projects.NewClient(context.Background())
        if err != nil {
            log.Fatalf("Error: %+v", err)
        }
    
        paginator := p.PaginateProjects()
        edges, err := pagination.Iterate(context.Background(), paginator)
        if err != nil {
            log.Fatalf("Error: %+v", err)
        }
    
        for _, edge := range edges {
            log.Printf("Project: %+v", edge.Node)
        }
    }
    ```

=== "PHP"
    ```php
    <?php
    $projects = new \Cbws\API\Projects\V1alpha1\Client();
    $data = $projects->listProjects();
    foreach ($data->getProjects() as $project) {
        var_dump($project);
    }
    echo 'Next page token: ' . $data->getNextPageToken() . PHP_EOL;
    ```

## Using a project

Most things you do on the CBWS platform will be done in the context of a project. Most tools will work in a specific
project so you can focus on the things at hand. It is however very easy to switch back and forth between different
projects.

=== "Panel"

    When you open the CBWS panel you can select a project by using the project selection button in the menu on the left.

=== "CLI"
    The CBWS command line tool generally operates on a specific project. This way you only see and manage the resources
    related to that specific project. Switching between projects can be done using the following command:

    ```bash
    cbws projects use test-project
    ```
    
    You can also use a flag to run a specfic command on a different project:
    
    ```bash
    cbws -p test-project iam service-accounts list
    ```

## Project IAM policies

When creating a new project, you will be the only one with the `Project owner` role. This will give you full access to
all resources within the project, and full access to the project itself. To give others or service accounts access to
your project or create a more specific access policy you can use the project IAM policies.

For more details IAM policies you can read the IAM getting started documentation.

!!! info
    To ensure we can help you we by default also give `Cloudbear tech support` the `Tech support` role on your project.
    You can remove this at any point, this does mean our support department won't be able to immediately help you.

### Getting current policy

### Changing policy

!!! warning
    Giving a principal the `setIAMPOlicy` permission will also this principal to give themselves more access.
