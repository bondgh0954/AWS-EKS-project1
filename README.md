<h1>AWS EKS Cluster</h1>
<h2>Technologies used</h2>

- <b>Kubernetes</b> 
- <b>AWS EKS</b>




<h2>Detailed Description of Project </h2>
1. Configure necessary IAM roles<br/>
2. Create VPC with Cloudformation Template for worker Nodes<br/>
3. Create EKS cluster (Control Plane Nodes)<br/>
4. Create Node Group for Worker Nodes and attach to EKS cluster<br/>
5. Configure Auto-scaling of worker nodes<br/>
6. Deploy a sample application to EKS cluster<br/>





   <p align="">
   <h2>step1    Configure IAM Role for EKS Cluster</h2>

   Kubernetes cluster created in linode<br/>
   <img src='./is/a1.png' height="80%" width="80%" alt="Disk Sanitization Steps">

   
   change the permissions of the kubeconfig file and export it as environmental variable<br/>
   <img src='./is/a2.png' height="80%" width="80%" alt="Disk Sanitization Steps">


   <h2>step2  Deploy Mysql database with 3 secondary replicas and volumes for data persistence</h2>
  
   Search for mysql helm chart<br/>
   add the repository that contains the helm chart<br/>
   Create a values configuration file to override certain default values of the helm chart<br/>
   set architecture to replication<br/>
   set to create persistence volume with linode block storage<br/>
   set auth root password<br/>
   helm-mysql.yaml<br/>
   <img src='./is/a3.png' height="80%" width="80%" alt="Disk Sanitization Steps">


   Install the chart by passing the values file to override certain values<br/>
   <img src='./is/a4.png' height="80%" width="80%" alt="Disk Sanitization Steps">


   mysql pod started with the set number of replicas in the values file "helm-mysql.yaml"<br/>
   mysql service and pods are all successfully created<br/>
   <img src='./is/a7.png' height="80%" width="80%" alt="Disk Sanitization Steps">


   persistence volume is created for all the pod replicas as specified in the values configuration file<br/>
   <img src='./is/a6.png' height="80%" width="80%" alt="Disk Sanitization Steps">
   
  

   

   <h2>step3   Deploy the Java application with 2 replicas</h2>
    add dockerfile to the application<br/>
    build a docker image from the application<br/>
    push the image to a private docker registry<br/>
    <img src='./is/a8.png' height="80%" width="80%" alt="Disk Sanitization Steps">
 
   
   

   <h2>step4</h2>
 
     

</p>
