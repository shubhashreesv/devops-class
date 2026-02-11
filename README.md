# Dockerizing any application

1. Go to VS code and open VM Ubuntu there
    
    Remote SSH: 
    
2. Clone git repo
    
    `git clone`https://github.com/jagadeeshkanna97/docker_sample/`
    
3. Move to cloned repo folder
    
    cd docker_sample
    
4. Create DockerFile (same name) inside that repo, 
Paste the below contents
    
    ```docker
    FROM node:18-alpine
    
    WORKDIR /app
    
    COPY package*.json ./
    
    RUN npm install
    
    COPY . .
    
    EXPOSE 3000
    
    CMD ["npm", "start"]
    
    ```
    

```docker
# docker_sample

FROM node:18-alpine  

- Install base image with Node.js
- node:18 - full node.js image
- node:18-alpine Lightweight Node image based on Alpine Linux

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

copies entire project into container

EXPOSE 3000

tells docker that app runs on port 3000 (not actual port mapping)

CMD ["npm", "start"] 
runs app when container starts

```

# 

`FROM node:18-alpine`

- Install base image with Node.js if not present
- this image has (the above image already has the below installed)
    - node.js ,
    npm,
    lightweight linux OS c
- node:18 - full node.js image
- node:18-alpine Lightweight Node image based on Alpine Linux

`WORKDIR /app`

- Creates /app directory inside the container (if not present)
- Sets it as the current working directory
- All next commands run inside /app
- Basically its like doing
    - `mkdir /app`
    - `cd /app`

`COPY package*.json ./`

- This copies the below files *from your local project → container `/app`*.
    
    ```
    package.json
    package-lock.json
    ```
    

`RUN npm install`

- inside container `/app/node_modules/` is created
- installs express, other libraries  → npm install installs Express because: Express listed in `package.json`.

`COPY . .`

- Everything is copied into `/app`
- copies entire project into container

`EXPOSE 3000`

- tells docker that app runs on port 3000 (not actual port mapping)
- port will be published only when `docker run` cmnd is used

`CMD ["npm", "start"]`

- When container starts, it will run `npm start`
- npm start will run node app.js (from package.json) → Depends on ur project

![image.png](attachment:a6ce982b-4f20-4edf-bb5b-9f4d40631161:image.png)

## Why 2 separate copies for package*.json and other files?

- Each layer gets cached
    
    Layer 1 → FROM node image
    Layer 2 → COPY package.json
    Layer 3 → npm install
    Layer 4 → COPY app code
    
- Suppose you change only `app.js`.
    
    Docker sees:
    
    ```docker
    package.json unchanged → reuse cached npm install
    ```
    

### npm install installs Express because:

Express listed in `package.json`.

# Steps to Run Docker Container

1. Build Image:
    1. `docker build -t docker-node-app .`
        1. `docker build` → Create an image from my project.
            - Read `Dockerfile`
            - Execute each instruction
            - Create image layers
        2. `-t my-node-app`
            - Tag (name) the image
            - this is your image
    
    1️⃣ Finds Dockerfile
    
    2️⃣ Downloads base image (Node Alpine)
    
    3️⃣ Copies package.json
    
    4️⃣ Installs dependencies
    
    5️⃣ Copies app code
    
    6️⃣ Saves final image.
    
2. Run Container
    1. `docker run -p 3000:3000 docker-node-app`
        1. docker run → starts container
        2. 
            
            Windows/VM → 3000
            Container → 3000
            
        3. `docker-node-app`
            
            This is image name
            
        
        1️⃣ Creates container from image
        
        2️⃣ Runs
        
        ```
        npm start
        ```
        
        (from Dockerfile CMD)
        
        3️⃣ Node app starts inside container
        
        4️⃣ Port forwarded to host.
        
3. Test in Browser
    1. Go to [http://localhost:3000](http://localhost:3000/) (if using vm then use vm’s ip instead of local host)
    2. You should see: Hello from Docker!
    
    ![image.png](attachment:8d098295-b330-44b8-a76c-32e233849c78:image.png)
    

Your Project Files
↓
Docker Image Build
↓
Docker Container Runs
↓
App Available on Port 3000

Before Docker build:
Ubuntu VM:
/home/username/docker_sample

After Docker build:
Container:
/app