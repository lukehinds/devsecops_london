# DevSecOps London Playalong session

This is a playalong session for the DevSecOps London meetup on 2024-09-24.

# Setup

1. Clone this repository

```bash
git clone git@github.com:lukehinds/devsecops_london.git
```

2. Fork a test repository, or use your own

[demo-repo-python](https://github.com/stacklok/demo-repo-python/fork)


2. Install the Minder CLI

MacOS:

```bash
brew install stacklok/tap/minder
```

Windows:
```bash
winget install stacklok.minder
```

Linux:
```bash
git clone git@github.com:stacklok/minder.git
cd minder
make build-minder-cli
```

* Path is : /bin/minder

# Login and create an account

```bash
minder auth login
```

# Create rules

```bash
minder ruletype create -f rules/
```

# Create a profile

```bash
minder profile apply -f devsecops.yaml
```
# Enroll a provider

```bash
minder provider enroll --provider github-app
```

# Register a repos

```bash
minder repo register
```

Select the repo you decided to use for the playalong.

# View the results of our scan

```bash
minder profile status list --detailed  --name devsecops-profile
```

![results_good_](img/result_good.png)

All good!

# Manual Remediaton

Let's now flip the secret scanning setting

Settings -> Code security and analysis -> Secret scanning [disable]

# View the results of our scan

```bash
minder profile status list --detailed  --name devsecops-profile
```

![result_bad](img/result_bad.png)

# Turn on automatic remediation

Here we will turn on automatic remediation

```bash
minder profile apply -f devsecops.yaml
```

# View the results of our scan again

```bash 
minder profile status list --detailed  --name devsecops-profile
```





