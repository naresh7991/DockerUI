## DockerUI
This is a sample project created for docker deployement learning.

## Deploying UI in docker
There are multiple way you can deploy and run this code

1. ## Using direct docker command
      First way to simply using docker command -
      
      docker run -p 3000:5173 -v "$PWD":/app -w /app node:22-alpine sh -c "npm ci && npm run dev -- --host
      ## lets explain each flag:
      1. -p: this flag assign the host port to container port. eg: -p hostPort:containerPort
      2. -v: this flag assign the host directory to container directory. eg. -v hostDirectory:containerDirectory  (note: $PWD is current directory for host)
      3. -w: this flag will set working directory for container. eg. -w containerDirectory
      4. sh -c:  this is combine as any thing after dockerImage is consider as command for docker container. So here i am running open sh and run command npm ci  and npm run dev -- --host. (mention --host might not required i added so it will enable the port)
      (Note: this react project requires node version > 20 image. So that why mentioning node:22-alpine)

## Added github action with self-hosted runner
      In this repo I also testing how we can use github action with self hosted runner to deploy in 
      in .github\workflows a main.yml file added, which contain github action
      
      In that I define github action with to run using self-hosted runner and run when any change happen in main branch
      (Note: Before running this you should setup your self-hosted runner, as when you create this file that also run this action, you can find how to setup github self-hosted runner under repository setting tab > actions >runner)
      (If you stop your self hosted runner in vm but github will not get any notification, So github actions still trigger but showing waiting for github action for some time and end up failing)

## Added build check github action with github runner
      Here I added build-check action with github runner to check and validate the build on pushing changes to main branch

