# Continuous-Integration-with-AWS-CodeBuild
Introducing Today's Project! In this project, I will demonstrate how to use CodeBuild to automate the Build prcess in our CI/CD Pipeline. A Build is the processing of compressing code into a smaller file like a zip file. Compressing makes it easier to deploy, which is what we're going to be doing later in this project

<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Continuous Integration with CodeBuild

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-codebuild-updated)

**Author:** Sentle Thabana  
**Email:** sentlewstrn@gmail.com

---

![Image](http://learn.nextwork.org/genuine_gray_festive_clementine/uploads/aws-devops-codebuild-updated_35588a47)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use CodeBuild to automate the Build prcess in our CI/CD Pipeline. A Build is the processing of compressing code into a smaller file like a zip file. Compressing makes it easier to deploy, which is what we're going to be doing later in this project.

### Key tools and concepts

Services I used were CodeBuild, CodeConnections, Github and S3

### Project reflection

This project took me approximately 3 hours, the challenging part was running a build we kept getting errors, the most rewarding part is seeing the build artifacts in our s3 buckets

This project is part four of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project today.

---

## Setting up a CodeBuild Project

CodeBuild is a continuous integration service, which means it helps you compile and package code which means turning it into something computers can run and store, engineering teams use it because it allows us to automate processes. If CI didnt exist, it would mean engineering teams need to compile the code manually themselves.

My CodeBuild project's source configuration means or suggests the place where CodeBuild gets our application files from.

![Image](http://learn.nextwork.org/genuine_gray_festive_clementine/uploads/aws-devops-codebuild-updated_fewgrhte)

---

## Connecting CodeBuild with GitHub

There are multiple credential types for GitHub, like... I used GitHub App because...

The service that helped connect AWS to GitHub is CodeConnections, we had to connect AWS inorder for it to reach the files we want it to compile and store and those files are in GitHub. We used authorization for CodeConnections to be able to reach GitHub.

![Image](http://learn.nextwork.org/genuine_gray_festive_clementine/uploads/aws-devops-codebuild-updated_a7c98e2d)

---

## CodeBuild Configurations

### Environment

My CodeBuild project's Environment configuration means the environment setup for the compute power that will be compiling the files when we run our CodeBuild project, it includes settings like the image and service role. This settings determine how a new EC2 Instance will be spun up. It's important to have the EC2 Instance to have permissions that make it possible for us to spin it up with these settings i.e service role.

### Artifacts

Build artifacts are the files that will get created as part of the CodeBuild process. They're important because they represent artifacts that need to be used later on in the CI/CD Pipeline for example, our Build Artifact will create a Compress file that will be used to deploy the WebApp. To deploy our Build Artifact, we created an S3 bucket.

### Packaging

When setting up CodeBuild, I also chose to package artifacts in a Zip file because this helps with package management as files are all organised neatly in a single file, it also helps with size configuration.

### Monitoring

For monitoring, I enabled CloudWatch Logs, which is a service that will note down any commands that are run and any errors that happen, this is helpful for troubleshooting.

---

## buildspec.yml

My first build failed because there was no buildspec file in my application. A Buildspec.yaml file is needed because it tells CodeBuild how to run the Build process.

The first two phases in my buildspec.yml file install Java and gets access to CodeArtifact. The third phase in my buildspec.yml file compiles the webapp, the fourth phase in our buildspec.yml file packages the file into a compressed artifact.

![Image](http://learn.nextwork.org/genuine_gray_festive_clementine/uploads/aws-devops-codebuild-updated_35588a47)

---

## Success!

My second build also failed, but with a different error that said settings.xml is not recognised by github. So we pushed and committed esentially giving it the permission to be in our application on git.

To resolve the second error, I had to create and configure the settings.xml file in our application

To verify the build, I checked my S3 bucket, seeing the Build Artifact tells me that the Buidl was a success. The Build compiled and compressed the file and stored it into our S3 Bucket.

![Image](http://learn.nextwork.org/genuine_gray_festive_clementine/uploads/aws-devops-codebuild-updated_d9cc6191)

---

## Automating Testing

---

---
