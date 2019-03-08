## hugo 搭建个人网站 for mac

### [本地搭建](https://gohugo.io/getting-started/quick-start/)
1. 安装hugo
    `brew install hugo`
2. 创建网站
    `hugo new site myblog`
3. 给网站添加一个主题
    ```
    cd myblog
    git init
    git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
    echo 'theme = "ananke"' >> config.toml
    ```
4. 添加一些内容
    `hugo new posts/my-first-post.md`
5. 启动hugo server
    `hugo server -D`
    启动成功后在[http://localhost:1313/](http://localhost:1313/)就可以看到自己的网站了  


### [部署到github上](https://gohugo.io/hosting-and-deployment/hosting-on-github/)    
1. Create a `<YOUR-PROJECT>` (e.g. `blog`) repository on GitHub. This repository will contain Hugo’s content and other source files.
2. Create a `<USERNAME>.github.io` GitHub repository. This is the repository that will contain the fully rendered version of your Hugo website.
3. `git clone <YOUR-PROJECT-URL> && cd <YOUR-PROJECT>`
4. Make your website work locally (`hugo server` or `hugo server -t <YOURTHEME>`) and open your browser to http://localhost:1313.
5. Once you are happy with the results:
    * Press Ctrl+C to kill the server
    * rm -rf public to completely remove the public directory
    * push your site to `<YOUR-PROJECT>` repository
       ```
       git add .
       git commit -m "some msg"
       git push origin master
       ```
6. `git submodule add -b master git@github.com:<USERNAME>/<USERNAME>.github.io.git public`. This creates a git submodule. Now when you run the `hugo` command to build your site to `public`, the created `public` directory will have a different remote origin (i.e. hosted GitHub repository). You can automate some of these steps with the following script.
7. submit the change
    ```
    git add .
    git commit -m "some msg"
    git push origin master
    ```
    That’s it! Your personal page should be up and running at `https://<USERNAME>.github.io` within a couple minutes.
