# Mediawiki
Helm chart for mediawiki to deploy on kubernetes

# Pre-requisites 

1.) Docker and Kubernetes cluster on cloud or Raspberry pi. You can also run a minikube or docker for windows desktop . \
2.) Helm \
3.) kubectl

versions installed on my machine . \
kubernetes v1.19.3 \
helm v3.5.2

# How to run 

The repo conatines two charts . mediawiki-chart runs mediawiki app and mediawiki-mariadb-chart run databse for mediawiki app.

To run hop over to the chart and execute below command

helm install <chart name>
 
example > helm install mediawiki ./mediawiki-chart and helm install mediawiki ./mediawiki--mariadb-chart
 
The application will be served on the external ip provided by below load balancer . In my case it was > http://localhost:8080
Set the db root password, username and db name from values file placed inside mediawiki-mariadb-chart . Uuse the same to configure mediawiki db details page .

At the end of configuartion , LocalSettings.php will be downloaded . The same file need to be placed at /var/www/html inside conatiner . This can be done by removing commented hostmount in deployment.yaml of mediawiki-chart and providing a hostmount path.
