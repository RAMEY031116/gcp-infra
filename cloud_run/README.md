###cloud run hosts the an application with the latest tag provided from container registry

gcloud run deploy cloud-run-deploy --image gcr.io/$PROJECT_ID/build-run-image --platform managed --region us-central1 --allow-unauthenticated

