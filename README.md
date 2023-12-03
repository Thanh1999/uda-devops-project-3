# Woking with deployment
1. User need to install awscli, kubectl, git to work with project
2. Configured the aws using "aws configured" to set the secret key id and access key to have the correct credential when using kubectl
3. Then run "aws eks update-kubeconfig --name udaci" - udaci is the cluster of the project
4. Under the deployments folder when you make change to these files run "kubectl apply -f <FILE_NAME>" to update the new changes to eks resource (deployment, service, env). Eg: kubectl apply -f api-deployment.yml - Update deployment resource will replace the existed pod with a new one
5. To connect to the application you can use port fowarding: "kubectl port-forward svc/api-app <LOCAL_PORT>:8080". For example if I use 8888 as my LOCAL_PORT, the application will be available in http://127.0.0.1:8888/ url. From there we can access api endpoint - Eg: http://127.0.0.1:8888/api/reports/user_visits
6. Everytime we make new change and push to github new build will be trigged to run in AWSCodebuild, new image will be created in ECR
