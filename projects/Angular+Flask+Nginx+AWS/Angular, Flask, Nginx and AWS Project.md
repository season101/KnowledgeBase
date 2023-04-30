To integrate such application into AWS ecosystem, we have to efficiently integrate it with CI/CD pipeline in AWS.
The steps in AWS CI/CD are:

1. AWS CodeCommit: Managed Git Repositories.
2. AWS CodeBuild: Mangaged Build Service that compiles your code, run tests,  and produces deployable artifacts. 
3. AWS CodePipeline: It integrates with CodeCommit, CodeBuild and other AWS services to deploy your application.
4. AWS CodeDeploy: It Automates deployment of your application into various compute services.

To setup CI/CD using AWS services, we typically follow following steps:
1. Create Code Repository: GitHub or AWS CodeCommit.
2. Configure the Build Environment to compile your code and run tests.
3. Setup CodePipeline that connects your source, build and deployment stages.
4. Configure CodeDeploy to deploy your application to your desired compute service.
---
# For Flask Application
Files needed:
1. appsec.yml
	This file is used by AWS CodeDeploy when deploying the application to EC2.
	
```yaml
version: 0.0
os: linux
files:
  - source: /
    destination: /home/ubuntu/python-backend/
hooks:
  AfterInstall:
   - location: scripts/install_dependencies
     timeout: 300
     runas: root
   - location: scripts/codestar_remote_access
     timeout: 300
     runas: root
   - location: scripts/start_server
     timeout: 300
     runas: root
  ApplicationStop:
   - location: scripts/stop_server
     timeout: 300
     runas: root
```
---
```
    2  sudo apt update
    3  sudo apt upgrade
    8  sudo apt install nginx
    9  sudo reboot
   10  cd /etc/nginx/conf.d/
   15  sudo systemctl status nginx
   16  sudo systemctl enable nginx
   27  sudo cp dist/* /var/www/angular-pmac/
   28  sudo cp -r dist/* /var/www/angular-pmac/
   38  cat /etc/nginx/nginx.conf
   43  ng build
   44  sudo rm -rf /var/www/angular-pmac/*
   45  sudo cp -r dist/angular-ulmpmac-app/* /var/www/angular-pmac/
   50  sudo vim /etc/nginx/nginx.conf
   51  sudo systemctl restart nginx
   55  clear
   56  ng build
   57  sudo rm -rf /var/www/angular-pmac/*
   58  sudo cp -r dist/angular-ulmpmac-app/* /var/www/angular-pmac/
   59  sudo systemctl restart nginx
   60  cd frontend/
   61  ls
   62  cd angular-ulmpmac-app/
   63  ls
   64  ng build
   65  sudo rm -rf /var/www/angular-pmac/*
   66  sudo cp -r dist/angular-ulmpmac-app/* /var/www/angular-pmac/
   67  ls /var/www/angular-pmac/
   68  sudo nginx -t
   69  sudo systemctl restart nginx
   70  ng build 
   71  sudo rm -rf /var/www/angular-pmac/*
   72  sudo cp -r dist/angular-ulmpmac-app/* /var/www/angular-pmac/
   73  sudo systemctl restart nginx
   74  clear
   75  cd /etc/nginx/
   76  sudo vim nginx.conf
   77  sudo systemctl restart nginx
   78  sudo vim nginx.conf
   79  ls
   80  cd ~/csci4060-capstone-project/
   81  ls
   88  ps -aux | grep python
   89  kill -9 18799
   90  kill -9 25371
   91  ps -aux | grep python
   92  cd backend/
   93  ls
   94  python3 -m gunicorn app:app
   95  htop
   96  cd csci4060-capstone-project/backend/
   97  ls
   98  pip list | grep mail
   99  pip list | grep flask
  100  pip list | grep Flask
  101  pip freeze > requirements.txt 
  102  cd ..
  103  ls
  104  cd frontend/
  105  ls
  106  cd angular-ulmpmac-app/
  107  ls
  108  npm install --force
  109  ls
  110  ng build
  111  sudo rm -rf /var/www/angular-pmac/*
  112  sudo cp -r dist/angular-ulmpmac-app/* /var/www/angular-pmac/
  113  ls
  114  clear
  115  sudo systemctl restart nginx
  116  ps -aux | grep gunicorn
  117  kill -9 6812 6813
  118  clear
  119  ls
  120  cd csci4060-capstone-project/
  121  ls
  122  cd backend/
  123  ls
  124  python3 -m gunicorn app:app
  125  ls
  126  ps -aux | grep gunicorn
  127  kill -9 4017 5632
  128  ;s
  129  ls
  130  ps -aux | grep gunicorn
  131  ls
  132  rm -rf csci4060-capstone-project/
  133  ls
  134  cd csci4060-capstone-project/
  135  cd backend/
  136  ls
  137  pip install -r requirements.txt 
  138  python3 -m gunicorn app:app
  139  pip install Flask-Mail
  140  pip list
  141  python3 -m gunicorn app:app
  142  htop
  143  clear
  144  ps -deaf | grep gunicorn
  145  apt install snapd
  146  sudo snap install snapd
  147  sudo snap install core
  148  sudo snap refresh core
  149  sudo snap install --classic certbot
  150  sudo ln -s /snap/bin/certbot /usr/bin/certbot
  151  sudo certbot --nginx
  152  clear
  153  sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/nginx-selfsigned.key -out /etc/ssl/certs/nginx-selfsigned.crt
  154  sudo openssl dhparam -out /etc/ssl/certs/dhparam.pem 2048
  155  vim /etc/nginx/nginx.conf
  156  sudo vim /etc/nginx/nginx.conf
  157  sudo systemctl restart nginx
  158  sudo vim /etc/nginx/nginx.conf
  159  sudo nginx -t
  160  sudo vim /etc/nginx/nginx.conf
  161  sudo nginx -t
  162  ls /etc/ssl/certs/ | 
  163  sudo vim /etc/nginx/nginx.conf
  164  sudo nginx -t
  165  sudo service nginx restart
  166  clear
  167  cat /etc/nginx/nginx.conf
  168  sudo vim /etc/nginx/nginx.conf
  169  clear
  170  cd csci4060-capstone-project/backend/
  171  ps -deaf | grep gunicorn
  172  kill -9 19573 20115
  173  ps -deaf | grep gunicorn
  174  ls
  175  python3 -m gunicorn app:app --access-logfile=/home/ubuntu/logs/access.log --error-logfile=/home/ubuntu/logs/errors.log
  176  fg
  177  clear
  178  ls
  179  cd ..
  180  ls
  181  cd frontend/
  182  ls
  183  cd angular-ulmpmac-app/
  184  ls
  185  cd src/environments/
  186  ls
  187  vim environment.prod.ts
  188  ng build
  189  clear
  190  sudo rm -rf /var/www/angular-pmac/*
  191  cd ..
  192  ls
  193  cd ..ls
  194  cd ..
  195  ls
  196  sudo cp -r dist/angular-ulmpmac-app/* /var/www/angular-pmac/
  197  sudo service nginx restart 
  198  ps -deaf | grep gunicorn
  199  history | grep gunicorn
  200  cd ..
  201  ls
  202  cd backend/
  203  ls
  204  python3 -m gunicorn app:app --access-logfile=/home/ubuntu/logs/access.log --error-logfile=/home/ubuntu/logs/errors.log
  205  ps -deaf | grep gunicorn
  206  kill -9 21774 21829
  207  ls
  208  cd csci4060-capstone-project/backend/
  209  ls
  210  python3 -m gunicorn app:app --access-logfile=/home/ubuntu/logs/access.log --error-logfile=/home/ubuntu/logs/errors.log &
  211  ps -deaf | grep gunicorn
  212  cls
  213  clr
  214  clear
  215  dir
  216  cd logs/
  217  nano errors.log 
  218  exit
  219  sudo vim /etc/nginx/nginx.conf
  220  clear
  221  sudo ln -s /snap/bin/certbot /usr/bin/certbot
  222  sudo certbot --nginx
  223  clear
  224  ls
  225  cd logs/
  226  ls
  227  nano errors.log 
  228  clear
  229  ls
  230  cd csci4060-capstone-project/backend/
  231  las
  232  ks
  233  ls
  234  clear
  235  ls
  236  clear
  237  ls
  238  cd logs
  239  nano errors.log 
  240  nano access.log 
  241  clear
  242  cd ..
  243  ls
  244  cde csci4060-capstone-project/backend/
  245  cd csci4060-capstone-project/backend/
  246  ls
  247  env
  248  clear
  249  set
  250  clear
  251  printenv FE_URL
  252  FE_URL=https://pmaculm.tech/
  253  clear
  254  exit
  255  clear
  256  ls
  257  cd csci4060-capstone-project/
  258  ls
  259  cd backend/
  260  FE_URL=https://ulmpmac.com/
  261  echo $FE_URL
  262  exit
  263  clear
  264  cd logs/
  265  nano errors.log 
  266  ls
  267  exit
  268  clear
  269  history
```

python3 -m gunicorn app:app --certfile /home/ubuntu/ulmpmac_com/ulmpmac_domain_chain.crt --keyfile /home/ubuntu/ulmpmac_com/private.key --access-logfile=/home/ubuntu/logs/access.log --error-logfile=/home/ubuntu/logs/errors.log