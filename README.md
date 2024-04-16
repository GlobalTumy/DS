PRACTICAL-1: ASP.NET CORE MVC

Step-1: Install .Net Core Sdk (Link: https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/install)

Step-2: Create folder MyMVC folder in D: drive or any other drive. 

Step-3: Open command prompt and perform the following operations.
Command to create mvc project:
(in command prompt) cd myc (in D drive)
dotnet new mvc --auth none

Step-4: Go to controllers’ folder and modify HomeController.cs file to match following: 

using System;
using System.Collections.Generic;
using System.Diagnostics; 
using System.Linq;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc; 
using Microsoft.Extensions.Logging; 
using MyMVC.Models;
namespace MyMVC.Controllers
{ public class HomeController : Controller
{
public String Index()
{ return " Hello world"; }
}
}

Step-5: Run the project.
(in command prompt) dotnet run
Now open browser and and type URL: localhost:5073

Step-6: Now go back to command prompt and stop running project using CTRL+C.

Step-7: Go to models’ folder and add new file StockQuote.cs to it with following content: 

using System;
namespace MyMVC.Models
{
public class StockQuote
{ public string Symbol {get;set;} 
public int Price{get;set;}
}
}

Step-8: Now Add View to folder then home folder in it and modify index.cshtml file to match following: 

@{
ViewData["Title"] = "Home Page";
}
<div>
Symbol: @Model.Symbol <br/> 
Price: $@Model.Price <br/>
</div>

Step-9: Now modify HomeController.cs file to match following: 

using System;
using System.Collections.Generic;
using System.Diagnostics; 
using System.Linq;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc; 
using Microsoft.Extensions.Logging; 
using MyMVC.Models;
namespace MyMVC.Controllers
{
public class HomeController : Controller
{ public async Task <IActionResult> Index()
{
var model= new StockQuote{ Symbol='HLLO', Price=3200}; 
return View(model);
}
}
}

Step-10: Now run the project using:
dotnet run

Step-11: Now go back to browser and refresh to get modified view response.


PRACTICAL-2: BUILDING ASP.NET CORE REST API

Step-1: Download and install.

To start building .NET apps you just need to download and install the .NET SDK (Software Development 
Kit version 3.0 above).
Link: https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/install

Step-2: Check everything installed correctly. Once you've installed, open a new command prompt and run 
the following command:

Command prompt: > dotnet

CREATE YOUR WEB API:

Step-1: Open two command prompts. 

Command prompt 1:
dotnet new webapi -o Glossary
cd Glossary 
dotnet run

Command Prompt 2: (try running ready-made weatherforecast class for testing)

curl --insecure http://localhost:5089/weatherforecast

Step-3: Now Change the content:
To get started, remove the WeatherForecast.cs file from the root of the project and the 
WeatherForecastController.cs file from the Controllers folder.

Add Following two files.

1) D:\Glossary\GlossaryItem.cs (type it in notepad and save as all files)

//GlossaryItem.cs 

namespace Glossary {
public class GlossaryItem{
public string Term { get; set; }
public string Definition { get; set; }}}

2) D:\Glossary\Controllers\ GlossaryController.cs (type it in notepad and save as all files)

//Controllers/GlossaryController.cs 

using System;
using System.Collections.Generic; 
using Microsoft.AspNetCore.Mvc; 
using System.IO;
namespace Glossary.Controllers
{
[ApiController] 
[Route("api/[controller]")]
public class GlossaryController: ControllerBase
{
private static List<GlossaryItem> Glossary = new List<GlossaryItem> { 
new GlossaryItem
{
Term= "HTML",
Definition = "Hypertext Markup Language"
},
new GlossaryItem
{
Term= "MVC",
Definition = "Model View Controller"
},
new GlossaryItem
{
Term= "OpenID",
Definition = "An open standard for authentication"
}
};
[HttpGet]
public ActionResult<List<GlossaryItem>> Get()
{ return Ok(Glossary);
}
[HttpGet] 
[Route("{term}")]
public ActionResult<GlossaryItem> Get(string term)
{
var glossaryItem = Glossary.Find(item =>
item.Term.Equals(term, StringComparison.InvariantCultureIgnoreCase)); 

if (glossaryItem == null)
{ return NotFound();
}
else
{
return Ok(glossaryItem);
}
}
[HttpPost]
public ActionResult Post(GlossaryItem glossaryItem)
{
var existingGlossaryItem = Glossary.Find(item => 
item.Term.Equals(glossaryItem.Term, StringComparison.InvariantCultureIgnoreCase)); 
if (existingGlossaryItem != null)
{
return Conflict("Cannot create the term because it already exists.");
}
else
{
Glossary.Add(glossaryItem);
var resourceUrl = Path.Combine(Request.Path.ToString(), Uri.EscapeUriString(glossaryItem.Term)); 
return Created(resourceUrl, glossaryItem);
}
}
[HttpPut]
public ActionResult Put(GlossaryItem glossaryItem)
{
var existingGlossaryItem = Glossary.Find(item => 
item.Term.Equals(glossaryItem.Term, StringComparison.InvariantCultureIgnoreCase)); 
if (existingGlossaryItem == null)
{
return BadRequest("Cannot update a nont existing term.");
}
else
{
existingGlossaryItem.Definition = glossaryItem.Definition; 
return Ok();
}
}
[HttpDelete] 
[Route("{term}")]
public ActionResult Delete(string term)
{
var glossaryItem = Glossary.Find(item =>
item.Term.Equals(term, StringComparison.InvariantCultureIgnoreCase)); 
if (glossaryItem == null)
{ return NotFound();
}
else
{ Glossary.Remove(glossaryItem); 
return NoContent();
}}}}

