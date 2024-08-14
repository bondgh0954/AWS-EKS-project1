<h1>AWS EKS Cluster</h1>
<h2>Technologies used</h2>

- <b>Kubernetes</b> 
- <b>AWS EKS</b>




<h2>Detailed Description of Project </h2>
1. Configure necessary IAM roles<br/>
2. Create VPC with Cloudformation Template for worker nodes<br/>
3. Create EKS cluster (Control Plane Nodes)<br/>
4. Create Node Group for Worker Nodes and attach to EKS cluster<br/>
5. Configure Auto-scaling of worker nodes<br/>
6. Deploy a sample application to EKS cluster<br/>





   <p align="">
   <h2>step1    Configure IAM Role for EKS Cluster</h2>
   Create a new role in the IAM service of AWS<br/>
   Select EKS cluster service<br/>
   Add AmazonEKSClusterPolicy to the role<br/>
   <img src='./img/w2.png' height="80%" width="80%" alt="Disk Sanitization Steps">

 


   <h2>step2  Create VPC with Cloudformation Template for worker Nodes</h2>
   EKS cluster needs specific networking configuration<br/>
   Default VPC is not optimized for it<br/>
   Search aws documentation for Yaml configuration file for creating VPC for eks cluster<br/>
   Create stack in aws cloudformation<br/>
   Copy and paste the url template in the text area under Amazon s3 url <br/>
   
  link:   https://s3.us-west-2.amazonaws.com/amazon-eks/cloudformation/2020-10-29/amazon-eks-vpc-private-subnets.yaml<br/>

  Give your stack a name and create vpc <br/>

  vpc is created with the name 'vpc-stack'
  <img src='./img/w3.png' height="80%" width="80%" alt="Disk Sanitization Step"> 

  

   <h2>step3 Create EKS cluster</h2>
   Create Kubernetes cluster from Elastic Kubernetes Service <br/>
   Configuration 
   use the created IAM role as the cluster service role <br/>
   Networking configuration<br/>
   the created VPC is used as the VPC for the cluster<br/>


   Cluster is created and acive <br/>
   <img src='./img/w4.png' height="80%" width="80%" alt="Disk Sanitization Step"> 
   

 
   
   

   <h2>step4  Create Node Group for Worker Nodes and attach to EKS cluster</h2>
   Before creating the nodes in the cluster, Create IAM role for the node Group <br/>
   
   
   IAM role is given 3 permissions<br/>
   <img src='./img/w5.png' height="80%" width="80%" alt="Disk Sanitization Step"> 

   Create nodegroups in the cluster from "compute"<br/>
   The created IAM role is selected for the node IAM role during creation <br/>
   Select the nodetype<br/>
   Capacity and ImageType<br/>

   <img src='./img/w6.png' height="80%" width="80%" alt="Disk Sanitization Step"> 

   NodeGroup successfully created<br/>
   <img src='./img/w7.png' height="80%" width="80%" alt="Disk Sanitization Step"> 


   The cluster can be connected to <br/>
   <img src='./img/w8.png' height="80%" width="80%" alt="Disk Sanitization Step"> 

 
     

</p>
