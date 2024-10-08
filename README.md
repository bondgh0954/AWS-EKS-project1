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
   <h2>step 1    Configure IAM Role for EKS Cluster</h2>
   Create a new role in the IAM service of AWS<br/>
   Select EKS cluster service<br/>
   Add AmazonEKSClusterPolicy to the role<br/>
   <img src='./img/w2.png' height="80%" width="80%" alt="Disk Sanitization Steps">

 


   <h2>step 2  Create VPC with Cloudformation Template for worker Nodes</h2>
   EKS cluster needs specific networking configuration<br/>
   Default VPC is not optimized for it<br/>
   Search aws documentation for Yaml configuration file for creating VPC for eks cluster<br/>
   Create stack in aws cloudformation<br/>
   Copy and paste the url template in the text area under Amazon s3 url <br/>
   
  link:   https://s3.us-west-2.amazonaws.com/amazon-eks/cloudformation/2020-10-29/amazon-eks-vpc-private-subnets.yaml<br/>

  Give your stack a name and create vpc <br/>

  vpc is created with the name 'vpc-stack'
  <img src='./img/w3.png' height="80%" width="80%" alt="Disk Sanitization Step"> 

  

   <h2>step 3 Create EKS cluster</h2>
   Create Kubernetes cluster from Elastic Kubernetes Service <br/>
   Configuration 
   use the created IAM role as the cluster service role <br/>
   Networking configuration<br/>
   the created VPC is used as the VPC for the cluster<br/>


   Cluster is created and acive <br/>
   <img src='./img/w4.png' height="80%" width="80%" alt="Disk Sanitization Step"> 
   

 
   
   

   <h2>step 4  Create Node Group for Worker Nodes and attach to EKS cluster</h2>
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


  Connect to the cluster <br/>
  <img src='./img/w8.png' height="80%" width="80%" alt="Disk Sanitization Step"> 


  
   <h2>step 5  Configure Auto-scaling of worker nodes</h2>
   Configuring autoscaling helps to save cost by adjusting the number of nodes<br/>
   when the load of application is higher or lower <br/>

   
   
   
   Create a custom policy and attach to the the role of the nodeGroup<br/>
   <img src='./img/w9.png' height="80%" width="80%" alt="Disk Sanitization Step"> 

   
   
   Attach the policy to the nodeGroup IAM role<br/>
   <img src='./img/w10.png' height="80%" width="80%" alt="Disk Sanitization Step"> 


   Deploy the cluster autoscaler yaml file in the cluster<br/>
   https://raw.githubusercontent.com/kubernetes/autoscaler/master/cluster-autoscaler/cloudprovider/aws/examples/cluster-autoscaler-autodiscover.yaml

   <img src='./img/w11.png' height="80%" width="80%" alt="Disk Sanitization Step"> 

   Edit the cluster autoscaler deployment<br/>
   <img src='./img/w12.png' height="80%" width="80%" alt="Disk Sanitization Step"> 
   
   add: "cluster-autoscaler.kubernetes.io/safe-to-evict:'false'" to the annotation<br/>

   command:<br/>
   - balance-similar-node-groups
   - skip-nodes-with-system-pods=false

   Replace the cluster name with the name of your cluster<br/>
   Replace the kubernetes version with the version of the cluster<br/>
   The tags to specific version can be found in kubernetes github repo<br/>
   https://github.com/kubernetes/autoscaler/tags
   

 
     

</p>
