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
baseurl = "https://richardsc.github.io/academic"
```

3. Configure a [Github Action](https://gohugo.io/hosting-and-deployment/hosting-on-github/#build-hugo-with-github-action) to build the site into the `gh-pages` branch.

4. Push the site and make sure the Action builds.

4. Configure repo Settings to use the `gh-pages` branch for the site (this won't show up until the action has run at least once and created the branch).

![image](https://user-images.githubusercontent.com/233584/142684554-28d6122c-156e-4526-be7b-41d3904931d9.png)
