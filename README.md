# comicbox

The dockerfile is used to create a Docker image node that runs the ComicBox application and
the deployment.yml file is used to deploy the application on Kubernetes.

Usage:

1.  Clone the repository
        
        git clone https://github.com/tosinfletcher/comicbox.git

2.  Change into the comicbox directory
        
        cd comicbox
    
3.  Login into Docker Hub
        
        docker login -u <DOCKER_HUB_USERNAME>
    
5.  Use Docker to create a comicbox node image to run the comicbook application with the docker file.
        
        docker build -t <DOCKER_HUB_USERNAME>/comicbox .
    
6.  Push the docker image just created to your Docker Hub account
        
        docker push <DOCKER_HUB_USERNAME>/comicbox

7.  Use vim to open the deployment.yml file.
        
        vim deployment.yml
        
9.  Modify the container image  to the one you just pushed to your Docker Hub account.
    This is to allow kubernetes pull it from your Docker Hub account when creating the application deployment later.
        
        containers:
        - name: comicbox
          image: <DOCKER_HUB_USERNAME>/comicbox
          ports:
            - containerPort: 3000
            
10. Deploy the comicbox application on Kubernetes.
        
        kubectl apply -f deployment.yml

11. Verify that the comicbox application has been successfully created.

        kubectl get pods

12. Access the comicbox application using the following website.
          
        http://<PUBLIC_IP_ADDRESS>:8001

        http://<PUBLIC_IP_ADDRESS>:8001/status

        http://<PUBLIC_IP_ADDRESS>:8001/comicbooks

