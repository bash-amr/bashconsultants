---
title: Configuration
excerpt: Configuration file contents and regeneration steps.
lastmod: 2024-05-31T01:57:04.547Z
config-dir: pages/_about/settings
config-file: _config.yml
permalink: /about/config/
---

## Configuration File for Site

The configuration file for the site is located in the `{{ page.config-dir }}` directory. The file is named `{{ page.config-file }}`. The contents of the file are included below.
This page also includes the steps to regenerate the configuration file to ensure that the site is up-to-date with the latest changes.

## Regenerate Config File with PowerShell

Regenerate the configuration file by following the steps below:

```powershell
# Regenerate Config File

cd ~/github/{{ site.local_repo }} # Navigate to the repository
cp {{ page.config-file }} {{ page.config-dir  }}/config-utf16.txt # Copy the config file
Get-Content {{ page.config-dir  }}/config-utf16.txt | Set-Content -Encoding UTF8 {{ page.config-dir }}/{{ page.config-file }} # Convert to UTF-8
```
## Regenerate Config File with Bash

```bash
# Regenerate Config File

cd ~/github/{{ site.local_repo }} # Navigate to the repository
cp {{ page.config-file }} {{ page.config-dir  }}/{{ page.config-file }} # Copy the config file
```

## Generated Config File

This is the contents of the configuration file:

```yml
# Include sitemap/config.yml
{% include_relative {{ page.config-file }} %}
```
