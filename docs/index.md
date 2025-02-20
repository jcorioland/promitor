---
layout: default
title: Promitor - An Azure Monitor scraper for Prometheus
---

[![License](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square)](https://github.com/tomkerkhove/promitor/blob/master/LICENSE)[![Build Status](https://img.shields.io/azure-devops/build/tomkerkhove/promitor/50/master.svg?label=Scraper%20Agent%20-%20CI&style=flat-square)](https://dev.azure.com/tomkerkhove/Promitor/_build/latest?definitionId=50&branchName=master) [![Docker Pulls](https://img.shields.io/docker/pulls/tomkerkhove/promitor-agent-scraper.svg?style=flat-square)](https://hub.docker.com/r/tomkerkhove/promitor-agent-scraper/)
[![Docker Stars](https://img.shields.io/docker/stars/tomkerkhove/promitor-agent-scraper.svg?style=flat-square)](https://hub.docker.com/r/tomkerkhove/promitor-agent-scraper/)[![Donate](https://img.shields.io/badge/Donate%20via-PayPal-blue.svg?style=flat-square)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=LYCEDSP3S5P9G&source=url)

**Promitor** is an **Azure Monitor scraper for Prometheus** providing a scraping endpoint for Prometheus that provides a configured subset of Azure Monitor metrics.

{:refdef: style="text-align: center;"}
![Promitor](./media/logos/promitor.png)
{: refdef}

# Running Promitor Scraper
Running Promitor Scraper is super easy:
```
docker run -d -p 8999:80 --name promitor-agent-scraper \
                         --env PROMITOR_AUTH_APPID='<azure-ad-app-id>'   \
                         --env-file C:/Promitor/az-mon-auth.creds \
                         --volume C:/Promitor/metrics-declaration.yaml:/config/metrics-declaration.yaml \ 
                         tomkerkhove/promitor-agent-scraper:1.0.0-preview-7
```

Docker image is available on [Docker Hub](https://hub.docker.com/r/tomkerkhove/promitor-agent-scraper/).

# Features

- Provides scraping endpoint for Prometheus
- Automatically scrapes Azure Monitor metrics
- Built-in support for a variety of Azure services ([overview](configuration/metrics))
- Easy to declare metrics to scrape via YAML & APIs
- Easily deployable via Docker & Kubernetes
- Sends telemetry to Azure Application Insights

And there is more on the way - Check our [backlog](https://github.com/tomkerkhove/promitor/issues) and vote for features!

# Documentation
- **Deployment**
    - [Running Promitor on Docker](deployment#docker)
    - [Running Promitor on Kubernetes](deployment#kubernetes)
    - [Image Tagging Strategy](deployment#image-tagging-strategy)
- **Metrics**
    - [General Declaration](configuration/metrics)
    - [Supported Providers](configuration/metrics#supported-azure-services)
- **Configuration**
    - [Runtime](configuration#runtime)
    - [Scraping](configuration#scraping)
    - [Authentication with Azure Monitor](configuration#authentication-with-azure-monitor)
    - [Logging & External Providers](configuration#logging)
- **Operations**
    - [Azure Resource Manager API - Consumption & Throttling](operations#azure-resource-manager-api---consumption--throttling)
    - [Health](operations#health)
- **Walkthroughs**
    - [Deploying Promitor, Prometheus, and Grafana on an AKS Cluster](/walkthrough)

# Support
Promitor is actively maintained and developed with best-effort support.

We do welcome PRs that implement features from our backlog and are always happy to help you incorporate Promitor in your infrastructure, but do not provide 24/7 support. Are you having issues or feature requests?

Feel free to [let us know](https://github.com/tomkerkhove/promitor/issues/new/choose)!

# Thank you!
We'd like to thank all the services, tooling & NuGet packages that support us - [Thank you](thank-you)!

# License Information
This is licensed under The MIT License (MIT). Which means that you can use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the web application. But you always need to state that Tom Kerkhove is the original author of this web application.
