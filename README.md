# Moodle Environment Cookiecutter

A very opinionated template for the excellent Python CLI
tool Cookiecutter. Quickly generate boilerplate for Docker
Compose environments ready to run [Moodle]() or Totara Learn
intended for **local development only**.

## Requirements
- [Cookiecutter](https://github.com/audreyr/cookiecutter)

## Usage

The very first time you'll need to give Cookiecutter the
Git URL:

```
$ cd /path/to/where/you/want/the/environment
$ cookiecutter git@github.com:jobyh/cookiecutter-moodle-env.git
```
You'll then be prompted for the project name (used to name the
directory in which the environment will be created).

After that you can just use the cutter name instead:

```
$ cookiecutter cookiecutter-moodle-env
```

GPLv3+ licensed. Copyright Joby Harding 2018.



