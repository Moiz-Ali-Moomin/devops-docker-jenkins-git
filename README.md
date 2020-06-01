# devops-jenkins-docker-git

# code to start services
systemctl start jenkins
systemctl start docker

mkdir devops-jenkins-docker-git

git clone https://www.github.com/{your account name}/devops-jenkins-docker-git

# To create post-commit hook

* cd devops-jenkins-docker-git
* cd .git/hooks
* Edit the post-commit.sample file using mv post-commit.sample && vim post-commit
* if you don't have that file already use touch post-commit and then vim post-commit 
* Then add this line inside that file

#!/bin/bash
git push

* Now save this file

# To create a development branch
* git branch dev1

# making directories

mkdir production_code
mkdir development_code 

# code inside shell execute job1

if sudo docker ps | grep production_server  
then
echo "Production server already running" 
else
sudo docker run -d -t -i -p 8081:80 -v /production_code:/usr/local/apache2/htdocs/ --name production_server httpd
fi
sudo cp -r -v -f * /production_code/


# code inside shell execute job2

if sudo docker ps | grep development_server  
then
echo "development server already running" 
else
sudo docker run -d -t -i -p 8081:80 -v /development_code:/usr/local/apache2/htdocs/ --name development_server httpd
fi
sudo cp -r -v -f * /development_code/


# Step by Step Documentation
https://devops-project-iiec.blogspot.com/2020/05/devops-continous-integration-with-git.html
