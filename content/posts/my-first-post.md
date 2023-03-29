---
title: "Create a static website with Hugo and Host it with Github Pages"
date: 2023-03-29T15:17:39+03:00
draft: true
---

In this article, we will explain how to create a blog site that incurs a minimal cost and doesn’t need our own hosting server.

Introduction

Static websites like online resumé or blog sites can be created using HTML, CSS, and JavaScript if you are a front-end developer. However, it can be a bit of a headache for people who are not familiar with these technologies. More importantly, if you are creating a blog site, it’s difficult to maintain uniformity in all its pages. In this blog, I am going to describe how we can create a static website without the need for such technologies.

Tools Used

    - Hugo: A fast and modern static website engine
    - Any text editor of your choice. I prefer VS Code

Getting Started

1. Download and install Hugo. For more details, refer Hugo’s getting started guide.
2. Once Hugo is installed, open a terminal and go to the folder where you want to store the code for your blog or static website
3. Run `hugo new site <your-site-name>` to create a new website. It will create the following directories in the folder:
├── archetypes
├── config.toml
├── content
├── data
├── layouts
├── public
├── static
└── themes
4. Now, go to http://themes.gohugo.io/ and clone a theme of your choice in the themes folder. Once done, copy the config.toml from the downloaded theme into the root folder of the website and run hugo server --buildDrafts from the root directory. It will start the server on port 1313. You can access the site from http://localhost:1313
5. To create a new blog entry, run hugo new post/<blog-file-name>.md. It will create a file in content/post/ folder
6. Open the newly created file in the text editor of your choice and start drafting the blog
7. Once you are done drafting the content, delete the contents of public folder and run hugo command to regenerate the files
8. Create a repo on Github and check in the content of the public folder
9. Now go to your repository on https://github.com and create a new branch called gh-pages. Click on settings and go to GitHub Pages section of the page where you will see the following message: Your site is published at https://<user_name>.github.io/<repo-name>/. You can use this link to access your static website or blog. If you want to use a custom domain, please follow [this](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).

I have included a few links that may come in handy while following these steps. Please feel free to drop your questions in the comments section.

Any feedback or suggestions will be greatly appreciated.

References

    https://blog.clairvoyantsoft.com/create-a-static-website-with-hugo-and-host-it-with-github-pages-f268b12371
    https://gohugo.io/
    https://atom.io/
    https://help.github.com/articles/using-a-custom-domain-with-github-pages/