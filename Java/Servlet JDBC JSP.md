
## JDBC

JDBC = Java Database Connectivity
We will use the JDBC API for the connection between the Java Application and the Database. Because Java does not know how to communicate with MySQL and MySQL does not know how to communicate with Java.

## Steps for DB Connection

1. Load and Register the driver(Translator)  = basically the drivers work as a translator between the Java Application and the Database. Download and add `mysql.connector.jar` else error will come.

```java
class.forName("com.mysql.cj.jdbc.Driver");
```

2. Create Connection(Read) = using this we can make connection between the database and the java application.                                                             MySQL database URL = `jdbc:mysql://localhost:3306/databaseName`

```java
Connection con = DriverManager.getConnection("url","username","password");
```

3. Create Statement = using this we can make data interchange or can manipulate data between the database and the java application.

```java
PreparedStatement ps = con.prepareStatement("Sql query");
// we can also use create statement
```

4. Execute SQL statements = when the data reaches in the database then we need to execute these statements.

```java
ResultSet -> ps.executeQuery(); // select query
int ->  ps.executeUpdate(); // insert, update, delete query
```

5.  Process the result
6. Close the connection. 

```java
ps.close();
con.close();
```

```java
package in.sp.test;

import java.sql.*;

public class InsertTest {
    public static void main(String[] args) throws Exception {
        // Load MySQL JDBC Driver
        Class.forName("com.mysql.cj.jdbc.Driver");
        System.out.println("✅ JDBC Driver Loaded Successfully.");

        // Connect to the database
        Connection con = DriverManager.getConnection(
            "jdbc:mysql://localhost:3306/db?useSSL=false", "root", "2314");
        System.out.println("✅ Connection to the database established.\n");

        // ----------------------------
        // 1. INSERT USING PreparedStatement (hardcoded values)
        // ----------------------------
        String query1 = "INSERT INTO register(name, email, password, gender, city) VALUES (?, ?, ?, ?, ?)";
        PreparedStatement ps1 = con.prepareStatement(query1);
        ps1.setString(1, "Saif Ali Khan");
        ps1.setString(2, "saifalikhan@gmail.com");
        ps1.setString(3, "Saif");
        ps1.setString(4, "Male");
        ps1.setString(5, "Kanpur");

        int rows1 = ps1.executeUpdate();
        System.out.println(rows1 > 0
            ? "✅ Record inserted using PreparedStatement (hardcoded values)."
            : "❌ Insert failed using PreparedStatement (hardcoded).");

        // ----------------------------
        // 2. INSERT USING Statement (not recommended)
        // ----------------------------
        Statement stmt = con.createStatement();
        String query2 = "INSERT INTO register(name, email, password, gender, city) " +
                        "VALUES ('Kareena Kapoor', 'kareena@gmail.com', 'Kareena', 'Female', 'Mumbai')";
        int rows2 = stmt.executeUpdate(query2);
        System.out.println(rows2 > 0
            ? "✅ Record inserted using Statement."
            : "❌ Insert failed using Statement.");

        // ----------------------------
        // 3. INSERT USING PreparedStatement with variables
        // ----------------------------
        String name = "Shah Rukh Khan";
        String email = "srk@gmail.com";
        String password = "SRK";
        String gender = "Male";
        String city = "Mumbai";

        String query3 = "INSERT INTO register(name, email, password, gender, city) VALUES (?, ?, ?, ?, ?)";
        PreparedStatement ps3 = con.prepareStatement(query3);
        ps3.setString(1, name);
        ps3.setString(2, email);
        ps3.setString(3, password);
        ps3.setString(4, gender);
        ps3.setString(5, city);

        int rows3 = ps3.executeUpdate();
        System.out.println(rows3 > 0
            ? "✅ Record inserted using PreparedStatement with variables."
            : "❌ Insert failed using PreparedStatement with variables.");

        // ----------------------------
        // Display all records in the table
        // ----------------------------
        System.out.println("\n--- 📄 Records in 'register' Table ---");
        PreparedStatement psFetch = con.prepareStatement("SELECT * FROM register");
        ResultSet rs = psFetch.executeQuery();

        while (rs.next()) {
            System.out.println(
                rs.getString("name") + " | " +
                rs.getString("email") + " | " +
                rs.getString("password") + " | " +
                rs.getString("gender") + " | " +
                rs.getString("city")
            );
        }

        // Close connection
        con.close();
        System.out.println("\n✅ Database connection closed.");
    }
}
```

