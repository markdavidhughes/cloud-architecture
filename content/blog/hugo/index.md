---
title: "How this site was created."
date: 2023-11-29
draft: false
description: "Discover how to create your very own blog just like this one."
categories: ["Azure"]
tags: ["Hugo", "Static Web App", "GitHub"]
---

{{< lead >}}
Discover how to create your very own blog just like this one.
{{< /lead >}}

The original aim of Blowfish was to develop a theme that was simple and lightweight. The theme is a fork of <a target="_blank" href="https://github.com/nunocoracao/congo">Congo</a> and expands its initial vision.

## Tailwind CSS 3.0

Tailwind CSS is at the heart of Blowfish and this release contains the very latest [Tailwind CSS version 3](https://tailwindcss.com/blog/tailwindcss-v3). It brings with it performance optimisations and support for some great new CSS features.

{{< youtube "TmWIrBPE6Bc" >}}

## Multilingual support

A highly requested feature, Blowfish is now multilingual! If you publish your content in multiple languages, the site will be built with all the translations available.

<div class="text-2xl text-center" style="font-size: 2.8rem">:gb: :de: :fr: :es: :cn: :brazil: :tr: :bangladesh:</div>

Thanks to submissions from the community, Blowfish has already been translated into [eight languages](https://github.com/nunocoracao/blowfish/tree/main/i18n) with more to be added over time. By the way, [pull requests](https://github.com/nunocoracao/blowfish/pulls) for new languages are always welcome!

## RTL language support

One of the benefits of the new Tailwind and Multilingual features is the ability to add RTL language support. When enabled, the entire site will reflow content from right-to-left. Every element in the theme has been restyled to ensure it looks great in this mode which aids authors who wish to generate content in RTL languages.

RTL is controlled on a per-language basis so you can mix and match both RTL and LTR content in your projects and the theme will respond accordingly.

## Automatic image resizing

A big change in Blowfish 2.0 is the addition of automatic image resizing. Using the power of Hugo Pipes, images in Markdown content are now automatically scaled to different output sizes. These are then presented using HTML `srcset` attributes enabling optimised file sizes to be served to your site visitors.

![](image-resizing.png)

```html
<!-- Markdown: ![My image](image.jpg) -->
<img
  srcset="
    /image_320x0_resize_q75_box.jpg 320w,
    /image_635x0_resize_q75_box.jpg 635w,
    /image_1024x0_resize_q75_box.jpg 1024w,
    /image_1270x0_resize_q75_box.jpg 2x"
  src="/image_635x0_resize_q75_box.jpg"
  alt="My image"
/>
```

Best of all there's nothing you need to change! Simply insert standard Markdown image syntax and let the theme do the rest. If you want a little more control, the `figure` shortcode has been completely rewritten to provide the same resizing benefits.


## Site search

Powered by [Fuse.js](https://fusejs.io), site search allows visitors to quickly and easily find your content. All searches are performed client-side meaning there's nothing to configure on the server and queries are performed super fast. Simply enable the feature in your site configuration and you're all set. Oh, and it also supports full keyboard navigation!

## Tables of contents

A highly requested feature, Blowfish now supports tables of contents on article pages. You can see it in action on this page. The contents are fully responsive and will adjust to take advantage of the space available at different screen resolutions.

Available on a global or per article basis, the table of contents can be fully customised using standard Hugo configuration values, allowing you to adjust the behaviour to suit your project.

## Accessibility improvements

From adding ARIA descriptions to more items or simply adjusting the contrast of certain text elements, this release is the most accessible yet.

Version 2 also introduces "skip to content" and "scroll to top" links that enable quick navigation. There's also keyboard shortcuts for enabling items like search without reaching for the mouse.

The new image resizing features also provide full control over `alt` and `title` elements enabling an accessible experience for all visitors.

## A whole lot more

There's countless other features to explore. From being able to display taxonomies on articles and list pages, to using the new `headline` author parameter to customise your homepage. There's also improved JSON-LD strucured data which further optimises SEO performance. 




This site was built using Hugo and is hosted using a static web application on Azure. There are associated GitHub actions which control how the site is built and published.

It uses the Stack theme created by Jimmy Cai. This is available from here.

This guide also follows the Microsoft Learn guide available from here.

If you'd like to build something similar you can follow the following steps:

Prerequisites
An Azure account with an active subscription. If you don't have one, you can create an account for free.
A GitHub account. If you don't have one, you can create an account for free.
Create a Hugo application
In order to create a similar site you must first install Hugo. Follow the installation guide for Hugo for your OS.
Open a terminal.
Run the Hugo CLI to create a new app.
hugo new site new-app
Go to the newly created app.
cd new-app
Initialize a Git repo.
git init
Create a main branch
git branch -M main
Add the Stack theme to the site by installing the theme as a git submodule.
git submodule add https://github.com/CaiJimmy/hugo-theme-stack/ themes/hugo-theme-stack
Apply the example site to give the new site some content.
cp -r themes/hugo-theme-stack/exampleSite/* ./
Now remove the config.toml that was generated by Hugo as this is replaced by the config.yaml file from the example site.
rm config.toml
Commit the changes to the main branch.
git add -A
git commit -m "initial commit"
Preview the example site by running the following and then browsing to http://localhost:1313/.
hugo server
Example Site running locally

Publish to GitHub
A GitHub repository is neeced to connect to Azure Static Web Apps.

Create a blank GitHub repo (don't create a README) here named new-app.
Add the GitHub repository as a remote to your local repo. Replace <YOUR_USER_NAME> with your GitHub username.
git remote add origin https://github.com/<YOUR_USER_NAME>/hugo-static-app
Push your local repo up to GitHub.
git push --set-upstream origin main
Your site now in GitHub

Deploy your web app
The following steps show you how to create a new static site app and deploy it to a production environment.

Create the application
Go to the Azure Portal.
Select Create a Resource.
Search for Static Web Apps.
Select Static Web Apps.
Select Create.
On the Basics tab, enter the following values.
Property	Value
Subscription	Your Azure subscription name.
Resource group	new-group
Name	new-app
Plan type	Free
Region for Azure Functions API and staging environments	Select a region closest to you.
Source	GitHub
Select Sign in with GitHub and authenticate with GitHub.
Enter the following GitHub values.
Property	Value
Organization	Select your desired GitHub organization.
Repository	Select new-app.
Branch	Select main.
In the Build Details section, select Hugo from the Build Presets drop-down and keep the default values.
Create your new web app

Review and create
Select Review + Create to verify the details are all correct.
Select Create to start the creation of the App Service Static Web App and provision a GitHub Actions for deployment.
Once the deployment completes, select Go to resource.
On the resource screen, select the URL link to open your deployed application. You may need to wait a minute or two for the GitHub Actions to complete.
Review your new web app

Your fully deployed web app running in Azure

Conclusion
This will provide you with an Azure static web app similar to mine with the Stack theme applied. From here you can add a custom domain and further customise the site.