# github-wiki-sidebar

[![NPM Version][npm-image]][npm-url]
[![NPM Downloads][downloads-image]][downloads-url]

Multi-level GitHub wiki sidebar menu generator (_Sidebar.md) from the filenames in the wiki repository 

## Features:

* generate markdown multi-level menu based on the pages titles
* enquire mode (init/tutorial) for customising job options
* automatically push changes to source repository
* allows you to order the items in the menu and save the order for later executions
* create a template - add logo / links / text etc around your generated menu

![github wiki sidebar generated by github-wiki-sidebar](https://raw.githubusercontent.com/wiki/adriantanasa/github-wiki-sidebar/images/github-wiki-sidebar-generator.png)

See examples of sidebar menu generated by this module at [github-wiki-sidebar's Wiki](https://github.com/adriantanasa/github-wiki-sidebar/wiki) and more in the *Examples* section (as [AngularJS](https://github.com/angular/angular.js/wiki), [ng-bootstrap](https://github.com/ng-bootstrap/ng-bootstrap/wiki), etc.)

## Installation

We recommend installing the module globally for ease of usage and not poluting your wiki repository with node_modules packages

```shell
npm install github-wiki-sidebar -g
```

## End-to-End Scenario

**First time**
* clone your local repository
* execute init job to customise the order of items  and the template of sidebar menu (ex: add a logo)

**Repeat**
* execute the job with the saved settings from above and automatic promotion to source repository

![Generate custom GitHub wiki sidebar with order and custom template](https://raw.githubusercontent.com/wiki/adriantanasa/github-wiki-sidebar/images/generating-github-wiki-sidebar-order-and-template.png)

## Usage

For ease of use install the module globally and if your npm bin path is in your $PATH variable just call the github-wiki-sidebar from within your local wiki folder (cloned):

```shell
# this will generate _Sidebar.md with default options
github-wiki-sidebar
```

Executing in tutorial mode (step by step) - allow user to generate sidebar with customised settings:

```shell
github-wiki-sidebar --action=tutorial
```

Executing in init mode (step by step) - allow user to generate an option.json file with customised settings that will be picked up on next execution.

```shell
github-wiki-sidebar --action=init
```

The "git-push" mode is also pushing the updated \_Sidebar.md file to your \<project\>.wiki repository given you have access to push.

```shell
github-wiki-sidebar --git-push
```

For more information on the syntax and available parameters run:

```shell
github-wiki-sidebar --help
```

Debug:

```shell
export DEBUG=github-wiki-sidebar;github-wiki-sidebar
```

## Options available in init/tutorial mode

**Customise the separator character(s) for multi-level menu: \:-**

Change the sequence to break titles into categories (default to ":-"). Users on Windows operating system have to chose a different separator for categories as colon is not accepted as a file separator.

**Customise the internal links format: ./%s**

You may prefer a full path route ex:  ```https://github.com/adriantanasa/github-wiki-sidebar/wiki/%s```

**Select the _Sidebar.md content template: %s**

You can add markdown content before/after menu content - use this to add for example a logo. The %s will be replaced with the content of the menu:

```
[![npm module\](https://rawgit.com/wiki/adriantanasa/gi
thub-wiki-sidebar/images/github-wiki-sidebar.svg)](https://www.npmjs.com/package/github-wiki-side
bar)\n\n%s
```

**Change the priority/order of the items in menu (ex: 3,4,0): n**

The list of local *.md files is displayed with indexes - here you can specify in a coma separated list the priority for them in the menu. By default the script is looking for the position of Home.md (if any) in your local folder and adding it with highest priority.


## Recipes

### Working directly with your GitHub wiki repository

```shell
git clone https://github.com/adriantanasa/github-wiki-sidebar.wiki.git
cd github-wiki-sidebar.wiki
github-wiki-sidebar
git add . && git commit -am "Create or Update the _Sidebar.md"
```

Updating from a local cloned GitHub wiki repository manually

```shell
cd github-wiki-sidebar.wiki
git fetch origin
git pull
github-wiki-sidebar
git add . && git commit -am "Update of the _Sidebar.md"
git push origin master
```

The --git-push modifier allows to execute the job above automatically.

```shell
cd github-wiki-sidebar.wiki
github-wiki-sidebar --git-push
```

### Changing the order of your menu items

Starting with version 1.1.0 there is builtin support for ordering pages as part of init/tutorial mode. See the End-to-End Scenario above.

### Add a logo to your menu

Execute the script in init mode and at the *Select the _Sidebar.md content template: %s* change the default template with one that will include the logo:

```markdown
![my Company Logo Alt text](https://somepublicdomain.com/path/to/my/image.png)\n\n%s
```

You can also add your image directly to wiki repository and reference it directly in your template.

## Contribution

Check [Roadmap](https://github.com/adriantanasa/github-wiki-sidebar/wiki/Roadmap) for planned items.

We are welcoming contributors - feel free to create issues and help imporve the tool. Also if you have a public wiki generated with this module please add it to README.md Examples section.

## Examples

GitHub wiki menus generated with this module:

* [AngularJS Wiki](https://github.com/angular/angular.js/wiki)
* [ng-bootstrap Wiki](https://github.com/ng-bootstrap/ng-bootstrap/wiki)
* [React.js Wiki](https://github.com/facebook/react/wiki)
* [ShellJS Wiki](https://github.com/shelljs/shelljs/wiki)


[npm-image]: https://img.shields.io/npm/v/github-wiki-sidebar.svg
[npm-url]: https://npmjs.org/package/github-wiki-sidebar
[downloads-image]: https://img.shields.io/npm/dm/github-wiki-sidebar.svg
[downloads-url]: https://npmjs.org/package/github-wiki-sidebar
