# Kubernetes-Networking
![image](https://github.com/singhritesh85/Kubernetes-Networking/assets/56765895/69bbf29c-8057-43ce-a33f-1951ea4eee8d)
#### Container to Container Communication
All the containers inside the pod have the same IP address as assigned to the Pod. The **container to container communication happens over the localhost.** 
<br><br/>
In the diagram shown above Pod1 is a multi-container pod (with containers C1 and C2) and Pod2, Pod3 and Pod4 are single container pods. The Container to container communication is shown in the diagram above with green line.
<br><br/>
Below screenshot shows a yaml file using which created a pod (replicas: 1) through the deployment. This pod has two containers one main container (nginx-container) and another container is sidecar container (alpine-container). From main container sending the log files to sidecar container. 
![image](https://github.com/singhritesh85/Kubernetes-Networking/assets/56765895/196fc8b3-d292-419e-88e1-a8824768e385)
Now check the IP address assigned to Pod and each of the containers(main container and sidecar container). They have the same IP address. 
![image](https://github.com/singhritesh85/Kubernetes-Networking/assets/56765895/78b70c18-6536-4831-879d-48c9c100c2fa)
![image](https://github.com/singhritesh85/Kubernetes-Networking/assets/56765895/db043d20-cd93-486b-8cba-0679560d4ef8)
![image](https://github.com/singhritesh85/Kubernetes-Networking/assets/56765895/38d3347d-2ff8-47b4-adb0-ca727923d509)
![image](https://github.com/singhritesh85/Kubernetes-Networking/assets/56765895/499f5e74-2251-41bc-a55d-4764b25a336a)
![image](https://github.com/singhritesh85/Kubernetes-Networking/assets/56765895/50755497-8e23-4df7-86bf-8cd5b851c05f)
From the alpine container we did curl to the localhost and we saw the home page for nginx.
![image](https://github.com/singhritesh85/Kubernetes-Networking/assets/56765895/9e443465-f865-4ca5-acd8-998af6a90dba)
<br><br/>
#### Pod to Pod Communication
**In kubernetes each pod has a unique IP address. When communication happens between the pods then it will happen over the IP address assign to the pod. The traffic flows from eth0 of Pod1 to eth0 of Pod2 through the virtual bridge network.**
<br><br/>
Here I have created another Pod with centos image and tried to ping nginx pod IP from here and centos pod IP from nginx pod and see the response.
![image](https://github.com/singhritesh85/Kubernetes-Networking/assets/56765895/3524aee9-25b3-40ed-a8a9-98292fa7ea1e)
![image](https://github.com/singhritesh85/Kubernetes-Networking/assets/56765895/9b62b20d-aba8-4344-ad00-3a0edd39efc6)
![image](https://github.com/singhritesh85/Kubernetes-Networking/assets/56765895/53a15f27-f82b-4fda-8209-ff4b79c63479)
**Pod to Pod communication happens over the IP address assigned to the pod.**
<br<br/>
#### Pod to Service Communication
![image](https://github.com/singhritesh85/Kubernetes-Networking/assets/56765895/ac52b4d4-8fc6-4a0e-a65f-509c04bf17ba)
Kubernetes Service serves as loadbalancer and routes the traffic to the Pod in **round robin algorithm**.
<br><br/>
I have created three pods and a service which routes the traffic to the pods in round robin algorithm. 
<br><br/>
![image](https://github.com/singhritesh85/Kubernetes-Networking/assets/56765895/0f3abd68-2252-41ee-b124-46c3be4c8fc4)
![image](https://github.com/singhritesh85/Kubernetes-Networking/assets/56765895/0b890d79-a126-4e86-9696-05b4a2bb151a)
<br><br/>
The traffic which comes to the Kubernetes Service will be routed to the endpoints (the three IP addresses assigned to the pod and the port) in round robin algorithm.
<br><br/>
![image](https://github.com/singhritesh85/Kubernetes-Networking/assets/56765895/d55af9b9-c069-404b-b4a2-c2f3034d1529)
![image](https://github.com/singhritesh85/Kubernetes-Networking/assets/56765895/586f5b7e-920d-4891-b113-9f45fa2c7ae0)
