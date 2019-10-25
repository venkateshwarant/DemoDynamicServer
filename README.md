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
```
cd ~/Downloads/apache-tomcat-9.0.27
```

and run below command to make the .sh file executable.
```
sudo chmod +x ./bin/*.sh
```

Now all the .sh file in tomcat bin directory is executable, you can run ls -al command to see that.
```
ls -al
```

Now you can start the tomcat server by running

```
sh bin/startup.sh
```

You can see all of the above steps in the following image.
![create web project](/src/images/62.png)

4) The default port number in which the tomcat starts is 8080. If you wish to change the default port number then open cong > server.xml

![create web project](/src/images/63.png)

5) Change the content of server.xml from 8080 to 8081 as shown in the image.

![create web project](/src/images/64.png)

6) Then shutdown and start the tomcat server by running the following command.

```
sh bin/shutdown.sh
sh bin/startup.sh
```

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

7) This is how automatically created servlet looks like the below image. Now It may show some compilation errors in eclipse as shown in the image below because we haven't added the servlet jars.

![create web project](/src/images/66.png)


8) To add the required jar, goto File > Configure Build path

![create web project](/src/images/67.png)

9) Then click "add library"

![create web project](/src/images/68.png)

10) Select "Server Runtime", click next

![create web project](/src/images/69.png)

11) Select "Apache Tomcat v9.0", then click finish

![create web project](/src/images/70.png)

12) You can see the newly added libraries for tomcat. Now Click "Apply and close". 

![create web project](/src/images/71.png)

13) Now you can see that all the code written in eclipse is compiled properly and there is no error in our java file.

![create web project](/src/images/72.png)

14) Paste the below content in the servlet file and save it.

```
import java.io.IOException;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import java.io.IOException;
import java.io.PrintWriter;
import java.util.Date;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebInitParam;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class FirstServlet
 */
@WebServlet(description = "My First Servlet", urlPatterns = { "/FirstServlet" , "/FirstServlet.do"}, initParams = {@WebInitParam(name="id",value="1"),@WebInitParam(name="name",value="venkat")})
public class FirstServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;
	public static final String HTML_START="<html><body>";
	public static final String HTML_END="</body></html>";
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public FirstServlet() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		PrintWriter out = response.getWriter();
		Date date = new Date();
		out.println(HTML_START + "<h2>Hi There!</h2><br/><h3>Date="+date +"</h3>"+HTML_END);
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
	}

}
```

15) Click on run icon in eclipse as shown in the image.

![create web project](/src/images/73.png)

16) Select tomcat v9.0 option and click finish

![create web project](/src/images/74.png)

17) Now you can see that the eclipse runs our dynamic web project and deployed it in the tomcat server and it has started the server. we can now access our page by calling http://localhost:8081/DemoDynamicServer/FirstServlet in any browser.

You can also see the web page in the eclipse as shown in the image too.

![create web project](/src/images/75.png)

## Exporting our dynamic web project's war file

Instead of using eclipse for deploying our project, we can create the war file from eclipse, So that we can deploy it in any tomcat server.

Let's look into its procedure.

1) Go to File > Export

![create web project](/src/images/76.png)

2) Select "war file", Then click next.

![create web project](/src/images/77.png)

3) Select the project for which you want to generate .war file and the destination where you want the .war file to be present. Click finish.

![create web project](/src/images/78.png)

4) Your war file will be generated in that specified location.

![create web project](/src/images/79.png)

5) Goto the location where the war file is generated and copy the war file into webapps location.

Then create a folder with same name as of the war file. move the war file to that new directory.

unzip the war file inside this directory.

all the above steps are shown in the below image

![create web project](/src/images/80.png)


6) Then kill if any tomcat is running previously and again start the tomcat server, now you can see that the file is served from here.

![create web project](/src/images/81.png)
