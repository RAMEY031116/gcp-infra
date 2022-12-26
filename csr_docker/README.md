###cloud source repository refers to the build image pushed by either could build or dockerfile
#the image is stored in storage but is only referred by a tag in the CSR

export PROJECT_ID=$(gcloud config list --format 'value(core.project)')


#you need to download and install docker in order to do this 
#if windows user is not added to the docker-users, docker is not able to authenticate
net localgroup docker-users "user" /add

#also you can check the docker-users list using, if the user exists skip this.
net localgroup docker-users

#after adding the user, make sure docker is authenticated with gcloud
gcloud auth configure-docker

#to build a dockerimage with a new version "v1.1" (assuming same name exists in csr) from the local repo use below
#make sure docker is open while exxecuting this command
docker build -t gcr.io/$PROJECT_ID/build-run-image:v1.1 .

#push docker from local to csr
docker push gcr.io/udos-372521/build-run-image:v1.1

