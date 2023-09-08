Hosting Static website on GitLab
Here we push static website on ci/cd pipeline in gitlab

Solution:
Create your Gitlab account and use the free tier

After setting your account you will find create new project page there you select "Create new project".

You will be redirected to the new page where you give name to your project and choose either you want to work as a group or individually.

Don't forget to tick the ReadMe check box.

Then you will be redirected to the new page here you will find the pop down options on middle left corner of your screen which contain options to create new file, upload file, etc.

There you will upload new file and upload your index.html file

Now move back to the previous screen and again create new file

Your code will not move to pipeline until you create ".gitlab-ci.ym" file here you deploy your site to gitlab pages

Code

image: alpine:latest

pages:

stage: deploy

script:

- echo "Deploying to GitLab Pages"
- mkdir .public
- cp -r * .public || exit 0
- mv .public public
artifacts:

paths:
  - public
only:

- main
This is the general code which can be used to deploy static website

After commiting it our site will be successfully deployed we can check this by moving to build > pipeline and see the status is active

We can also visit your site by folling this link "https://your-github-username.gitlab.io/project-name"

Problems
The task seems simple, but it's not

If you are new to gitlab and then try to deploy then after you commit .gitlab-ci.ym commit you will find a validation error
You will be given two options either you use runner or validate your credit card
If you go want to go runner option then their is another process by which we setup our runner and link it with our project, I will not discuss this process here
So after doing all the necessary task which were require to set up runner you will still find the validation error
So you will have to validate your account by your credit card
Validation process take some time and deduct some amount from your account which is against their policy.