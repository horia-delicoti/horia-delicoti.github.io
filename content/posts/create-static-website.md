---
title: "Create a static website with Hugo and Host it with Github Pages"
subtitle: "In this article, we will explain how to create a blog site that incurs a minimal cost and doesn’t need our own hosting server."
date: 2023-03-29T15:17:39+03:00
draft: false

tags: [hugo, website]
categories: []
fontawesome: true
linkToMarkdown: true
rssFullText: false
---
## Introduction

Static websites like online resume or blog sites can be created using HTML, CSS, and JavaScript if you are a front-end developer. However, it can be a bit of a headache for people who are not familiar with these technologies. More importantly, if you are creating a blog site, it’s difficult to maintain uniformity in all its pages. I am going to describe how we can create a static website without the need for such technologies.

#### Tools Used

* [Hugo][hugo]: A fast and modern static website engine
* Any text editor of your choice. I prefer [VS Code][vscode]

#### Getting Started

1. Download and [install Hugo][hugo_installation]. For more details, refer Hugo’s [getting started][hugo_getting_started] guide.
2. Once Hugo is installed, open a terminal and go to the folder where you want to store the code for your blog or static website
3. Run these commands to create a Hugo site with the LoveIt theme

    Create the [directory structure][hugo_dir_structure] for your project in the quickstart directory.

    ```sh
    hugo new site quickstart
    ```

    Change the current directory to the root of your project.

    ```sh
    cd quickstart
    ```

    Initialize an empty Git repository in the current directory.

    ```sh
    git init
    ```

    Go to [hugo themes][hugo_themes] and clone a theme of your choice in the themes fodler. I cloned the [LoveIt][loveit] theme into the themes directory, adding it to your project as a Git submodule.

    ```sh
    git clone --recurse-submodule git@github.com:horia-delicoti/LoveIt.git themese/LoveIt
    ```

    Append a line to the site configuration file, indicating the current theme.

    ```sh
    echo "theme = 'LoveIt'" >> config.toml
    ```

    Start Hugo’s development server to view the site.

    ```sh
    hugo server
    ```

    Press Ctrl + C to stop Hugo’s development server.

    Go to [http://localhost:1313][localhost]

4. To create a new blog entry, run hugo command. It will create a file in `content/post/` folder

    ```sh
    hugo new post/<blog-file-name>.md
    ```

5. Open the newly created file in the text editor of your choice and start drafting the blog
6. Once you are done drafting the content, delete the contents of public folder and run hugo command to regenerate the files
7. Create a repo on Github and check in the content of the public folder
8. To publish on `GitHub Pages`, follow [here][host_on_github]. If you want to use a custom domain, please follow [this][custom_domain].

## References

* [Hugo][hugo]
* [VS Code][vscode]
* [Using a custom domain with github pages][custom_domain]

[hugo_getting_started]: https://gohugo.io/getting-started/
[hugo_installation]: https://gohugo.io/installation/
[hugo_dir_structure]: https://gohugo.io/getting-started/directory-structure/
[hugo_themes]: http://themes.gohugo.io/
[loveit]: https://github.com/dillonzq/LoveIt
[localhost]: http://localhost:1313
[hugo]: https://gohugo.io
[vscode]: https://code.visualstudio.com/
[custom_domain]: https://help.github.com/articles/using-a-custom-domain-with-github-pages
[host_on_github]: https://gohugo.io/hosting-and-deployment/hosting-on-github/