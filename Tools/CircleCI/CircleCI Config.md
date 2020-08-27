# [CircleCI Config](https://circleci.com/docs/2.0/configuration-reference/)

[TOC]

---

## [version](https://circleci.com/docs/2.0/configuration-reference/#version)

> Circleci Version

- **Required**
- param
    - 2
    - 2.0
    - 2.1

---

## [orbs](https://circleci.com/docs/2.0/configuration-reference/#orbs-requires-version-21)

- Requires version : 2.1

---

## [command](https://circleci.com/docs/2.0/configuration-reference/#commands-requires-version-21)

- Requires version : 2.1

---

## [parameters](https://circleci.com/docs/2.0/configuration-reference/#parameters-requires-version-21)

- Requires version : 2.1

---

## [executors](https://circleci.com/docs/2.0/configuration-reference/#executors-requires-version-21)

- Requires version : 2.1

---

## [jobs](https://circleci.com/docs/2.0/configuration-reference/#jobs)

### [<job_name>](https://circleci.com/docs/2.0/configuration-reference/#job_name)

#### [\<executor\>](https://circleci.com/docs/2.0/configuration-reference/#docker--machine--macos--windows-executor)

> environmnet setting

- **One executor type should be specified per job**
- executor List
    - docker
    - machine
    - macos
    - windows
- param
    - image
        - **Required**
        - Avaliable Docker Image List : [URL](https://circleci.com/docs/2.0/circleci-images/)
    - name
    - entrypoint
    - command
    - user
    - environmnet
    - auth
    - aws_auth
- ex

```yaml
docker:
	- image: circleci/<language>:<version Tag>
```

#### [steps](https://circleci.com/docs/2.0/configuration-reference/#steps)

> step of job

- **Required**
- \<step_type\>
    - [run](https://circleci.com/docs/2.0/configuration-reference/#run)
    - [checkout](https://circleci.com/docs/2.0/configuration-reference/#checkout)
    - [setup_remote_docker](https://circleci.com/docs/2.0/configuration-reference/#setup_remote_docker)
    - [save_cache](https://circleci.com/docs/2.0/configuration-reference/#save_cache)
    - [restore_cache](https://circleci.com/docs/2.0/configuration-reference/#restore_cache)
    - [store_artifacts](https://circleci.com/docs/2.0/configuration-reference/#store_artifacts)
    - [store_test_result](https://circleci.com/docs/2.0/configuration-reference/#store_test_results)
    - [persist_to_workspace](https://circleci.com/docs/2.0/configuration-reference/#persist_to_workspace)
    - [attach_workspace](https://circleci.com/docs/2.0/configuration-reference/#attach_workspace)

---

## [workflows](https://circleci.com/docs/2.0/configuration-reference/#workflows)

### \<workflow_name\>

#### triggers

- param
    - schedule
        - param
            - cron
            - filters
                - branches

#### jobs

##### \<job_name\>

- param
    - requires
    - context
    - type
    - filters
        - branches



---

- example

    ```yaml
    version: 2.1
    
    jobs:
    	chechout-code:
    		working-directory: ~/repo
    		docker:
            	- image: circleci/node:latest
             steps:
             	- 
    ```

    

    