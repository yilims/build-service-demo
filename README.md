# Prepare
- clone this repo to local
- update environment variables below in build.sh
  - ACR_LOGIN_SERVER
  - ACR_USER
  - ACR_PASSWORD
# Build image in local
run ./build.sh to build image
# Rebase image
- update stack image version in rebase.yaml. Two stack version are support: 0.1.106 and 0.1.115
- run ./rebase.sh to rebase image
- Wait 1 min for the image to be rebased and check ACR repo in Azure Portal, new image sha256 should appear in ACR.
# Run Github pipeline to build and deploy Spring Petclinic App
- update file [messages.properties](https://github.com/yilims/spring-petclinic/blob/main/src/main/resources/messages/messages.properties#L1) and change message to "Welcome to Spring Petclinic", commit the change.
- Github pipeline [Build source code to container image and deploy to AKS](https://github.com/yilims/spring-petclinic/actions/workflows/build-deploy-image.yml) is triggered and it will:
  - build image and stream build log in console
  - deploy image to AKS
- visit Spring Petclinic URL, you will see the message is changed to to "Welcome to Spring Petclinic"
# Run Github pipeline to Rebase image
- update file [build-service.yaml](https://github.com/yilims/spring-petclinic/blob/main/deploy/build-service.yaml#L7-L10) and change build & run image version to "0.1.106", commit the change.
- Github pipeline [Rebase Image when Stack and Buildpack Version changes](https://github.com/yilims/spring-petclinic/actions/workflows/rebase-image.yml) is triggered and it will rebase image
- Wait 1 min for the image to be rebased and check ACR repo in Azure Portal, new image sha256 should appear in ACR.

