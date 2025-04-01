Deploying a Docker Image to Google Artifact Registry

Step 1: Enable Artifact Registry on GCP with 
  gcloud services enable artifactregistry.googleapis.com

Step 2: Install Google Cloud CLI and authenticate Google Account

Step 3: Create a Docker Repository in Artifact Registry
  gcloud artifacts repositories create my-docker-repo
      --repository-format=docker
      --location=australia-southeast1
      --description="My Docker repository"

  or in the Artifact Registry Console

Step 4: Authenticate Docker with Artifact Registry
  gcloud auth configure-docker australia-southeast1-docker.pkg.dev

Step 5: Tag the Docker Image
  docker tag 52d-web australia-southeast1-docker.pkg.dev/sit323-25t1-oris-3932a7f/my-docker-repo/52d-web:latest

Step 6: Push the image to Artifact Registry
  docker push australia-southeast1-docker.pkg.dev/sit323-25t1-oris-3932a7f/my-docker-repo/52d-web:latest

Step 7: Ensure repository is in the Artifact Registry
  gcloud artifacts repositories list --location=australia-southeast1

  Or check the Artifact Registry console

Step 8: Run the Container
  docker run -d -p 5000:5000 --name 52d-web-container australia-southeast1-docker.pkg.dev/sit323-25t1-oris-3932a7f/my-docker-repo/52d-web:latest
 



