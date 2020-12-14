### What is "Git conflict markers"?
{: id="20201210002930-7cvn3j6"}

The conflicting place looks like this in the document text (you can open the document through an external text editor to view):

```plaintext
<<<<<<< HEAD
Here is the original local content
=======
Here is the content pulled from the cloud
>>>>>>> feebfeb6bef44cf1384d51cdd7aef7e4197b8180
```

You can edit it manually, or you can use the diff tool to edit it.

## Why can't I sync empty folders?

This is the Git design. At least one file is required under the folder (the file content can be empty) to be included in version management.

## How to sync to GitHub repository?
{: id="20201213120253-hhtskws"}

1. Create a repository on GitHub, and [Configure SSH](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/connecting-to-github-with-ssh)
2. Configure the remote repository via `git remote add github git@github.com:user/repo.git` under the notebook folder, where:
   * `github` is the name of the remote repository, do not use `origin`, because `origin` is the official remote repository name of SiYuan
   * `user/repo` please change to your own repository name
3. Pull from remote via `git pull github main --allow-unrelated-histories`
4. Push the remote *master* branch through `git push github master`. Please note that the default branch name of the repository created by GitHub from October 2020 is *main*. After using this command, a `master` branch will be created on the remote repository. The default branch can be set to *master* in the repository Settings - Branches

## How to sync to Gitee repository?
{: id="20201213120253-ulbi3zh"}

1. Create a repository on Gitee and [Configure SSH](https://gitee.com/help/articles/4191)
2. Configure the remote repository via `git remote add gitee git@gitee.com:user/repo.git` under the notebook folder, where:
   * `gitee` is the name of the remoterepository, please do not use `origin`, because `origin` is the official remote repository name of SiYuan
   * `user/repo` please change to your own repository name
3. Pull from remote via `git pull gitee master --allow-unrelated-histories`
4. Push remote *master* branch through `git push gitee master`


{: id="20201210002859-thjj328" type="doc"}