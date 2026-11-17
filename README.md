# testjenkins

# Jenkins CI/CD on Azure: Static Website Deployment

A practice project that automatically deploys a static website using Jenkins on an Azure VM.

## How it works
1. Code is pushed to this GitHub repo.
2. Jenkins (running on an Azure Ubuntu VM) pulls the latest code by polling
3. A build step copies `index.html` to the Nginx web root.
4. Nginx serves the updated site.

## Tech stack
Jenkins, Azure VM (Ubuntu, free tier), Nginx, GitHub, Linux

## Setup steps
1. Create an Ubuntu VM on Azure and open ports 22, 80, and 8080 in the network security group.
2. Install Jenkins and Nginx on the VM.
3. Create a Jenkins job linked to this GitHub repo.
4. Add a build step, e.g. `sudo cp index.html /var/www/html/index.html`.
5. Give the `jenkins` user permission to run that command (via sudoers or file permissions).
6. Run the job and open the VM's public IP to see the site.

## What I learned
- Opened the Azure firewall port for Jenkins and fixed file permissions so the `jenkins` user could deploy to Nginx.
- Connected Jenkins to GitHub to build and deploy the site on demand.

## Possible improvements
- Move the job into a `Jenkinsfile` (pipeline as code)
- Add automatic GitHub webhook triggers
- Add HTTPS with a domain name
