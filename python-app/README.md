# jenkins-argocd

I made a project where i am using CICD pipeline to make a change in one of my python application running in kubernetes.

Here, I am using the following technologies:-

1. Github - To store all the required artifacts. For jenkins I am using this repository https://github.com/EkanshJain98/jenkins/tree/main/python-app and for ArgoCD I am using this repository https://github.com/EkanshJain98/argocd
2. Kubernetes - where I am running very basic python (Flask) application
3. Jenkins - I have deployed this on EC2 server for achieving continous integration.
4. ArgoCD - Deployed this on kubernetes for achieving continous delivery.

Let's take a look into the quick overview of the CI-CD pipline for this project.

Following image you can see of jenkins pipeline, which will pick the changes automatically from the source github repository as soon as there is a push event and then it push the changes to the target repository where k8s artifacts are stored.

<img width="1900" height="836" alt="image" src="https://github.com/user-attachments/assets/b20470d7-819a-47a8-99a8-ec1bf2e6f9ee" />

Following image you can see of the ArgoCD and it is a very much compatible with the kubernetes. ArgoCD will automatically pick the changes from it's source repository and accordingly update the artifacts stored in the kubernetes.

<img width="1912" height="892" alt="image" src="https://github.com/user-attachments/assets/6d90085e-f062-4885-8224-38ca207a1466" />

Below is the very simple python (Flask) based application which is deployed on kubernetes using deployment and service objects.

<img width="1918" height="452" alt="image" src="https://github.com/user-attachments/assets/147c966c-3066-4f48-a2a3-2950517a8eb6" />

Now let me show you the complete process.

1. Let's make a change in the repository (python-app) so that jenkins can gets trigger to push the changs to the target respository (argocd) using github webhooks.

<img width="1575" height="454" alt="image" src="https://github.com/user-attachments/assets/e8784ea1-b66f-41ec-8129-f2ef80cf2dd5" />

2. Github webhook will trigger.

<img width="851" height="365" alt="image" src="https://github.com/user-attachments/assets/d9297295-6d20-4ba4-8d94-41001ad1feb6" />

3. Jenkins pipeline will trigger

<img width="1877" height="374" alt="image" src="https://github.com/user-attachments/assets/38e55214-68c8-4265-a4a7-18f08b0e89ee" />

4. Let's see the ArgoCD dashboard if it has synced the changes and updated the same in Kubernetes.

<img width="1675" height="887" alt="image" src="https://github.com/user-attachments/assets/6643fd22-01bd-4c11-be3e-1ff1f110bf62" />

5. Let's check the deployment's image where change is supposed to apply.

<img width="1066" height="467" alt="image" src="https://github.com/user-attachments/assets/0f8e103c-64e0-4932-9c15-58d6d6fbe416" />

Image is successfully updated inside kubernetes.

6. Now let's check the web server to see the updated changes which we did in step 1

<img width="703" height="342" alt="image" src="https://github.com/user-attachments/assets/4d38db65-ae8f-4afc-b6e1-1554b27ab7e7" />

This completes our CI-CD pipeline.
