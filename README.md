# contact-form
### Docker/Hyper PWP Contact Form Demo

Install/Sign Up:

https://www.docker.com/products/docker-desktop

https://hub.docker.com/

https://hyper.sh/

#### Commands to run from directory with Dockerfile in it:

Build the image with your DockerHub username:\
`docker build . -t <YOUR_USERNAME>/contact-form`\
`-t` allows us to give the image our own name\
`.` refers to where you want to create the image from

Check for the image:\
`docker images`

Create a new container from the image:\
`docker container run --rm -p 8080:80 -d <YOUR_USERNAME>/contact-form`\
`--rm` means to delete the container when it stops running (default is to be manually removed)\
`-p 8080:80` means to publish Docker's port 80 to your local machine's port 8080\
`-d` means to run in detach mode, or in other words in the background of your terminal

Check for the running container:\
`docker container ls`

Go to localhost:8080 to see your app!

---

#### [For Hyper hosting](https://hyper.sh/howto/deploying-a-docker-based-php-project-with-hyper.sh.html):

Login to DockerHub:\
`docker login`

Push image to DockerHub:\
`docker push <YOUR_USERNAME>/tiny-php-app`

Run Hyper container from DockerHub image:\
`hyper run -d -p 80:80 <YOUR_USERNAME>/tiny-php-app`

Allocate & attach floating IP:\
`hyper fip allocate 1`\
`hyper fip attach <YOUR_IP> <YOUR_CONTAINER_ID>`

Go to the given IP to see your live, hosted app!!!!

> **Note:** Make sure all your necessary IPs are configured to work from your Google Recaptcha admin settings.\
> **Note:** This assumes you have Docker installed and running, have a DockerHub account, and have installed and configured Hyper CLI with your Hyper account keys.

---
#### In Beta:
#### [For Certbot Domain SSL Certification](https://certbot.eff.org/lets-encrypt/ubuntubionic-apache)

List your running Hyper containers:\
`hyper ps`

Go to the command line of your running Hyper container:\
`hyper exec -it <YOUR_CONTAINER_NAME> bash`

Run these commands in sequence to install Certbot, answering any questions with "Y" or Enter:\
`apt-get update`\
`apt-get install software-properties-common`\
`add-apt-repository ppa:certbot/certbot`\
`apt-get update`\
`apt-get install python-certbot-apache`\
`certbot --apache`

Enter any email when prompted and then enter the domain name you will be using for your PWP.

Exit the Hyper shell:\
`exit`

You should now have an SSL Certificate for your hosted, domained PWP!
