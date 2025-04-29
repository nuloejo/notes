# Take Your Tests to the Cloud with Testkube

## What traditional testing looks like?

| CI/CD Pipeline |  Kubernetes  |
|:---------------|:------------:| 
| Junit          | -> Backend A |
| Pytest         | -> Backend B | 
| Playwright     | -> Backend C | 
| Gatling        |

## Why traditional testing breaks down?

* Fragmentation of testing tools
* Missing single pane of glass
* Running tests is tied to CI/CD
* Running tests only against exposed services
* Running tests at scale
* Version of tests detached from version of applications

## What is TESTKUBE ?

* Testkube is a test **orchestration** and **execution framework**
* Test **framework agnostic**, supports any type of tests
* Build for Kubernetes, **cloud native**, acts as an operator, uses CRDs
* Free, **OpenSource**, with commercial edition and enterprise features
* **Integrates** seamlessly **with CI/CD** tools and pipelines
* Compatible with **GitOps** workflows, enables declarative tests management
* Provides **centralized visibility**, execution reports, artifacts, and logs in one place
* Leverages Kubernetes for horizontal and vertical **scaling**
* **Enhances security**, by avoiding unnecessary services exposure

## How to define test ?

* TestWorkflows are core test abstraction
* Provides easy, flexible and powerful way to define test scenarios
* Orchestrated by testkube agent and executed inside the cluster
* Composable from multiple steps or child test workflows

### More real life example of definition

```yaml
apiVersion: testworkflows.testkube.io/v1
kind: TestWorkflow
metadata:
  name: frontend-tests
  namespace: testkube
spec:
  container:
  image: frontend-tests:1.23
resources:
  limits:
  срu: 1
  memory: 1Gi
env:
  - name: FRONTEND_URL
    value: https://acme.com
steps:
  - name: Run frontend tests
    shell: pm playwright test --output /data/reports
    retry:
      count: 3
    artifacts:
      paths:
        - /data/reports/**/*
```

* Uses standard configuration constructs
* Supports parameterization with env. variables, ConfigMaps, and Secrets
* Collects test artifacts and execution reports
* Automatically retries failed test steps

## How to run test ?

```shell
testkube run testworkflow simple-test --watch
# Test Workflow Execution:
# Name:
# Execution ID:
# Execution name:
# Status:
# simple-test
# 66d838e679bb7d4de696e8f0
# simple-test-1
# queued
# getting logs from test workflow 66d838e679bb...
# test completed successfully in 2.199s ö
testkube get testworkflowexecution simple-test-1
testkube download artifacts simple-test-1
```

* Manage and interact with test resources with testkube CLI
* Connect to the testkube API directly or via proxy
* Seamlessly integrates with CI/CD pipelines

### Run multiple tests using label selectors

* Run multiple tests using label selectors
* Run scheduled tests with Cron trigger
* Run tests as a step in a CI/CD pipeline
* Run tests as an ArgoCD post-synchronization hook
* Run tests in response to specific Kubernetes events

#### Example 1

```yaml
kind:
  TestWorkflow metadata:
name:
  frontend-tests labels:
type: smoke
```

#### Example 2

```yaml
kind:
  TestWorkflow metadata:
name: frontend-tests
spec:
events:
  - cronjob:
cron: "*/5 ****"
```

#### Example 3

```yaml
kind: TestTrigger
metadata:
  name: simple-trigger
spec:
  event: modified
  resource: configmap
  resourceSelector:
    name: myapp-config
  action: run
  execution: test
  testSelector:
    name: myapp-test
```