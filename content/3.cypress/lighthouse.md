<!-- omit in toc -->
# ![Lighthouse](https://wd.imgix.net/image/MtjnObpuceYe3ijODN3a79WrxLU2/QXJ5lmcjHEFLTHg5B4o8.svg)

[Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/) is an open-source, automated tool for automated auditing, performance metrics, and best practices for the web.

<!-- omit in toc -->
## Table of Contents

- [Prerequisites](#prerequisites)
- [UI/UX Testing](#uiux-testing)
  - [Step 1: Initialisation](#step-1-initialisation)
  - [Step 2: Configuration](#step-2-configuration)
  - [Step 3: GitLab CI Configuration](#step-3-gitlab-ci-configuration)

## Prerequisites

- [x] GitLab Runner

## UI/UX Testing

### Step 1: Initialisation

First, we must create new folder and initiate new node project.

```bash
npm init -y
```

The `Lighthouse CI` should be installed inside the recently created folder.

```bash
npm install lighthouse
```

**Note:** user should create `.gitignore` file. Copy and paste the following code:-

```
node_modules
.lighthouseci
```

### Step 2: Configuration

Create `lighthouserc.js`. Copy and paste the following code:-

```js
module.exports = {
  ci: {
    collect: {
      numberOfRuns: 1,
      url: ['https://www.google.com/'],
      settings: {
        // exclude "pwa" category
        onlyCategories: [
          'performance',
          'accessibility',
          'best-practices',
          'seo',
        ],
        chromeFlags: '--no-sandbox',
        extraHeaders: JSON.stringify({
          Cookie: 'customCookie=1;foo=bar',
        }),
      },
    },
    assert: {
      assertions: {
        'categories:performance': [
          'error',
          { minScore: 0.9, aggregationMethod: 'median-run' },
        ],
        'categories:accessibility': [
          'error',
          { minScore: 1, aggregationMethod: 'pessimistic' },
        ],
        'categories:best-practices': [
          'error',
          { minScore: 1, aggregationMethod: 'pessimistic' },
        ],
        'categories:seo': [
          'error',
          { minScore: 1, aggregationMethod: 'pessimistic' },
        ],
      },
    },
    upload: {
      target: 'temporary-public-storage',
    },
  },
}
```

### Step 3: GitLab CI Configuration

Create `.gitlab-ci.yml`. Copy and paste the following code:-

```yml
image: cypress/browsers:node18.6.0-chrome105-ff104

stages:
  - test

workflow:
  rules:
    # run MERGE REQUEST PIPELINE if a merge request is created/updated
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'
    # don't run BRANCH PIPELINE if a MR is already opened on this branch
    - if: '$CI_COMMIT_BRANCH && $CI_OPEN_MERGE_REQUESTS'
      when: never
    # run BRANCH PIPELINE if a commit is pushed on any branch
    - if: '$CI_COMMIT_BRANCH'

lighthouse:
  allow_failure: true
  script:
    - npm install
   # - npm run build
    - npm ci
    - npm install @lhci/cli
    - lhci autorun --upload.target=temporary-public-storage --collect.settings.chromeFlags="--no-sandbox" || echo "LHCI failed!"
  stage: test
  rules:
    # run MERGE REQUEST PIPELINE if a merge request is created/updated
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'
    # run BRANCH PIPELINE if a commit is pushed on master
    - if: '$CI_COMMIT_BRANCH == "master"'

```

### Step 4 (Optional): Using Node CLI

The Node CLI provides the most flexibility in how Lighthouse runs can be configured and reported. Users who want more advanced usage, or want to run Lighthouse in an automated fashion should use the Node CLI.

```bash
npx lighthouse www.google.com
```

**Note:** Lighthouse requires Node 18 LTS (18.x) or later.
