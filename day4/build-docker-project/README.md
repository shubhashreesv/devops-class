Jenkins will:

1️⃣ Clone that repo
2️⃣ Build Docker image from it
3️⃣ Run container from that image

1. Job 1 → Pull Code
    - Name: dockerized-proj-builder
    - Repo URL: https://github.com/shubhashreesv/my-nginx-app.git
    - Branch: */main
    - Execute Shell is optional
2. Job 2 → Build Docker Image
    - Name: dockerized-proj-image
    - Build Trigger > Build after other projects built > dockerized-proj-builder > Trigger only if stable
    - Execute Shell:
        
        ```docker
        cd $WORKSPACE
        docker build -t my-nginx-app .
        echo "Image built"
        ```
        
3. Job 3 → Run Container
    - Name: dockerized-proj-run
    - Build Trigger: > Build after other projects built > dockerized-proj-image > Trigger only if stable
    - Execute Shell:
        
        ```docker
        docker rm -f nginx-container || true
        docker run -d -p 8085:80 --name nginx-container my-nginx-app
        echo "Container running"
        
        ```
        

## Only run: **`dockerized-proj-builder`**

## Check output: [`http://192.168.72.129:8085`](http://192.168.72.129:8085/)

---

I got an error: Docker Permission error, I resolved with the below

`sudo usermod -aG docker jenkins
sudo systemctl restart jenkins`

