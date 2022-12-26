###cloud source repository refers to the build image pushed by either could build or dockerfile
#the image is stored in storage but is only referred by a tag in the CSR

export PROJECT_ID=$(gcloud config list --format 'value(core.project)')

#to build a dockerimage witha new version "v1.1" from the local repo use below
docker build -t gcr.io/$PROJECT_ID/build-run-image:v1.1 .

#if pushing from local use this to authenticate docker to push to csr
net localgroup docker-users "user" /add
gcloud auth configure-docker


#push docker from local to csr
docker push gcr.io/udos-372521/build-run-image:v1.1

