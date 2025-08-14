# Flask-CI-CD-Demo
A simple Flask app demo with a full CI/CD pipeline using Docker, Kubernetes, Argo CD, and GitHub Actions. Automates building, pushing images, and deploying to Kubernetes via GitOps. Perfect for learning modern cloud-native app delivery with automated sync and rollout.


Setup

Clone the repo:

git clone https://github.com/<YOUR_GITHUB_USERNAME>/flask-argo-demo.git
cd flask-argo-demo


Update the Docker image name in k8s/deployment.yaml with your DockerHub username.

Push changes to GitHub.

Configure Argo CD to track the k8s folder in your repo by applying the Application manifest:

kubectl apply -f argocd/app.yaml -n argocd


Login to Argo CD and sync the app:

argocd login <ARGOCD_SERVER> --username admin --password <password>
argocd app sync flask-app

Usage

On each push to the main branch, GitHub Actions will:

Build and push the Docker image

Update the Kubernetes deployment manifest

Push the updated manifest back to GitHub

Trigger Argo CD to sync the app and deploy the new version

Access your Flask app via the LoadBalancer IP or port-forward the service.
