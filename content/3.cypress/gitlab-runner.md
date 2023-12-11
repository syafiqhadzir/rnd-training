<!-- omit in toc -->
# ![GitLab Runner](https://gitlab.msu.edu/uploads/-/system/project/avatar/6141/gitlab-ci-cd-logo_2x.png)

[GitLab Runner](https://docs.gitlab.com/runner/) is an application that works with GitLab CI/CD to run jobs in a pipeline.

<!-- omit in toc -->
## Table of Contents

- [Prerequisites](#prerequisites)
- [GitLab CI/CD Runner](#gitlab-cicd-runner)
  - [Step 1: Installation](#step-1-installation)
  - [Step 2: Configuration](#step-2-configuration)
  - [Step 3: Registration](#step-3-registration)
  - [Step 4: Validation](#step-4-validation)

## Prerequisites

- [x] GitLab Repository
- [x] Runner Server

## GitLab CI/CD Runner

### Step 1: Installation

On the project page, open any available repository.

<kbd>![screenshot_project_page](https://github.com/syafiqhadzir/rnd-training/assets/34176032/7e51236c-4b29-4f37-aee3-98bf5d0d2f4a)</kbd>

Once opened, select **Settings** > **CI/CD** on the left sidebar.

<kbd>![screenshot_settings_cicd](https://github.com/syafiqhadzir/rnd-training/assets/34176032/394523b7-2e4d-44b7-9cfd-2720409d3e9b)</kbd>

Search for the runner section, click **Expand** to expand the runner list.

<kbd>![screenshot_runner_expand](https://github.com/syafiqhadzir/rnd-training/assets/34176032/b1c7b949-026d-4742-a85d-7434b265435e)</kbd>

And click **New project runner**.

<kbd>![screenshot_new_project](https://github.com/syafiqhadzir/rnd-training/assets/34176032/ca082f98-b246-488d-bb77-87db6aa06e50)</kbd>

**Note:** for better experience, users are advised to disable shared runners.

<kbd>![screenshot_shared_runners](https://github.com/syafiqhadzir/rnd-training/assets/34176032/638c6492-0b45-408a-84f2-946f90d2ce38)</kbd>

### Step 2: Configuration

**Note:** This registration process is only supported in GitLab Runner 15.10 or later.

For the **Platform** section, select **Linux**.

<kbd>![screenshot_config_linux](https://github.com/syafiqhadzir/rnd-training/assets/34176032/8a1c42b7-5bc4-4277-943a-b0cc9e7ac235)</kbd>

For the **Tags** section, it is recommended to have tag as it helps to distinguish among the runners installed. Suggested tag, `self-hosted`.

When a CI/CD job runs, it knows which runner to use by looking at the assigned tags. Tags are the only way to filter the list of available runners for a job.

<kbd>![screenshot_config_tags](https://github.com/syafiqhadzir/rnd-training/assets/34176032/5c4da68d-61f3-4d98-ad19-95fb52598710)</kbd>

**Note:** Users are also advised to enable the **"Run untagged jobs"** features for personal and small projects. For tutoring purposes, all other fields are required to be left blank.

<kbd>![screenshot_create_runner](https://github.com/syafiqhadzir/rnd-training/assets/34176032/89cfd44a-88a0-4818-9afa-f066da5c743a)</kbd>

Click **"Create runner"** to proceed.

### Step 3: Registration

Copy and paste the displayed command to register the runner.

```bash
$ gitlab-runner register
  --url {gitlab_domain_url}
  --token {runner_authentication_token}
```

Choose an executor when prompted by the command line. Executors run builds in different environments.

To manually verify that the runner is available to pick up jobs:-

```bash
gitlab-runner run
```

### Step 4: Validation

To validate if the runner is running, go the **"Assigned project runners"** section and check if the status indicator turns green.

<kbd>![screenshot_assigned_runners](https://github.com/syafiqhadzir/rnd-training/assets/34176032/ab82a017-4fe3-4813-8ff9-3c210efc4fc4)</kbd>

Once the status indicator turned green, the runner is ready to receive jobs.