On Command prompt 2:
1) Getting a list of item

curl --insecure http://localhost:5202/api/glossary

2) Getting a single item

curl --insecure https://localhost:5202/api/glossary/MVC

3) Creating an item

curl --insecure -X POST -d "{\"term\": \"MFA\", \"definition\":\"An authentication process.\"}" -H

"Content-Type:application/json" https://localhost:5202/api/glossary


4) Update Item

curl --insecure -X PUT -d "{\"term\": \"MVC\", \"definition\":\"Modified record of Model View 

Controller.\"}" -H "Content-Type:application/json" http://localhost:5202/api/glossary

5) Delete Item

curl --insecure --request DELETE --url http://localhost:5202/api/glossary/openid

PRACTICAL-3: WORKING WITH DOCKER

Step-1: Create Docker Hub account (sign up).

Step-2: Login to https://labs.play-with-docker.com/
Click on start.

Step-3: Add new instance.

Step-4: Perform following:

Method 1:
1) To pull and push images using docker. 
Command to check docker version. 

docker –version

2) To pull readymade image
Command:

docker pull rocker/verse

3) To check images in docker 
Command: docker images

Now Login to docker hub and create repository

Click on the Create button. 

Now check repository created.

To login to your docker account 

docker login –username=kbdocker11

password:

Command: To tag image

docker tag fd553ed661ad kbdocker11/repo1:firsttry

Note: here fd553ed661ad this is image ID which you can get from docker img

Command: to push image to docker hub account 

docker push kbdocker11/danielrepo1:firsttry
Check it in docker hub now.
Click on tags and check.


Method 2:
Build an image then push it to docker and run it

Command: to create docker file

1. cat > Dockerfile <<EOF

2. FROM busybox

3. CMD echo "Hello world! This is my first Docker image."

4. EOF

Command: To build image from docker file. 

docker build –t kbdocker11/repo2 

Command: To check docker images. 

docker images

Command: To push image to docker hub. docker

push kbdocker11/repo2

Now check it on docker hub

Command: To run docker image. 

docker run kbdocker11/repo2


PRACTICAL-4: Installing software packages on Docker

Pre-Requisites:

1. Open Windows Firewall

2. Click on Advanced Security

3. Click on Inbound Rules

4. Create a New Rule

a. Which type of rule would you like to create port.

b. Does this rule apply to the local ports or specific local ports.

c. Select Specific local ports - 80.

d. What action should be taken when a connection matches the specified conditions? - Allow the 
connection

e. When does this apply? - Domain, Private, Public

f. Name: ReportServer

g. Description: ReportServer

Step 1: Enter the following Commands.

a) docker pull nginx nginx: nginx is the image which is already available in docker

b) docker run -it-name-webapp -d -p 80:80 nginx: Create a webapp and run it with nginx image on port 80

Step 2: Click on Port and enter 80 in the dropdown window and click OK.

Step 3: Enter the below command to enter bash shell and then open port 80. docker exec -it WebApp bash
Cd/usr/share/nginx/html
Echo "Hello Welcome to updated nginx Page."> index.html 
exit

Step 4: List all the running containers: docker ps

Step 5: Create another container in Docker: webappl 

Docker run -it --name=webapp1 -d -p 80:80 nginx:

Step 6: Click on port and enter 80 in the dropdown and click ok.


PRACTICAL-5: Working with Docker volumes and networks

Problem: Updates made in one container are not reflected into another container. 

Solution: Volume

Updates made in one container within the volume will be reflected in all the containers of that volume.

Step 7: Creation of Volume(MyVolume)

Command:

