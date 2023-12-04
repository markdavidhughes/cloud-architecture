---
title: "How this site was created"
date: 2023-04-12
draft: false
description: "Discover how to create your very own blog just like this one."
categories: ["Azure"]
tags: ["Hugo", "Static Web App", "GitHub"]
---

{{< lead >}}
Discover how to create your very own blog just like this one.
{{< /lead >}}

This site was built using Hugo and is hosted using a static web application in Microsoft Azure. There are associated GitHub actions which control how the site is built and published.

It uses the Blowfish theme created by Nuno Coração which available from [here.](https://github.com/nunocoracao/blowfish "here")

This guide also follows the Microsoft Learn guide available from [here.](https://learn.microsoft.com/en-us/azure/static-web-apps/publish-hugo "here")

If you'd like to build something similar you can follow the following steps:

## Prerequisites

* An Azure account with an active subscription. If you don't have one, you can [create an account for free.](https://azure.microsoft.com/free/ "create an account for free")
* A GitHub account. If you don't have one, you can also [create an account for free.](https://github.com/join "create an account for free")

## Create a Hugo application
1. In order to create a similar site you must first install Hugo. Follow the [installation guide](https://gohugo.io/installation/ "installation guide") for Hugo for your operating system.
2. Once installed, open a terminal and run the Hugo CLI to create a new site within your chosen directory.
```bash
hugo new site "Example Site"
```
3. Change directory into the newly created site.
```bash
cd "Example Site"
```
4. Initialize a Git repository for the new site.
```bash
git init
```
5. Next create a main branch.
```bash
git branch -M main
```
6. Then add the Blowfish theme to the site by installing the theme as a git submodule.
```bash
git submodule add https://github.com/nunocoracao/blowfish themes/blowfish
```
7. Now apply the example site to give the new site some content.
```bash
cp -r themes/blowfish/exampleSite/* ./
```
8. Commit the changes to the main branch.
```bash
git add -A
git commit -m "initial commit"
```
9. Preview the example site by running the following and then browsing to `http://localhost:1313/blowfish`.
```bash
hugo server
```