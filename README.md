# Sample academic group site

This site uses the Huge Academic Group theme, found at https://github.com/biaslab/hugo-academic-group.

# Setup:

1. Install Hugo and set up a new site: https://gohugo.io/getting-started/quick-start/

2. Install the theme as per the instructions [here](https://github.com/biaslab/hugo-academic-group), e.g.
```
hugo new site website_name
cd website_name
git clone git@github.com:biaslab/hugo-academic-group.git themes/hugo-academic-group
cp -av themes/hugo-academic-group/exampleSite/* .
hugo server --watch
```
Make sure that the `config.toml` has the correct `baseurl`, e.g.
```
baseurl = "https://richardsc.github.io/"
```

3. Configure a [Github Action](https://gohugo.io/hosting-and-deployment/hosting-on-github/#build-hugo-with-github-action) to build the site into the `gh-pages` branch.

4. Push the site and make sure the Action builds.

5. Configure repo Settings to use the `gh-pages` branch for the site (this won't show up until the action has run at least once and created the branch).

![image](https://user-images.githubusercontent.com/233584/143870276-d18e2c29-e203-4a87-9d1d-0c210b6dbfde.png)

# Editing Content

There are two ways to add/edit content on the site.

## 1. The Quick method:

Assuming you have write access to the website repo, the quickest way to edit is to clone the repo to your machine, with e.g.:

```
git clone https://github.com/DalOceanDynamicsGroup/daloceandynamicsgroup.github.io.git
```

Then, edit what you want to. When you are finished, you need to: `add` your changes to the git history, `commit` the changes, and then `push` the new commits up to the main repository. You would do that something like:

```
# make some file changes/additions/deletions
git add . 
git commit -am "made some changes" # (the -a says commit changes to all tracked files and the -m is the quick way of doing the commit message)
git push
```

This is not ideal if there are a lot of people trying to edit the same files, as it can quickly result in "merge conflicts" (basically, when git can't decide what it can merge and what it needs someone to take a look at).

## 2. The Forking method:

The alternative is to make your own personal copy of the main repository (called a "fork"). You then clone your fork, make edits, add changes, commit changes, and then push back up to your fork on Github.

In order to get your changes included in the original repository you use the Github website to create a "Pull Request". This is a mechanism that allows one of the repo admins to review your changes before merging them back in to the original (or "upstream") repository.

You make a pull request (or PR) by going to the Github page for your fork, e.g. https://github.com/YOUR-USER-NAME/daloceandynamicsgroup.github.io, going to the "Pull Requests" tab:

IMG

and then clicking on the "New Pull Request" button:

IMG

Once your commits have been reviewed, they will be merged by a repo admin and included in the main repository.

### Keeping your fork up to date with the "upstream" repo

Because your fork only matched the original repository at the time you forked it, if you want to keep using it to create/edit content you're going to need to keep it up to date as the main repository is updated by other users (through either direct commits or PRs). This is referred to as *Fetching  upstream changes*. There are two ways to do this.

1. Use the "Fetch upstream" buttom on the Github page for your fork. Easy.

IMG

2. Update your fork to recognize the original repo as the "upstream" one, which will allow you to fetch (and merge) changes directly at the command line of your own fork. For more details, see [here](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork#syncing-a-fork-from-the-command-line), but it essentially amounts to the following steps.

  - List the current configured remote repo for your fork:
  ```
  $ git remote -v
  > origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
  > origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
  ```
  
  - Specify a new remote upstream repository that will be synced with the fork.
  ```
  $ git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git
  ```

  - Verify the new upstream repository you've specified for your fork.
  ```
  $ git remote -v
  > origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
  > origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
  > upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (fetch)
  > upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (push)
  ```

Once you've configured the remote "upstream" repo (only have to do this once), you can fetch any new commits from it, and merge them into your own repo. The instructions here apply to merging with the `main` branch, but you can merge into any branch you want (see e.g. https://www.clarkrichards.org/2021/11/28/forking-and-syncing-branches-with-git-and-github/). To do this:

  - Fetch the branches and their respective commits from the upstream repository. Commits to BRANCHNAME will be stored in the local branch upstream/BRANCHNAME.
  ```
  $ git fetch upstream
  remote: Counting objects: 75, done.
  remote: Compressing objects: 100% (53/53), done.
  remote: Total 62 (delta 27), reused 44 (delta 9)
  Unpacking objects: 100% (62/62), done.
  From https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY
   * [new branch]      main     -> upstream/main
  ```

  - Check out your fork's local default branch - in this case, we use main.
  ```
  $ git checkout main
  > Switched to branch 'main'
  ```
  
  - Merge the changes from the upstream default branch - in this case, upstream/main - into your local default branch. This brings your fork's default branch into sync with the upstream repository, without losing your local changes.
  ```
  $ git merge upstream/main
  Updating a422352..5fdff0f
  Fast-forward
   README                    |    9 -------
   README.md                 |    7 ++++++
   2 files changed, 7 insertions(+), 9 deletions(-)
   delete mode 100644 README
   create mode 100644 README.md
  ```
  If your local branch didn't have any unique commits, Git will instead perform a "fast-forward":
  ```
  $ git merge upstream/main
  > Updating 34e91da..16c56ad
  > Fast-forward
  >  README.md                 |    5 +++--
  >  1 file changed, 3 insertions(+), 2 deletions(-)
  ```
  
Note that syncing your fork only updates your local copy of the repository. To update your fork on GitHub.com, you must [push your changes](https://docs.github.com/en/github/getting-started-with-github/pushing-commits-to-a-remote-repository).
