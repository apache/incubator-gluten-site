---
layout: page
title: How To Scan Security issues
nav_order: 11
parent: Developers
grand_parent: Documentations
permalink: /docs/developers/how-to-security-scan/
---
# How to scan the security issues

This section outlines the steps to use tools to scan Apache Gluten (incubating) source code and make sure no vulnerability issues in the code.
All projects under the Apache umbrella must adhere to the [Apache Release Policy](https://www.apache.org/legal/release-policy.html). This guide is designed to assist you in comprehending the policy and navigating the process of releasing projects at Apache.

## Scan Security Process

Before every Apache Gluten (incubating) release, we need to ensure there is no vulnerability issue in the source code.
We use [Trivy](https://github.com/aquasecurity/trivy) as the tool to scan all the security issues.


1. Install Trivy, please follow the steps to install Trivy: [Trivy Installation](https://trivy.dev/latest/getting-started/installation/)

2. Configuring Trivy, please follow the guide to configure Trivy for specific operation: [Trivy Configuration](https://trivy.dev/latest/docs/configuration/)

3. Run Trivy File System Scan with the source code. Below is an example about how we run Trivy scan with Apache Gluten (incubating) source code. You can use your own tpl file as a template.

```bash
trivy fs --list-all-pkgs --format template --template "@/PATH/TO/csv.tpl" --output ./trivy-report.csv /PATH/TO/GLUTEN_LOCATION/
```

4. Open the report file and check if there is any vulnerability issue highlighted. We must guarantee all the vulnerability issue has been solved before an official release.
