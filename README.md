# Bitbucket Pipelines Runner
`bbrun` is a small command line tool to execute [Bitbucket Pipelines](https://confluence.atlassian.com/bitbucket/configure-bitbucket-pipelines-yml-792298910.html) locally.

[![Build Status](https://travis-ci.org/mserranom/bbrun.svg?branch=master)](https://travis-ci.org/mserranom/bbrun)


## Install

Install `bbrun` using `npm`:

```bash
$ npm install -g bbrun
```

## Usage

With `bbrun` you can execute any step defined in your `bitbucket-pipelines.yml` template:

```yaml
pipelines:
  default:
    - step:
          name: hello
          image: ubuntu2
          script:
            - echo "hello world!"
```

Run `bbrun` straight from your project path:

```bash
$ bbrun hello
running "build" in "atlassian/default-image" image...
hello world!
```

### Options

```
  Usage
    $ bbrun <step> <options>

  Options
       --template, pipeline template, defaults to "bitbucket-pipelines.yml"
       --env,  define environment variables for execution
       --save-env, saves an environment variable in env-file
       --env-file, file storing environment variables, defaults to "~/.bbrun"
       --dry-run,  performs dry run, printing the docker command
       --interactive, starts an interactive /bin/bash session in the container
       --help, prints this very guide

     Examples:
       Execute all steps defined in ./bitbucket-pipelines.yml
         $ bbrun
         $ bbrun --template bitbucket-template.yml
       Execute a single step by name
         $ bbrun test
         $ bbrun test "Build and test"
       Execute a step using an environment variable
         $ bbrun test --env EDITOR=vim
         $ bbrun test --env EDITOR=vim,FOO=bar
       Define a global environment variable and save it in ~/.bbrun
         $ bbrun --save-env EDITOR=vim
```

## Build and Test

```bash
npm install && npm test
```

### Install locally

```bash
$ npm install && npm link
```