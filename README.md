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
