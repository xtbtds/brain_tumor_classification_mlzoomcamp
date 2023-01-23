This is a ***FastAPI + React JS + nginx*** application for brain tumor classification. 
It uses trained xgboost model with 75% accuracy. You can see how it was trained in [**notebook.ipynb**](https://github.com/xtbtds/brain_tumor_prediction/blob/main/backend/notebook.ipynb)  

# Table of contents
* [Problem description](#problem-description)
* [Dataset](#dataset)
* [Usage](#usage)
* [Deploy to AWS](#deploy-to-aws)


# Problem description

# Dataset

# Usage 
- `git clone https://github.com/xtbtds/brain_tumor_classification_mlzoomcamp`
- `cd <project folder>`
- `docker-compose up`
- wait for docker-compose to build and run images.
- go to `http://localhost` 
- click "select" button to select an image from your computer, then click upload to upload it to the service.
- wait a little bit (5-10 s) and you'll see the probabilies of different deceases

![](app-usage-gif.gif) 

**Note:** you don't need to download the whole repo if you don't want to. Another way to run the app is to use [this  docker-compose file](https://github.com/xtbtds/brain_tumor_classification/blob/main/pulled/docker-compose.yml). It pulles already built images from docker hub. Copy this file to your local machine and run `docker-compose up`. 

# Deploy to AWS
1. Go to AWS, sign in to the console and create ubuntu EC2 instance, create and download your .PEM key 
2. Give your .pem file the right permissions, otherwise it won't let you to ssh to your EC2 instance because of wrong permissions:
  - `chmod 0400 <YOUR_PEM_FILE.pem>`
3. Connect to your EC2 instance:
  - `ssh -i <YOUR_PEM_FILE.pem` ubuntu@<your_ec2_public_IP>
4. Run this steps to install docker and docker-compose to your EC2 ubuntu machine:
  - `yum update -y`
  - `amazon-linux-extras install docker -y`
  - `service docker start`
  - `systemctl enable docker`
  - `usermod -a -G docker ec2-user`
  - `chmod 666 /var/run/docker.sock`
  - `curl -L https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose`
  - `chmod +x /usr/local/bin/docker-compose`
