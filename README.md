# Moodle Environment Cookiecutter

A very opinionated template for the excellent Python CLI
tool Cookiecutter. Quickly generate boilerplate for Docker
Compose environments ready to run [Moodle]() or Totara Learn
intended for **local development only**.

As I work on Unixy environments (OSX / Ubuntu) at this time
the tool is not Windows compatible due to the use of `make`
for automating tasks.

## Requirements
- [Make](https://www.gnu.org/software/make/)
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

Change into the created directory and clone your Moodle or Totara
into a directory called `html` theninitialise the environment.
You only need to do this once:

```
$ cd project-dir
$ git clone https://github.com/moodle/moodle.git html
$ make init
```

The `init` task will ask for the `sudo` password to change the
permissions on the local direcories. You can see exactly which
commands are run in the Makefile if you'd like to check.

After that you can start the Docker containers and install the database:

```
$ docker-compose up -d
$ make install-db
```

Your environment should now be accessible on port 80 on your localhost.

[GPLv3+](https://www.gnu.org/licenses/gpl-3.0.txt) licensed. Copyright Joby Harding 2018.



