# gcp-ace-demo-labs
GCP Associate Cloud Engineer Certification labs - hands on

Cloud Run Demo: [Project Name]
A streamlined demonstration of deploying a containerized application to Google Cloud Run. This project showcases how to move from local development to a fully managed, auto-scaling serverless environment.

🚀 Features
Serverless: No infrastructure to manage.

Auto-scaling: Scales from zero to N based on traffic.

Containerized: Built using Docker for environment consistency.

HTTPS Enabled: Automatically provisioned TLS certificates.

🛠 Prerequisites
Before you begin, ensure you have the following installed and configured:

Google Cloud SDK (gcloud)

Docker Desktop

An active Google Cloud Project with billing enabled.

💻 Local Development
Clone the repository:

Bash

git clone <your-repo-url>
cd <project-directory>
Build the Docker image locally:

Bash

docker build -t cloud-run-demo .
Run the container:

Bash

docker run -p 8080:8080 cloud-run-demo
Access the app at http://localhost:8080

☁️ Deployment Steps
1. Enable Required APIs
Bash

gcloud services enable run.googleapis.com containerregistry.googleapis.com
2. Submit Image to Container Registry
Build and push your image directly to Google Cloud:

Bash

gcloud builds submit --tag gcr.io/[PROJECT_ID]/cloud-run-demo
3. Deploy to Cloud Run
Bash

gcloud run deploy cloud-run-demo \
  --image gcr.io/[PROJECT_ID]/cloud-run-demo \
  --platform managed \
  --region [YOUR_REGION] \
  --allow-unauthenticated
🧪 Testing the Endpoint
Once the deployment is complete, the CLI will provide a Service URL. You can test it using curl:

Bash

curl [YOUR_CLOUD_RUN_URL]
🧹 Cleanup
To avoid incurring charges, delete the Cloud Run service and the stored images:

Delete Service: gcloud run services delete cloud-run-demo

Delete Image: gcloud container images delete gcr.io/[PROJECT_ID]/cloud-run-demo
