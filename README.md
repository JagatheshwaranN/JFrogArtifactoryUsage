Understanding Our Repository Structure and Artifact Management
==============================================================
Challenge statement
========================
Scenario: A Core Automation team develops the Core automation framework and which is used by different products team to test their application 
using the Core automation framework as their base framework.

Solution: Core Automation Framework can be created and pushed to some central storage, which can be used as a central repository to store these 
libraries, ensuring consistent access and version control. Also, the product teams can download and use the Core Automation Framework from 
central repository.

Introduction
============
This repo aims to clarify the structure of our repository and the role of JFrog Artifactory in managing our automation frameworks.

CoreAutomationFramework
=======================
The CoreAutomationFramework is the foundation for all automation efforts within our organization. It houses essential modules and components that
are universally applicable across different product teams. Think of it as a shared toolkit providing building blocks for automation development.

TestCoreAutomationFramework
===========================
To illustrate how the CoreAutomationFramework can be used in a real-world scenario, we've created the TestCoreAutomationFramework project. This 
project represents a typical product team's setup, demonstrating how to incorporate the core modules into their specific automation needs.

Centralized Artifact Management with JFrog Artifactory
======================================================
To ensure consistency and efficiency, we've integrated JFrog Artifactory as our centralized repository. The CoreAutomationFramework code is uploaded
to Artifactory, making it readily accessible to all product teams. By downloading the necessary components from Artifactory, teams can avoid redundant
efforts and maintain a unified automation approach.

Benefits of This Structure
==========================
1. Code Reusability: Promotes code sharing and reduces development time.
2. Consistency: Ensures uniformity in automation practices across teams.
3. Efficiency: Streamlines the process of accessing and utilizing core modules.
4. Centralized Management: Simplifies version control and updates of core components.

By adopting this repository structure and leveraging JFrog Artifactory, you can establish a robust framework for automation development and collaboration.

JFrog Intro
===========
JFrog is a comprehensive platform for managing software development artifacts and pipelines. It offers tools to automate and streamline various
stages of the software development lifecycle, from building and testing to deployment and distribution.

Core Components of JFrog Platform
=================================
1. Artifactory: A universal artifact repository for storing and managing various types of artifacts (libraries, packages, Docker images, etc.).
2. Pipelines: A continuous integration and continuous delivery (CI/CD) pipeline orchestration tool.
3. Distribution: A platform for distributing software packages to various channels (end-users, internal teams, cloud platforms).
4. Xray: A universal artifact analysis tool for identifying security vulnerabilities and license compliance issues.

Example Use Cases
=================
To better understand how JFrog can be used, let's explore some common scenarios:

1. Managing Dependencies with Artifactory

Scenario: A development team uses various open-source libraries in their project.
Solution: Artifactory can be used as a central repository to store these libraries, ensuring consistent access and version control. It can also be 
configured to proxy external repositories, reducing network load and improving performance.

2. Automating Builds and Deployments with Pipelines

Scenario: A team wants to automate the build, test, and deployment process for their application.
Solution: JFrog Pipelines can be used to create complex CI/CD pipelines that trigger builds, run tests, and deploy artifacts to different environments
(development, staging, production).

3. Ensuring Software Quality with Xray

Scenario: A security team needs to identify vulnerabilities in the project's dependencies.
Solution: Xray can scan artifacts for known vulnerabilities, license compliance issues, and other security risks, providing detailed reports and 
remediation recommendations.

4. Distributing Software Packages with Distribution

Scenario: A company needs to distribute its software to customers through different channels (e.g., web downloads, app stores).
Solution: JFrog Distribution can be used to manage software releases, create distribution channels, and deliver updates to end-users efficiently.

Steps to be followed to achieve the above (Managing Dependencies with Artifactory) use case
===========================================================================================
Step 1
======
Navigate to the below link and create your own account with JFrog with Google / Custom account.
https://jfrog.com/

Step 2
======
Create a Free Trail Cloud account by choosing any of the cloud partner and fill up your details to create your environment. Create your domain as 
below. => https://learneveryday.jfrog.io/

Step 3
======
After landing on the dashboard page, click on Administration option on top near the search bar. Click on your login icon and click on Quick Repository
Creation. Then, select the Maven option on the display options.

Step 4
======
On Create Repositories dialog, provide the meaningful Repositories prefix name and click on create. You will see the Repositories created message.

Step 5
======
Click on Application option on the top near the Project dropdown. On the left hand side, you can see the Artifactory option. On clicking it, you can
see the below options.
1. Packages
2. Builds
3. Artifacts
4. Release Lifecycle

Step 6
======
Click on Artifacts on the shown options, now you will be shown the list of repositories which got created in the previous step. Select the snapshot-local
repository. You can see the General section with details. Click the Set Me Up button on top. Set Up A Maven Client dialog will open.

Step 7
======
You can see two options Configure and Deploy. Click on Configure. Click on Generate Token button and your token will be generated. Save it for later use.
Scroll down and you can see the Generate Settings button, click on and your settings.xml file will be generated, download the same and copy it inside the
.m2 folder.

Step 8
======
You can see two options Configure and Deploy. Click on Deploy and copy the Distribution Management details shown. Go back to the Framework which you want 
to push, open the pom.xml and add the copied content after the dependencies section.

Step 9
======
Make sure, the maven is using the updated Settings.xml file. Now, you can build the project using Maven option on Intellij or by using the cmd line. On 
cmd line, type mvn deploy and it will create the snapshot and push it to JFrog Artifactory. You can verify the same on JFrog Artifactory.

Step 10
=======
Go to the Child Project, where you want to use the Core Automation Framework and copy the Distribution Management details as below in the pom.xml. So, 
when you run  the project as mvn test, your test will run by downloading the core automation framework code from the JFrog Artifactory website.
