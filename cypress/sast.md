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

<kbd>![screenshot_new_file](https://github.com/syafiqhadzir/rnd-training/assets/34176032/38298cec-e637-4b35-a19e-d7253d3fed75)</kbd>

Copy and paste the following code:-

```javascript
console.log("Latihan DevOps")
```

Note: the GitLab runner is triggered each time a new commit is pushed to the repository.

### Step 2: Secret Detection

`GitLab Secret Detection` helps you prevent the unintentional leak of sensitive information like authentication tokens and private keys.

To enable this function, expand **Secure** on the left sidebar. Select **Security configuration**.

<kbd>![screenshot_security_configuration](https://github.com/syafiqhadzir/rnd-training/assets/34176032/b219c362-636b-4f4f-93b8-74339e8e4213)</kbd>

Go to **Secret Detection**, click **Configure with a merge request**.

<kbd>![screenshot_secret_detection](https://github.com/syafiqhadzir/rnd-training/assets/34176032/6acc0c2b-4bb9-42f7-92de-9d634fc14977)</kbd>

The **New merge request** form will be displayed.

<kbd>![screenshot_merge_request](https://github.com/syafiqhadzir/rnd-training/assets/34176032/609afde0-55b1-455a-b3bc-0ef97fa4a2f1)</kbd>

Click **Create merge request**.

<kbd>![screenshot_request_button](https://github.com/syafiqhadzir/rnd-training/assets/34176032/1e43c843-88c2-45c1-a270-500f4cc1b704)</kbd>

Then, click **Merge**.

<kbd>![screenshot_merge_button](https://github.com/syafiqhadzir/rnd-training/assets/34176032/4a52c543-a220-4ad0-be4b-0e2a30b2ca24)</kbd>

Note: to verify if the CI process is running, click **Build** > **Pipelines** on the left sidebar.

### Step 3: Personal Access Token
