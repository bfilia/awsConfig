<h2>Qlik Project</h2>

<h4>Summary</h4>
The goal of this project is to create an EC2 compute instance programmatically and deploy a REST API application to it. In addition, the application has a UI, tests, and is deployed in a container.<br/><br/>

<h4>Architecture</h4>
This project is split between three repositories:<br/>
<a href="https://github.com/bfilia/awsConfig">awsConfig</a>: This repository handles the scripts that run on the user's machine to create an EC2 instance.<br/>
<a href="https://github.com/bfilia/centos7Config">centos7Config</a>: This repository configures the new instance and deploys the application.<br/>
<a href="https://github.com/bfilia/qliktest">qliktest</a>: This repository contains all the code for the REST API application and its Dockerfile.<br/>

The application is built using Node.js and a few packages. Strongloop is used for API endpoints. mocha, superagent, and expect.js are used for testing. is-palindrome is used for checking whether or not a message is a palindrome. MongoDB is being used to persist data, and is hosted with mLab. The application is deployed in a Docker container, and the image is being hosted on Docker hub. nginx is the reverse proxy used to point the server's public dns at the container. The automation of (almost) everything is done using shell scripts.<br/><br/>

<h4>How to build, deploy, and access the app</h4>
This project is built for Centos 7. Build options are provided below:<br/>
<h5>Full build</h5> 
This option will configure your system to create an EC2 instance, configure the instance, and deploy the application. You will need an AWS account with an administrator and its respective access key ID and secret access key ID. This is the intended deployment method<br/>
<b>Steps</b><br/>
<ol>
  <li>Clone this repository using "git clone https://github.com/bfilia/awsConfig.git"</li>
  <li>Run the script using "./awsConfig/awsCreate" (if it does not run, try using "chmod +x /awsConfig/awsCreate")</li>
  <li>Follow the steps it provides and enjoy!</li>
  <li>The application will be accessible via the public dns of the instance. The UI is at /explorer</li>
</ol>
<h5>App only</h5>
This option will clone a copy of the Node.js application and allow you to run it locally.
<b>Steps</b><br/>
<ol>
  <li>Clone the application repository using "git clone https://github.com/bfilia/qliktest.git"</li>
  <li>Change directories into the project using "cd qliktest"</li>
  <li>Install its dependencies using "node ." (or test it if you like using "npm test")</li>
  <li>The application will be hosted at localhost:3000. The UI is at localhost:3000/explorer</li>
</ol>
<h5>Containerized App</h5>
This option will pull the containerized app and run it. Make sure you have docker installed first!
<b>Steps</b><br/>
<ol>
  <li>Pull and run the docker image using "docker run -p 3000:3000 -d --name qrun bfilia/qapp"</li>
  <li>The application will be hosted at localhost:3000. The UI is at localhost:3000/explorer</li>
</ol>
<br/>
<h4>REST API Application</h4>
If you'd like to see the application in action, <a href="ec2-54-174-160-48.compute-1.amazonaws.com/explorer">click here</a>!
