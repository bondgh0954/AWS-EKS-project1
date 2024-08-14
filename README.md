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

  
   
  

   <img src='./is/a3.png' height="80%" width="80%" alt="Disk Sanitization Step">



   
  

   

   <h2>step3 Create EKS cluster</h2>
   

 
   
   

   <h2>step4</h2>
 
     

</p>
