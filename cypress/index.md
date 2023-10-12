<!-- omit in toc -->
# Cypress

![Cypress](https://www.cypress.io/_astro/navbar-brand.0d71ff96.svg)

Open-source E2E testing tools & UI testing framework. Website: [https://www.cypress.io/](https://www.cypress.io/).

<!-- omit in toc -->
## Table of Contents

- [Using Graphical User Interface (GUI)](#using-graphical-user-interface-gui)
  - [Step 1: Initialisation](#step-1-initialisation)
  - [Step 2: Usage](#step-2-usage)

## Using Graphical User Interface (GUI)

### Step 1: Initialisation

First, we must create new folder and initiate new node project.

```bash
npm init -y
```

Then, Cypress should be installed inside the created folder.

```bash
npm install cypress@latest
```

Note: executing `npx cypress` requires Cypress installation.

### Step 2: Usage

To open interactive GUI:

```bash
npx cypress open
```
