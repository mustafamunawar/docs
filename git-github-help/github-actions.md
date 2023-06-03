# Github Actions (GHA)

## Overview

- GHA allows you to automate, customize, and execute your software development `workflows` right in your repository

- GitHub Actions (GHA) is a continuous integration and continuous delivery (CI/CD) platform that allows you to automate your build, test, and deployment pipeline.

- GHA automatically executes a `workflow` whenever some `event` occures.

- You can configure a GHA `workflow` to be triggered when an `event` occurs in your repository.

- A `workflow` is a configurable automated process that will run one or more `jobs`. Workflows are defined by a YAML file checked in to your repository and will run when triggered by an event in your repository, or they can be triggered manually, or at a defined schedule.

- Workflows are defined in the `.github/workflows` directory in a repository, and a repository `can have multiple workflows`, each of which can perform a different set of tasks.

- You can reference a workflow within another workflow. For more information

- Examples of GHA `events`: `a pull request is created`, `an issue is created` and `someone pushes a commit to a repository` etc.

- A GHA `workflow` is consists of one or more `jobs` which can run in sequential order or in parallel.

- You can `configure a job's dependencies with other jobs`; by default, jobs have no dependencies and run in parallel with each other. When a job takes a dependency on another job, it will wait for the dependent job to complete before it can run.

- Each `job` will run inside its own virtual machine `runner`, or inside a `container`, and has one or more `steps` that either run `a script that you define` or run an `action`, which is a reusable extension that can simplify your workflow.

- A `job` is a set of `steps` in a workflow that is executed on the same runner.

- Each `step` is either a `shell script` that will be executed, or an `action` that will be run. Steps are executed in order and are dependent on each other. Since each step is executed on the same runner, you can share data from one step to another. For example, you can have a step that builds your application followed by a step that tests the application that was built.

- An `action` is a custom application for the GitHub Actions platform that performs a complex but frequently repeated task.

- An `action` can be used as a `step` in a `workflow`

- `Actions` help reduce the amount of repetitive code that you write in your workflow files.

- For example an `action` can `pull your git repository from GitHub`, `set up the correct toolchain for your build environment`, or `set up the authentication` to your cloud provider.

- You can write your own `actions`, or you can find commonly used `actions` in the `GitHub Marketplace`.

- A `runner` is a server that runs your workflows when they're triggered.

- Each runner can run `a single job at a time`.

- GitHub provides Ubuntu Linux, Microsoft Windows, and macOS runners to run your workflows; each workflow `run` executes in a fresh, newly-provisioned virtual machine. GitHub also offers larger runners, which are available in larger configurations.

- Besides Github runners, you can host your own runners called `self-hosted runners`.
