# DemoDynamicServer
Tutorial on creating a dynamic web project and deploying it in a tomcat server.

## Getting Started

First follow https://github.com/venkateshwarant/UAT to install Java and Eclipse in your machine

### Install web development tools in eclipse

1) Launch the Eclipse IDE and from Help menu, click “Install New Software”.

![Install New Software](/src/images/13.png)

2) You will see a dialog window, click “Add” button.

![Web](/src/images/15.png)

3) Type name as you wish, lets take “Oxygen” and type “http://download.eclipse.org/release/oxygen” as location. Click OK.

![Prev web](/src/images/46.png)

4) Select web from the options available as shown in the image

![Prev web](/src/main/47.png)

5) Click Next, It will fetch the details of all the softwares which are needed to be installed in eclipse so as to start developing a web project.

![Prev web](/src/images/48.png)

6) View the softwares to be installed if you want, then click next

![Prev web](/src/images/49.png)

7) Accept the licence agreements and the click finish.

![Prev web](/src/images/50.png)

8) Eclipse will install all the needed softwares, wait for it to complete.

![Prev web](/src/images/51.png)

9) Then restart the eclipse to view the changes.

![Prev web](/src/images/52.png)

## Downloading Tomcat server

1) Download tomcat install package from https://tomcat.apache.org/download-90.cgi page. You can select zip file or tar.gz file. Here I've selected tar.gz file.

Here we are downloading the currently available latest tomcat server (Tomcat version9)

![create web project](/src/images/59.png)

2) After download, unzip the compress file to a local directory.

here is the downloaded tar.gz
![create web project](/src/images/60.png)

I've unzipped it in the same directory where the tar.gz file is present.

![create web project](/src/images/61.png)

3) Then navigate to the unzipped directory. For me unzipped directory is ~/Downloads/apache-tomcat-9.0.27

Therefore
'''
cd ~/Downloads/apache-tomcat-9.0.27
'''

and run below command to make the .sh file executable.
'''
sudo chmod +x ./bin/*.sh
'''

Now all the .sh file in tomcat bin directory is executable, you can run ls -al command to see that.
'''
ls -al
'''

Now you can start the tomcat server by running

'''
sh bin/startup.sh
'''

You can see all of the above steps in the following image.
![create web project](/src/images/62.png)

4) The default port number in which the tomcat starts is 8080. If you wish to change the default port number then open cong > server.xml

![create web project](/src/images/63.png)

5) Change the content of server.xml from 8080 to 8081 as shown in the image.

![create web project](/src/images/64.png)

6) Then shutdown and start the tomcat server by running the following command.

'''
sh bin/shutdown.sh
sh bin/startup.sh
'''

7) You can open any browser and load http://localhost:8081. You can see the default page of Apache as shown in the image

![create web project](/src/images/65.png)

## Creating a new dynamic web project

1) Open Eclipse, goto File > New > Project

![create web project](/src/images/53.png)

2) Select "Dynamic Web project"

![create web project](/src/images/54.png)

3) Give corresponding name of your project and select the location to save the project. Then Click finish

![create web project](/src/images/55.png)

4) Select open perspective 

![create web project](/src/images/56.png)

5) Now your project is created. Go to src inside your project directory and then create a new servlet.

![create web project](/src/images/57.png)

6) Give proper package name and class name as shown in the image.

![create web project](/src/images/58.png)
