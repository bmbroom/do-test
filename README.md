# Test the NG-CHM RStudio Container on DigitalOcean

The button below will launch the [NG-CHM RStudio container](https://hub.docker.com/r/ngchm/rstudio-ngchm) on the [DigitalOcean](https://digitalocean.com) cloud.

You will need a [DigitalOcean](https://digitalocean.com) account.  At the time of writing, you can get a test account good for $100 or 60 days, whichever comes first.  Once the free trial is over, it will cost about $10/month (depending on the size of virtual machine you choose, and how long you leave it running).

To start, click the button below.  It will open the first of three simple configuration pages.

  1. After a brief pause, the first page should say "Dockerfile detected" and show "Web Service" in the drop-down box.  It also lets you change the value of the PASSWORD environment variable.  You will use username "rstudio" and the password you set to login to the running RStudio container.  Once the container is running, there does not appear to be anyway of finding out the password you set.  So change it to something easy for you to remember!
  2. Clicking Next takes you to the second page, which lets you set the app name and the DigitalOcean region in which to run the app.  There typically isn't any need to change those.
  3. Clicking Next takes you to the third page, which lets you pick the size of compute instance to run on.  The default values are good choices for initial testing ("Basic", 1 GB RAM, 1 vCPU).  (The number of containers should always be 1, even on the "Pro" plan.)

Clicking the "Deploy" button, will initiate "building" the app (basically, pulling the Docker image) and deploying it.  Since the ngchm/rstudio-ngchm image is large, this can take a few minutes.  Please be patient.

Once the app has deployed, a "Live App" button will appear on the page. Clicking it will open a new tab on the running RStudio deployment.  Login with the username "rstudio" and the password you set earlier.

In the lower-right panel, select the "Files" tab (it's selected by default) and the "Upload" button to upload files, and the "More" menu entry "Export..." to download files from the server back to your computer.  You will need to use the latter to view ngchm files you create.

[![Deploy to DO](https://www.deploytodo.com/do-btn-blue.svg)](https://cloud.digitalocean.com/apps/new?repo=https://github.com/bmbroom/do-test/tree/main)

After the RStudio container has been running for a while, the app page should show you some summary statistics of the container's resource utilization.  The Insights tab shows recent CPU and memory usage in more detail.  You can use these as a guide for estimating the size of future deployments.

## Terminate your deployment

When you're finished testing, make sure you have exported **all** the files you need back to your local environment.  Once the deployment is terminated, all of the container's storage is deleted and it is impossible to retrieve any additional content.

To terminate the deployment and stop charges from accruing, choose "Destroy App" from the "Actions" dropdown menu at the top-right of the app page. Enter the app name into the input box to indicate you really mean it, and click the red "Destroy" button.  Destruction should be confirmed in a few moments.  Failing to destroy the app means you will be charged for the time it's running but not being used.

## Pros and Cons of this test environment

Pros:
  - Easy deployment on a cloud server.
  - Choose the about of RAM, CPUs needed easily.
  - Competitive pricing.
  - Secure SSL connection to the server with no effort from the user and at no extra charge.

Cons:
  - You need to create a DigitalOcean account just for a short test (but it is free for initial testing).
  - Storage is ephemeral.  All user files disappear when the deployment is terminated.
  - You cannot get password back if needed. (Destroy and restart app, but all user files will be lost.)
  - Hard to remember app URL (There is a way to link it to your domain, but it's out of scope for this README and not worth it for an ephemeral app.)
  - Currently unknown what happpens to your files if RStudio crashes. Deletion is a likely possibility. Make sure to export copies of important files after any changes.

Future tutorials will describe deployments that overcome some of these issues (but are a bit more complex).