In the above example we can see that:
1. First we loaded the driver.
2. we made connection with the database by provided the databse url, username and password. not the useSSL=false will not check the servers identitity verificaiton.
3. next we have taken a variable String name.
4. then we are going to add the query to insert into the db we can also use the positional parameters. ? ? ? ? ? and we can also use '"+name+"' like this or can directly pass values.
5. executeUpdate() will execute the query passde and will return an integer value greater than 0
6. then we close the connection.

You can see that we can use preparedStatement or createStatement as well as there are three ways to insert the values in to the database and also you can see that we can also log the data in the databse using resultset as well

Now to update we just need to change the query that is passed
```java
package in.up.test;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;

public class UpdateTest {
	public static void main(String[] args) throws Exception{
		
		// load the driver
		Class.forName("com.mysql.cj.jdbc.Driver");
		System.out.println("Driver Loaded");
		
		// Connect the Database
		Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/db?useSSL=false","root","2314");
		System.out.println("Databse Connected");
		
		// Update a value in the table
		PreparedStatement ps = con.prepareStatement("UPDATE register SET city=? WHERE email=?");
		ps.setString(1, "Kanpur");
		ps.setString(2, "srk@gmail.com");
		int i = ps.executeUpdate();
		
		if(i > 0) {
			System.out.println("Updated");
		} else {
			System.out.println("failed");
		}
		
		// Delete query
		PreparedStatement ps1 = con.prepareStatement("DELETE FROM register WHERE name=?");
		ps1.setString(1, "Shah Rukh Khan");
		int j = ps1.executeUpdate();
		
		if(j > 0) {
			System.out.println("Deleted");
		} else {
			System.out.println("Failed");
		}
		con.close();
		}
}
```

This was basic CRUD for jdbc with the databse MySQL, there is also something like transactions where you can execeute more than querries if something happens then commit other wise rollback.

-----

## Lets Have a look at servlets

They are server side technology which is used to process and handle request from the client and give a dynamic response.

We have servers, we can have hardware servers and software servers(virtual,vm), but right now we should discuss about web servers and application servers, we also have game server and many more.

Web server = Apache tomcat, Nginx

we use apache tomcat with servlets

we have a lot of containers inside apache tomcat web server
- servlet container
- jsp container
- security container
- websocket container
- JNDI container

what ever servlet class file we make will be deployed and managed by the apace tomcat server. and checks what type of request is it, and the servlet file is handled by the servlet container and then after processing dynamic response will be generated. either dynamic or static and then response

version of apache tomcat i used was 9 and eclipse 2023 06 
then we can setup that in server form the preferences and just add the directory where the server was installed it will automatically take the versoin and then we have to create a server remember to remove the port -1 from the conf service file

and then we can create a dynamic web project and run using the server

the hierarchy

Servlet -> only to create the lifecycle methods in servlet

GenericServlet -> it is used to create a non protocal based requests 

HttpServlet -> it is for Http protocol 

Servlet is a interface and it is implemented by GenericServlet and then both GenericServlet and HttpServlet are classes we need to extended and HttpServlet inherits GenericServlet

some commonly used hhtp methods
get, post, head, put, delete
get = get method is used to retreive info from the given server using the given url

### 🔍 Summary Table

|HTTP Method|Servlet Method|Use Case|
|---|---|---|
|GET|doGet()|Read / fetch data|
|POST|doPost()|Submit / create data|
|PUT|doPut()|Update existing resource|
|DELETE|doDelete()|Delete a resource|
|HEAD|doHead()|Check metadata (no body)|

resource here is any type of data that can be accessed or manipulated using url

### 🔧 Why Override?

Because the default implementation in `HttpServlet` **does nothing** or **returns an error** (like 405 Method Not Allowed).

So, to handle actual logic like fetching data, saving a form, deleting a user, etc., **we must override** the appropriate method.

when ever we create servlet we have to create a deployment descriptor file
web.xml probably => 

HttpServlet is the most used so we can use something like this 
```java
package in.sp.backend;

import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class MyServlet extends HttpServlet{
	/**
	 * 
	 */
	private static final long serialVersionUID = 1L;

	@Override
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		PrintWriter printWriter = response.getWriter();
		printWriter.print("Saif ALI khan");
	}
}
```

we also have to setup the deployment descriptor file here 

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
		 xmlns="http://xmlns.jcp.org/xml/ns/javaee" 
		 xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd" 
		 id="WebApp_ID" 
		 version="4.0">
		 <servlet>
			 <servlet-name>myservlet</servlet-name>
			 <servlet-class>in.sp.backend.MyServlet</servlet-class>
		 </servlet>
		 <servlet-mapping>
			 <servlet-name>myservlet</servlet-name>
			 <url-pattern>/aaa</url-pattern>
		 </servlet-mapping>
