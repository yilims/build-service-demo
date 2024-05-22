# Prepare
Clone this repo to local, update environment variables below in build.sh
- ACR_LOGIN_SERVER
- ACR_USER
- ACR_PASSWORD
# Build image in local
run ./build.sh to build image
# Rebase image
- update stack image version in rebase.yaml. Two stack version are support: 0.1.106 and 0.1.115
- run ./rebase.sh to rebase image

