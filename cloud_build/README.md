###cloud build requires
app.py
Dockerfile
cloudbuild.yaml

#service used to create builds from the above files. 

gcloud services enable run.googleapis.com

#exporting project id to PROJECT_ID param
export PROJECT_ID=$(gcloud config list --format 'value(core.project)')

#submitting a cloud build with the tag gcr.io/$PROJECT_ID/build-run-image using a Dockerfile
gcloud builds submit --tag gcr.io/$PROJECT_ID/build-run-image

#creates a new build based on cloudbuild yaml file instead of dockerfile
gcloud builds submit --config cloudbuild.yaml