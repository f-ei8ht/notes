
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

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;

public class InsertTest {
    public static void main(String[] args) throws Exception {
        Class.forName("com.mysql.cj.jdbc.Driver");
        System.out.println("Successfully Loaded");
        
        Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/db?useSSL=false", "root", "2314");
        System.out.println("Connection made to the database successfully");
        
        String name = "Saif Ali Khan";
        PreparedStatement ps =    con.prepareStatement("insert into register values('"+name+"', 'saifalikhan@gmail.com', 'Saif', 'Male', 'Kanpur')");
        // PreparedStatement ps =    con.prepareStatement("insert into register values(?,?,?,?,?)");
        // ps.setString(1, name);
        
        int i = ps.executeUpdate();
        
        if(i > 0) {
            System.out.println("Successfully inserted values into the table: " + i);
        } else {
            System.out.println("Failed: " + i);
        }
        con.close();
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