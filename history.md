    1  /home/shubhashreesv
    2  # Add Docker's official GPG key:
    3  sudo apt update
    4  sudo apt install ca-certificates curl
    5  sudo install -m 0755 -d /etc/apt/keyrings
    6  sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
    7  sudo chmod a+r /etc/apt/keyrings/docker.asc
    8  # Add the repository to Apt sources:
    9  sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
   10  Types: deb
   11  URIs: https://download.docker.com/linux/ubuntu
   12  Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
   13  Components: stable
   14  Signed-By: /etc/apt/keyrings/docker.asc
   15  EOF
   16  sudo apt update
   17  sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
   18  sudo systemctl status docker
   19  sudo systemctl start docker
   20  sudo docker run hello-world
   21  sudo groupadd docker
   22  sudo usermod -aG docker $USER
   23  newgrp docker
   24  docker run hello-world
   25  history
   26  docker ps
   27  pwd
   28  docker build -t docker-node-app .
   29  sudo usermod -aG docker $USER
   30  docker build -t docker-node-app .
   31  docker run hello-world
   32  sudo docker build -t docker-node-app .
   33  sudo docker run -p 3000:3000 my-node-app
   34  sudo docker run -p 3000:3000 docker-node-app
   35  git push -u dev gay3
   36  git push -u dev day3
   37  git config --global --unset credential.helper
   38  git push -u dev day3
   39  history
   40  touch day3.txt
   41  history >> day3.txt
   42  git add day3.txt
   43  git commit -m "Added day3 history to day3.txt"
   44  git push dev day3
   45  cd ..
   46  cd ..
   47  mv /mnt/c/Users/SUBHA SHREE S V/Downloads/devops-template.zip ~/
   48  mv /mnt/c/Users/SUBHA\ SHREE\ S\ V/Downloads/devops-template.zip ~/
   49  cd /mnt/c/Users/SUBHA\ SHREE\ SV/Downloads
   50  ls
   51  git status
   52  git init
   53  git checkout -b day3
   54  git add .
   55  git commit -m "Dockerized an application"
   56  git config --global user.email "shubha.sv.shree@gmail.com"
   57  git commit -m "Dockerized an application"
   58  git remote add origin https://github.com/shubhashreesv/devops-class
   59  git remote -v
   60  git remote add dev  https://github.com/shubhashreesv/devops-class
   61  git remote -v
   62  git commit -m "Dockerized an application"
   63  git push dev day3
   64  git push -u dev day3
   65  git clone https://github.com/jagadeeshkanna97/docker_sample/
   66  git status
   67  pwd
   68  git init
   69  cd docker_sample
   70  ls
   71  code .
   72  history
   73  cd ..
   74  ls
   75  mv /mnt/c/Users/SUBHA\ SHREE\ S\ /Downloads/template.zip ~/
   76  mv /mnt/c/Users/SUBHA\ SHREE\ SV/Downloads/devops-template.zip ~/
   77  ls
   78  cd /mnt/c/Users/SUBHA\ SHREE\ SV/Downloads
   79  ls
   80  git clone -b day3-ngnix https://github.com/shubhashreesv/devops-class/
   81  ls
   82  git clone -b day3-ngnix https://github.com/shubhashreesv/devops-class/ my-nginx-site
   83  ls
   84  cd my-nginx-site
   85  ls
   86  nano Dockerfile
   87  docker build -t my-nginx-site .
   88  vi Dockerfile
   89  docker build -t my-nginx-site .
   90  docker run -d -p 8080:80 my-nginx-site
   91  docker ps
   92  history
   93  touch history.md
   94  echo history >> history.md
   95  cat history.md
   96  echo "history" >> history.md
   97  cat history.md
   98  history > history.md