a) docker volume create MyVolume
b) docker volume is
c) docker volume inspect MyVolume
d) docker stop WebAppl

Step 8: Create a container (WebApp 2 ) inside the container MyVolume

docker run -d-name = WebApp2-mount source-MyVolume,destination=/usr/share/nginx/html -p 80:80 

nginx

Step 9: Enter the below commands:

a) ls/

b) cd /var/lib/docker

c) ls

d) cd volumes

e) ls

f) cd MyVolume

g) Is

h) cd_data

Step 10:Edit the index file with the below content to "Display the content on the Webpage."

Open Port 80

Step 11: Stop the above container (WebApp2) and Create another container within the volume 
(MyVolume)

Open port 80

Output: The edits made in one container of the volume will be reflected in all the containers of that volume


PRACTICAL 06 Working with Circle CI for continuous integration

Create a repository:

1. Log in to GitHub and begin the process to create a new repository.

2. Enter a name for your repository (for example, CircleCi).

3. Select the option to initialize the repository with a README file.

4. Finally, click Create repository.

5. There is no need to add any source code for now.

Login to Circle CI https://app.circleci.com/ Using GitHub Login, Once logged in navigate to Projects.

Set up CircleCI

1. Navigate to the CircleCI Projects page. If you created your new repository under an organization, you 
will need to select the organization name.

2. You will be taken to the Projects dashboard. On the dashboard, select the project you want to set up 
(CircleCi).

3. Select the option to commit a starter CI pipeline to a new branch, and click Set Up Project. This will 
create a file

4. .circleci/config.yml at the root of your repository on a new branch called circleci-project-setup.

Your First Pipeline

On your project's pipeline page, click the green Success button, which brings you to the workflow that 
ran

(say-hello- workflow).

Within this workflow, the pipeline ran one job, called say-hello. Click say-hello to see the steps in this 
job:

· Spin up environment

· Preparing environment variables

· Checkout code

· Say hello

Now select the "say-hello-workflow" to the right of Success status column


PRACTICAL 07 Creating Backing Service with ASP.NET Core.

Login in to Play-With-Docker 

Start typing following commands

Step 1: Command :

docker run -d -p 5000:5000 -e PORT=5000 \

-e LOCATION URL=http://localhost:5001 \

dotnetcoreservices/teamservice:location

Step 2: Command: to run location service

docker run -d -p 5001:5001 -e PORT=5001 dotnetcoreservices/locationservice:nodb

Step 3: Command: to check running images in docker $docker images

Step 4: Command: to create new team

curl -H "Content-Type:application/json" -X POST -d \

'{"id":"e52baa63-d511-417e-9e54-7aab04286281", "name":"KC"}' http://localhost:5000/teams

Step 5: Command: curl http://localhost:5000/teams/e52baa63-d511-417e-9e54-7aab04286281

Step 6: Command: to add new member to team

curl -H "Content-Type:application/json" -X POST -d \

'{"id":"63e7acf8-8fae-42ce-9349-3c8593ac8292", "firstName":"Mitali", "lastName":"Vishwekar"}' 

http://localhost:5000/teams/e52baa63-d511-417e-9e54-7aab04286281/members

Step 7: Command: To confirm member added

curl http://localhost:5000/teams/e52baa63-d511-417e-9e54-7aab04286281

Step 8: Command: To add location for member

curl -H "Content-Type:application/json" -X POST -d \

'{"id":"64c3e69f-1580-4b2f-a9ff-2c5f3b8f0e1f", "latitude":12.0,"longitude":12.0,"altitude":10.0, 

"timestamp":0,"memberId":"63e7acf8-8fae-42ce-9349-3c8593ac8292"}' 

http://localhost:5001/locations/63e7acf8- 8fae-42ce-9349-3c8593ac8292

Step 9: Command : To confirm location is added in member

curl http://localhost:5001/locations/63e7acf8-8fae-42ce-9349-3c8593ac8292


PRACTICAL 08 Working with Kubernetes

Step 1 : Add a new Instance

Step 2 : Create master node and create a Cluster Using the following commands

Master: kubeadm init --apiserver-advertise-address $(hostname -i) --pod-network-cidr 10.5.0.0/16

Step 3: Cluster: kubectl apply -f https://raw.githubusercontent.com/cloudnativelabs/kube-

router/master/daemonset/kubeadm-kuberouter.yaml

Step 4: You Can Create worker node using the following command given by master node in an another instance

Step 5: The Below Command Can be used to create Containers in the pods in master node/Control plane 

kubectl create deployment my-dep --image=nginx --replicas=3

Basic Commands

View the nodes available - kubectl get nodes 

View the pods available - kubectl get pods

View the Services available - kubectl get services 

Check the version - docker -v
