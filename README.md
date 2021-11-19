# Sample academic group site

This site uses the Huge Academic Group theme, found at https://github.com/biaslab/hugo-academic-group. 

# Setup:

1. Install Hugo

2. Install the theme as per the instructions [here](https://github.com/biaslab/hugo-academic-group), e.g.

```
hugo new site website_name
cd website_name
git clone git@github.com:biaslab/hugo-academic-group.git themes/hugo-academic-group
cp -av themes/hugo-academic-group/exampleSite/* .
hugo server --watch
```

3. Configure a [Github Action](https://gohugo.io/hosting-and-deployment/hosting-on-github/#build-hugo-with-github-action) to build the site into the `gh-pages` branch.

4. Push the site and make sure the Action builds.

4. Configure repo Settings to use the `gh-pages` branch for the site (this won't show up until the action has run at least once and created the branch).

![image](https://user-images.githubusercontent.com/233584/142683521-bf26fb1f-0209-4163-b91c-7ffcb45bde68.png)
