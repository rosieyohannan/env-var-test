# Test env var order of precedence

I've made branches showing the various ways to set an environment variable, and which take precedence over each other. I've use the env var CIRCLE_JOB.

You can see that the env var is set in a context and in project settings too:

![env var set in project settings](projectsettings.png)
![env var set in context](context.png)

1. Set env var in shell command overrides everything, as follows:

    * Environment variables declared with the `environment` key for a `run` step
    * Environment variables set with the `environment` key for a job
    * Built-in Environment Variables
    * Context environment variables 
    * Project-level environment variables
    * Environment variables set with the `environment` key for a container

    See https://app.circleci.com/jobs/github/rosieyohannan/env-var-test/96

    On master branch

2. Set env var using `environment` key in a step overrides:
   
    * Environment variables set with the `environment` key for a job
    * Built-in Environment Variables
    * Context environment variables 
    * Project-level environment variables
    * Environment variables set with the `environment` key for a container

    See: https://app.circleci.com/pipelines/github/rosieyohannan/env-var-test/54/workflows/0272418a-a5d0-4ab6-be9a-00fa2c772a07/jobs/98

    On branch: https://github.com/rosieyohannan/env-var-test/blob/env-key-run-step/.circleci/config.yml
    
3. Se env var using `environment` key at job level overrides:

    * Built-in Environment Variables
    * Context environment variables 
    * Project-level environment variables
    * Environment variables set with the `environment` key for a container

    see: https://app.circleci.com/pipelines/github/rosieyohannan/env-var-test/57/workflows/2993776c-0275-48d7-bea6-dd276c86a28b/jobs/101
    
    on branch: https://github.com/rosieyohannan/env-var-test/blob/job-env-key/.circleci/config.yml
