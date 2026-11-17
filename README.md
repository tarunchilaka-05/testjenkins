# testjenkins

# Jenkins CI/CD on Azure: Static Website Deployment

A practice project that automatically deploys a static website using Jenkins on an Azure VM.

## How it works
1. Code is pushed to this GitHub repo.
2. Jenkins (running on an Azure Ubuntu VM) pulls the latest code [on manual build / via webhook / by polling: pick one].
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
- [One or two real points, e.g. fixing a permissions error, opening the Azure firewall port, or connecting Jenkins to GitHub]

## Possible improvements
- Move the job into a `Jenkinsfile` (pipeline as code)
- Add automatic GitHub webhook triggers
- Add HTTPS with a domain name
