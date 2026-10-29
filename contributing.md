---
title: Contributing
nav_order: 7
---

# Contributing to CyberGridML

Thank you for taking the time to contribute. This page explains how to take part in the CyberGridML project, which rules apply, and how to submit your changes.

The following guidelines are mostly guidelines, sometimes rules. Use your best judgment, and feel free to propose changes to this page in a pull request.

## Table of contents

* [Code of Conduct](#code-of-conduct)
* [License and Developer Certificate of Origin](#license-and-developer-certificate-of-origin)
* [How Can I Contribute?](#how-can-i-contribute)
  * [Getting involved in the technical meetings](#getting-involved-in-the-technical-meetings)
  * [Promoting the project](#promoting-the-project)
  * [Reporting Bugs and Suggesting Enhancements](#reporting-bugs-and-suggesting-enhancements)
  * [Contributing Code](#contributing-code)
  * [Improving the documentation](#improving-the-documentation)
  * [Definition of Done](#definition-of-done)
* [Styleguides](#styleguides)
  * [Git Commit Messages](#git-commit-messages)
  * [English language convention](#english-language-convention)
* [Git workflow guidelines](#git-workflow-guidelines)

## Code of Conduct

Everyone who takes part in the CyberGridML project, whether in issues, pull requests, meetings or any other channel, is expected to be respectful and constructive. Harassment, discrimination and personal attacks are not acceptable. If you witness or experience unacceptable behavior, report it privately to the project maintainers through GitHub.

## License and Developer Certificate of Origin

### License

CyberGridML is licensed under the [Eclipse Public License 2.0](https://github.com/cybergridml/cybergridml.github.io/blob/main/LICENSE) (EPL-2.0). By submitting a contribution, you agree that it is licensed under the same license.

### Developer Certificate of Origin

The project requires the [Developer Certificate of Origin](https://developercertificate.org/) (DCO). By signing off a commit, you certify that you have the right to submit the contribution under the project's license.

Every commit must contain a `Signed-off-by` line, with your name and email address:

```text
Add the Quick Setup tutorial

Signed-off-by: Your Name <your.email@example.com>
```

Git adds this line for you when you use the `-s` option:

```bash
git commit -s -m "Add the Quick Setup tutorial"
```

Pull requests with commits that lack a valid sign-off must be amended before they can be merged.

## How Can I Contribute?

### Getting involved in the technical meetings

Technical discussions take place in the issues and pull requests of the project's repositories. Reading and commenting on open pull requests is a good way to understand the priorities of the project, give technical advice, and find where you can help.

### Promoting the project

You can help CyberGridML reach new users and contributors:

* use CyberGridML in your teaching, studies or research, and tell us about it;
* give talks or write articles about your experience with the project;
* share your feedback and ideas with the community.

### Reporting Bugs and Suggesting Enhancements

Bugs and enhancement suggestions are tracked as [GitHub issues](https://docs.github.com/en/issues):

* errors in this documentation go to the [documentation repository](https://github.com/cybergridml/cybergridml.github.io/issues);
* problems with the modeler itself go to the [CyberGridML editor repository](https://github.com/cybergridml/cybergridmodel/issues).

Before opening an issue, search the existing issues, both open and closed. If a matching issue is still open, add your information to it instead of opening a new one. If you find a matching issue that is closed, open a new issue and link to the closed one.

A good bug report includes the version of CyberGridML you use, the steps to reproduce the problem, what you expected, what happened, and any relevant logs or screenshots.

Do not report security vulnerabilities in a public issue. Contact the maintainers privately instead.

### Contributing Code

Code changes are submitted as [pull requests](https://docs.github.com/en/pull-requests). Crafting a good pull request takes time, and the maintainers will help as much as they can, but expect an iterative process. The goals of this process are to:

* maintain the software quality;
* fix the problems that matter most to users;
* engage the community in working toward the best possible features;
* keep the review workload sustainable for the maintainers.

For a substantial change, open an issue to discuss the approach before you start coding. Then follow the [Git workflow guidelines](#git-workflow-guidelines) below, keep your pull request focused on one change, and describe in the pull request what changed and why.

### Improving the documentation

This documentation is built with [Jekyll](https://jekyllrb.com/) and the [just-the-docs](https://just-the-docs.com/) theme. Each page is a Markdown file, organized in the four sections of the [Diátaxis](https://diataxis.fr/) framework:

* `tutorials/`: learning-oriented lessons;
* `how-to-guides/`: step-by-step instructions for a specific task;
* `explanation/`: background and design choices;
* `reference/`: precise technical descriptions.

Every page starts with a front matter block that sets its title, its parent section and its position in the navigation. Keep these fields when you edit a page, and check that every relative link and image path still resolves.

To preview the site locally, build it with the same Jekyll version that GitHub Pages uses, through Podman, and write the output outside the repository:

```bash
mkdir -p ../site-preview
podman run --rm -v "$PWD":/srv/jekyll:Z -v "$PWD/../site-preview":/out:Z -w /srv/jekyll docker.io/jekyll/jekyll:4 sh -c 'gem install jekyll-remote-theme jekyll-include-cache jekyll-relative-links -N && jekyll build --destination /out'
python3 -m http.server --directory ../site-preview 4000
```

Then open `http://localhost:4000` in your browser.

### Definition of Done

Before a change is considered done, check the following:

* the assumptions of the issue are met, and the change is described in the issue or the pull request;
* the required documentation is updated, including this page if the process changes;
* for documentation changes: the site builds, the new pages have their front matter, the images are included with relative paths, and the text follows the [English language convention](#english-language-convention);
* for code changes: the build succeeds, all tests pass, the code style checks report no violation, new behavior is covered by unit tests where applicable, and the security analysis reports no unaddressed issue;
* at least one maintainer has reviewed the pull request and approved it.

The Definition of Done is not a static list. If you think it should change, propose the change in a pull request.

## Styleguides

### Git Commit Messages

* Start the message with a short summary line of 50 characters or fewer, written in the imperative mood, for example `Add quick setup tutorial`.
* Leave a blank line, then explain what the change does and why in the body. Wrap the body at 72 characters.
* Link the related issues in the body or the footer, for example `Fixes #12`.
* Add the `Signed-off-by` line, as described in [Developer Certificate of Origin](#developer-certificate-of-origin).

```text
Add quick setup tutorial

Explain how to start a CyberGridML application instance with Podman,
using the cybergridapp-deployment quickstart. The tutorial also covers
the download of the application JAR, which the quickstart did not
describe.

Signed-off-by: Your Name <your.email@example.com>
```

### English language convention

All project documents, including code comments, documentation and this website, are written in American English. Use American spelling (for example *modeling*, *behavior*, *color*) and run a spell checker before you submit your change.

## Git workflow guidelines

1. **Fork the repository** on GitHub, then clone your fork and add the original repository as `upstream`:

   ```bash
   git clone https://github.com/<your-account>/cybergridml.github.io.git
   cd cybergridml.github.io
   git remote add upstream https://github.com/cybergridml/cybergridml.github.io.git
   ```

2. **Create one branch per change**, starting from an up-to-date `main`. Use a prefix that describes the kind of change, such as `feature/`, `fix/` or `docs/`:

   ```bash
   git fetch upstream
   git switch -c docs/add-contributing-page upstream/main
   ```

3. **Keep the history clean.** Make focused commits, and rebase your branch on `upstream/main` before you ask for a review or when the branch is out of date:

   ```bash
   git fetch upstream
   git rebase upstream/main
   ```

4. **Never commit directly to `main`.** Push your branch to your fork and open a pull request against `main` of the original repository.

5. **Update your branch after a review** by pushing new commits to the same branch. If you rewrite history, use `git push --force-with-lease`, and only on your own branches.

6. **Pull requests are squashed when merged**, so the title of the pull request becomes the commit message on `main`. Write it as you would write a commit summary.
