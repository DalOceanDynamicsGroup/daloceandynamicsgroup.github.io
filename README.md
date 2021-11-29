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

6. Quick start adding content (not ideal... see next step for better way)

git clone https://github.com/DalOceanDynamicsGroup/daloceandynamicsgroup.github.io.git

Then edit what you want to.

Then 
```
git add
git commit
git push.
```

7. Making a fork and updating the main website (this is how we ought to maintain the website)

Make your own fork of the repository. Clone that to your computer and edit files as you wish. 
git add; git commit and git push them back to your fork of the repository. 

Once you have done this and are happy with your changes, you need to set up a pull request to the main site to see them appear. To do this, you need to  
```
git fetch upstream 
```
(this is similar to git pull as it tries to update your fork with respect to the main repo, but it does not try to merge the changes), then create a pull request. This will be reviewed by Clark or Ruth and then your changes will be merged with the main website.