</web-app>
```
When a client sends an HTTP request to `/aaa`, the server:

1. Looks up the URL pattern in `<servlet-mapping>`.
    
2. Finds it’s linked to servlet-name `myservlet`.
    
3. Finds the matching `<servlet>` definition.
    
4. Instantiates the class `in.sp.backend.MyServlet`.
    
5. Invokes its `doGet()` or `doPost()` method based on the HTTP method.

the container or the server that does this all is apache tomcat

## Servlet lifecycle

- **Client Request:**
    
    - A client (e.g., browser or application) sends an HTTP request to the server.
        
- **Server Receives Request:**
    
    - The **web server (e.g., Apache Tomcat)** receives the request and looks for the appropriate servlet mapping in the `web.xml` or through annotations (`@WebServlet`).
        
- **Servlet Loading & Instantiation (Only Once):**
    
    - If the servlet is not already loaded:
        
        - The server loads the servlet `.class` file into memory.
            
        - An instance (object) of the servlet is created using **reflection**.
            
- **Initialization (Only Once):**
    
    - The server calls the **`init()`** method on the servlet instance.
        
    - This method is called **only once** during the servlet's lifecycle to initialize resources (e.g., DB connections, config).
        
- **Request Handling (Multiple Times):**
    
    - For each client request:
        
        - A **new thread** is spawned.
            
        - The **`service()`** method is invoked.
            
        - Based on the request type:
            
            - `service()` delegates to `doGet()`, `doPost()`, `doPut()`, etc.
                
    - This part supports **multithreading**: one servlet instance, multiple threads.
        
- **Destruction (Only Once):**
    
    - When the servlet is being taken out of service (e.g., server shutdown or redeployment):
        
        - The **`destroy()`** method is called once.
            
        - Used to release resources like closing DB connections, stopping background tasks, etc.
            
- **Finalization (Optional, Not Reliable):**
    
    - Java's `finalize()` method **may** be called by the **garbage collector** when the servlet object is collected.
        
    - Not guaranteed, and generally avoided in favor of explicit cleanup in `destroy()`.

## Web.xml

Deployment descriptor file when we deploy project we provide its every description inside the web.xml 


what servlet file we have to map can be done using this file, this is called servlet mapping or servlet config, according the request what servlet should be executed
`
```
<web-app>
<servlet-mapping>
<servlet>
<servlet-name>
<url-pattern>
<servlet-class>
```

we create the web.xml in side web-app then inside the WEB-INF where we add html files, jsp files and many more 
but in the latest versions it is not necessary to have the deployment descriptor we can use annotations now

one such annotation is @Web-Servlet("/url")

just need to match this inside the link in an html file without slash url like this.


# HttpServletRequest and HttpServletResponse

getParameter, getCookies, getSession, getMethod, getAttributes, getHeader

getWriter(), sendError(), sendStatus, sendHeader, sendcontentlenght, sendredirect,

# Get post method

get method sends data through the resource url and thus it is not secured and post method sends data through the http message body and thus is more secured

for get data is visible in the url and not the case with the post method we can send very less data using get request beccause data is transfered using url maximg 2048 characters

we can send more data using Post because we send thorugh message body

post method cannot be cached but get can be cached

same get request can be bookmarked and post method cannot be bookmarked

The **message body** is the part of an HTTP request or response that contains the **actual data being sent** — such as form inputs, JSON, XML, or file contents.

- **GET** is faster for **read-only** operations.
    
- **POST** is better for **sensitive or large data** and when you want to **change something on the server**.

|   |   |
|---|---|
|**Cache**|A saved version of a page so it loads faster later|

|   |   |
|---|---|
|**Bookmark**|A shortcut to return to a web page quickly|

we can use the service method and pass the annotation webservlet with the url map from the html form or we can use dopost or do get respectively with the same annotation

## sendRedirect()

just get the parameter value from the form that is from the input fields name and then use httpServlerResponse resp.sendRedirect() and pass the redirect url like for the google we pass the .com url full + the search?q= 

## Request Dispatcher

we also have a RequestDispatcher rd = req.RequestDispatcher("/profile.jsp")

we can use resp.setContentType("text/html");
and the printwriter as well using if else in side them 

we have forward and include as well in this 

| Feature         | `forward(req, resp)`                           | `include(req, resp)`                         |
| --------------- | ---------------------------------------------- | -------------------------------------------- |
| Output Control  | Transfers control, only target writes response | Caller and target both write to the response |
| Client URL      | Stays the same                                 | Stays the same                               |
| Use After Write | **Not allowed** after output is committed      | Allowed at any time                          |
| Control Flow    | Stops in caller, continues in callee           | Returns to caller after execution            |
