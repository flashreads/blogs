---
id: 002-aws-appstream-2.0.md
title: AWS Appstream 2.0 Technology
tags: 
  - cloud hosting
  - streaming
  - desktop apps
  - aws
date: 2022-10-28 
keywords: aws, cloud hosting
categories: cloud streaming
author: Salil Cuncoliencar
meta-description: brief overview on streamning desktop apps with Appstream 2.0 Technology
---

# AWS Appstream 2.0
Appstream 2.0 is a Managed service from AWS which helps users stream desktop apps securely in a browser. 
You no longer need access to a physical desktop machine to install apps, just use this technology and stream you apps online.
It supports 3 modes of authentication:
- SAML
- User Pool
- Programmatic

# Setup:
- You need to have an AWS account (Learning account would do)
- Setup your ImageBuilder from `AWS console` or via `AWS-CLI`. This is similar to baking an AMI in EC2.
- Install the required desktop apps on this Image and create final image
- Create a Fleet with appropriate configuration
- Setup a Stack and map it to a fleet
- Generate a temporary url from the Stack and share it for use to your peers, you can choose from 30 mins to 7 days


