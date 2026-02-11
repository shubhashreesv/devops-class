```docker
ThemeWagon Template
        ↓ download
Static HTML/CSS/JS files
        ↓ Dockerfile
Nginx Container
        ↓ docker run
Website running in browser

```

- **Nginx** is a **web server and reverse proxy server** mainly used to deliver websites and handle internet traffic efficiently.
- Simple definition: Nginx is software that serves websites and manages web traffic quickly and efficiently.
- Nginx is used when hosting static websites, acting as a reverse proxy, handling HTTPS, load balancing, and improving performance.
- Without Nginx, applications can still run directly, but they may lack scalability, security, and optimized performance, which is why Nginx is commonly used in production environments.

Browser → Nginx → Website files/app → Response back

| Feature | Node Dockerfile | Nginx Dockerfile |
| --- | --- | --- |
| Purpose | Run application | Serve static files |
| Runtime needed | Node.js runtime | Web server only |
| Code execution | Yes | No |
| Backend logic | Yes | No |
| npm install | Required | Not required |
| Start command | Needed (`npm start`) | Not needed |
| Example | API / fullstack app | HTML template |

## 1. Download ThemeWagon Template

- Pick any template  & download zip (free)
- To move it to ubuntu, I pushed into github (after unzipping) from my windows, and cloned that repo (branch) into my VM

## 2. Check whether all the file exists by use `ls`

## 3. Create Dockerfile (Nginx)

- `nano Dockerfile`
- Paste: (to save: Ctrl + X → Y (Yes) → Enter)
    
    ```docker
    FROM nginx:latest
    COPY . /usr/share/nginx/html
    EXPOSE 80
    ```
    
- Nginx is already configured to serve website files from that folder by default.
- So when you copy HTML there → Nginx automatically shows your website.
- Standard Linux convention
    
    
    | Folder | Purpose |
    | --- | --- |
    | `/usr` | System software |
    | `/usr/share` | Shared files |
    | `/usr/share/nginx` | Nginx related files |
    | `/usr/share/nginx/html` | Website files |
- Nginx supports serving static web files such as HTML, CSS, JavaScript, images, fonts, videos, and documents. It does not execute backend code but efficiently delivers static content to clients, which makes it ideal for frontend hosting.

## 4. Build Docker Image

- `docker build -t my-nginx-site .`

## 5. Run Container

- `docker run -d -p 8080:80 my-nginx-site`

## 6. In Browser, Now you can see the extracted file on live:

- [`http://192.168.72.128:8080/`](http://192.168.72.128:8080/)

![image.png](attachment:4f6eff4e-d6b7-4a8a-b729-acf802f583f7:image.png)