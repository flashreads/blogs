---
id: 002-remove-github-pages.md
title: How to unpublish GitHub pages site
tags: git, github, github-pages
author: Zoran Pandovski
meta-description: The missing step for unpublishing the Github pages site
---

You don't want your Github Pages site to be available or you are migrating to the new repository so you need to unpublish the site. The first thing that all of us will do is to:
1. Go to repository settings
2. Under GitHub Pages select the None(Disable GitHub Pages) option from the dropdown.

That is the correct way but, there is one additional step that you need to do to successfully unpublish the site.

## Delete gh-pages branch

For most of the GitHub pages sites, the gh-pages branch is the default branch for publishing source. Make sure that this branch is deleted from the repository:

```git
git push origin -d gh-pages
#git version older then 1.7
git push origin :gh-pages
```

If the response is `fatal: 'gh-pages' does not appear to be a git repository`, make sure that you have the branch locally before deleting it:

```git
git pull origin gh-pages
```
and then delete it.

>Note: If you are using a custom domain for the GitHub Pages site, make sure to update your DNS settings.

That's all. You have successfully unpublish the GitHub Pages site.