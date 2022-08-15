# OpenSearch-Log-Ingestion
The following configuration is defined for an architecture consists of a simplified multi-tier highly available application. The frontend application is deployed on OCI managed service Kubernetes cluster. The backend application is deployed on a customer managed Kubernetes cluster on-premises. Fleuntd and Fluentbit (defined below) are deployed as two different combinations but can also be deployed independently.
1.	End User accesses the front-end application deployed on the Kubernetes cluster in the cloud environment
2.	The request lands on the OCI Active load balancer and is processed by application pod
3.	To fulfill the request front end application pod fetches data from the backend Kubernetes cluster
4.	OCI - Fleuntbit is running as a DeamonSet to collect logs from all the pods and pushing to Fluentd
5.	OCI - Fluentd is running as a Deployment to aggerate logs received from Fluentbit
6.	Customer Premises - Fleuntd is running as a DeamonSet is collecting logs from all the pods and pushing to the OpenSearch endpoint
7.	The aggerated logs are ingested by Fluentd to the OCI OpenSearch endpoint
8.	In the event of an incident the application owner can login into OCI OpenSearch dashboard and search for error codes
9.	OCI OpenSearch fetches the matching search results in near real time 
10.	Application owner identifies potential incident and can take corrective action on specific node/pod/application
11.	A graphical representation is provided to the end user for building artifacts related to the incident using OCI OpenSearch Service Dashboard
12.	OCI OpenSearch REST API is accessible on port 9200 
13.	OCI OpenSearch Dashboards is accessible on 5601 

Always replace your opensearch endpoint at the end of the configuration


