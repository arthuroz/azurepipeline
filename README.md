# Azure Pipeline as code
This is a practical sample of "pipeline as code" for [Azure DevOps](https://azure.microsoft.com/en-au/services/devops/)

## What does this project do
This project provides a [Postman](https://www.getpostman.com/) collection that implements a typical 
pipeline in [Azure DevOps](https://azure.microsoft.com/en-au/services/devops/)

It consists of below requests:
* Configures variables to be used in either URI or [JSON](https://www.json.org/) payloads
* Creates a repo
* Initialises master branch
* Makes sure nobody can push to master directly and pull requests must be reviewed before merge
* Makes sure comments are resolved before merge into master branch
* Creates dev branch
* Creates build pipeline, which runs a [Maven](https://maven.apache.org/) build then publishes 
  a [Docker](https://www.docker.com/) image to 
  [Azure Container Registry](https://azure.microsoft.com/en-au/services/container-registry/)
* Creates a typical release pipeline that deploys a [Spring Boot](https://spring.io/projects/spring-boot) 
  based micro service to dev, test and staging environments in 
  [Azure ASE](https://docs.microsoft.com/en-us/azure/app-service/environment/intro) 

This Postman collection also includes a few delete requests that can clean up test repo 
  and pipelines to help tailor the sample pipeline to your own needs

## Tools
* [Postman](https://www.getpostman.com/)
* [REST APIs for Azure DevOps](https://docs.microsoft.com/en-us/rest/api/azure/devops/?view=azure-devops-rest-5.1)

## Instructions
* Clone the repository
* Get Postman
* Import azurepipeline.json into [Postman](https://www.getpostman.com/)
* Configure variables as needed in "Pre-request Script" of the first request
* Runs the requests as needed in order
* Experiments with the collection and use provided DELETE requests to clean up test pipelines 
    or repository when needed
    
## Tips
* "Pre-request Script" of the first request is used to configure global variables
* "Tests" of a few requests are used to capture values from returned JSON payload for later usage
* [Azure DevOps](https://azure.microsoft.com/en-au/services/devops/) uses
  [basic auth](https://en.wikipedia.org/wiki/Basic_access_authentication). User name is your Azure 
  account email address and password is your 
  [PAT token](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops).
  If you are to handcraft the auth string, please be kindly reminded that a ":" is needed between
  username and password before the composed string is encoded
* The easiest way to obtain needed variables is to export existing repositories or pipelines 
  from your project as JSON files and then search for those values in exported files
