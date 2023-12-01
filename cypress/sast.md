<!-- omit in toc -->
# ![SAST](https://gitlab.msu.edu/uploads/-/system/project/avatar/6141/gitlab-ci-cd-logo_2x.png)

`Static application security testing (SAST)` is used to secure software by reviewing the source code of the software to identify sources of vulnerabilities.

<!-- omit in toc -->
## Table of Contents

- [Prerequisites](#prerequisites)
- [Security Testing](#security-testing)
  - [Step 1: Triggering Runner(s)](#step-1-triggering-runners)
  - [Step 2: Secret Detection](#step-2-secret-detection)
  - [Step 3: Personal Access Token](#step-3-personal-access-token)

## Prerequisites

- [x] GitLab Repository
- [x] GitLab Runner

## Security Testing

### Step 1: Triggering Runner(s)

Create **new file**.

<kbd>![screenshot_new_file](image.png)</kbd>

Copy and paste the following code:-

```javascript
console.log("Latihan DevOps")
```

Note: the GitLab runner is triggered each time a new commit is pushed to the repository.

### Step 2: Secret Detection

`GitLab Secret Detection` helps you prevent the unintentional leak of sensitive information like authentication tokens and private keys.

To enable this function, expand **Secure** on the left sidebar. Select **Security configuration**.

<kbd>![screenshot_security_configuration](image-1.png)</kbd>

Go to **Secret Detection**, click **Configure with a merge request**.

<kbd>![screenshot_secret_detection](image-2.png)</kbd>

The **New merge request** form will be displayed.

<kbd>![screenshot_merge_request](image-3.png)</kbd>

Click **Create merge request**.

<kbd>![screenshot_request_button](image-4.png)</kbd>

Then, click **Merge**.

<kbd>![screenshot_merge_button](image-5.png)

Note: to verify if the CI process is running, click **Build** > **Pipelines** on the left sidebar.

### Step 3: Personal Access Token
