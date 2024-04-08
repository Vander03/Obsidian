Persistence in kava refers to the usage of a database to store data between sessions. This is achieved in Java using SQL and facilitated by the Java Database Connectivity (JDBC) API.

## Structured Query Language (SQL)
SQL is used to create, read, update and delete (CRUD) records in a database. In relational databases, data is stored in tables, which are made up of attributes (columns) and records (rows).

The relations between tables are defined by **primary** and foreign **keys**. A **primary** key is a unique identifier for a record in a table, and a **foreign** key is a reference to a primary key in another table. Considering table`transactions`and`people`:

**people**

| id  | name          | bankBalance |
| --- | ------------- | ----------- |
| 1   | John Howard   | 10,000      |
| 2   | Peter Beattie | 5,000       |
| 3   | Tony Abbott   | 12,000      |
| 4   | Kevin Rudd    | 63,000      |
**transactions**

| fromId | toId | amount | timestamp           |
|--------|------|--------|---------------------|
| 1      | 2    | 500    | 2022-01-01 12:00:00 |
| 3      | 4    | 1000   | 2022-01-01 12:00:01 |
| 2      | 3    | 2000   | 2022-01-01 12:00:02 |
| 4      | 1    | 200    | 2022-01-01 12:00:03 |

Here, `fromId` and `toId` columns are foreign keys that are reference to the`id`of people in the `people` table, meaning that person with `id=1` is transferring money to person of `id=2`. The code used to create these tables is shown here:

```SQL
CREATE TABLE people (
    id INTEGER PRIMARY KEY,
    name VARCHAR,
    bankBalance INTEGER
);

CREATE TABLE transactions (
    fromId INTEGER,
    toId INTEGER,
    amount INTEGER,
    timestamp DATETIME,
    FOREIGN KEY (fromId) REFERENCES people(id),
    FOREIGN KEY (toId) REFERENCES people(id)
);
```

Some common SQL commands include:

| Command           | Description                           |
| ----------------- | ------------------------------------- |
| `SELECT`          | Retrieves data from a table.          |
| `INSERT`          | Adds new records to a table.          |
| `UPDATE`          | Modifies existing records in a table. |
| `DELETE`          | Removes records from a table.         |
| `CREATE TABLE`    | Creates a new table.                  |
| `ALTER TABLE`     | Modifies an existing table.           |
| `DROP TABLE`      | Deletes a table.                      |
| `CREATE DATABASE` | Creates a new database.               |
| `ALTER DATABASE`  | Modifies an existing database.        |
| `DROP DATABASE`   | Deletes a database.                   |

### Retrieve Data
```SQL
/* retrieves all data from the `people` table */
SELECT * FROM PEOPLE

/* selects the name and bankBalance from the people table, where the bankBalance is greater than 10000 */
SELECT name, bankBalance FROM people WHERE bankBalance > 10000 

```


### Add new records
```SQL
/* adds a new record to the people table */
INSERT INTO people (id, name, bankBalance) VALUES (5, 'Scott Morrison', 20000);

/*  inserts a record into the transactions table */
INSERT INTO transactions (fromId, toId, amount, timestamp) VALUES (1, 5, 1000, '2022-01-01 12:00:00');
```

### Modify Existing Records
```SQL
/* Modifies the vankBalance of the person with id=5 */
UPDATE people SET bankBalance = 25000 WHERE id = 5;
```

### Remove Records
```SQL
/* Removes person with id = 5 from the people table*/
DELETE FROM people WHERE id = 5;
```

## Java Database Connectivity (JDBC)

### The Connection Interface
The connection interface is the first step to working with a database as it represents a connection to a database, and provides methods to create **Statement** and **PreparedStatement** objects as well as methods to commit and rollback translations.

It is convenient to have a globally accessible connection object, so that it can be used throughout the application. This is normally achieved by creating a Connection object in a separate class, and providing methods to retrieve and close the connection.

The following code shows how to create a connection to a database called `database.db` in the root directory of the project using JDBC

```Java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class DatabaseConnection {
    /**
    * The singleton instance of the database connection.
    */
    private static Connection instance = null;
    /**
    * Constructor intializes the connection.
    */
    private DatabaseConnection() {
        String url = "jdbc:sqlite:database.db";
        try {
            instance = DriverManager.getConnection(url);
        } catch (SQLException sqlEx) {
            System.err.println(sqlEx);
        } catch (IOException ex) {
            ex.printStackTrace();
        }
    }
    /**
    * Provides global access to the singleton instance of the database connection.
    * @return a handle to the singleton instance of the database connection.
    */
    public static Connection getInstance() {
        if (instance == null) {
            new DatabaseConnection();
        }
        return instance;
    }
}
```

Using this, other classes and methods can use the `getInstance()` method to retrieve the connection and use it to interact with the database. For e.g:

Create a table of `bankAccounts` with `id`, `name` and `bankBalance` columns:

```Java
import java.sql.Connection;
import java.sql.SQLException;
import java.sql.Statement;

public class Main {
    public static void main(String[] args) {
        Connection connection = DatabaseConnection.getInstance();
        try {
            Statement statement = connection.createStatement();
            statement.execute("CREATE TABLE IF NOT EXISTS bankAccounts (id INTEGER PRIMARY KEY, name VARCHAR, bankBalance INTEGER)");
            connection.close();
        } catch (SQLException sqle) {
            System.err.println(sqle);
        }
    }
}
```

### Statements
When a **connection** has been established, it can be used to execute **statements**. There are 3 types of statements in JDBC:
- The **statement** interface represents a basic SQL statement
- The **preparedStatement** sub-interface represents precompiled SQL statement which can offer improved performance and convenience
- The **CallableStatement** sub-interface allows JDBC programs access to stored procedures within the database itself, offering even more improved performance. **However, not all databases support stored procedures (SQLite doesn't)**

##### Create a table:
```Java
Statement stmt = connection.createStatement();
String sql = "CREATE TABLE bankAccounts " +
             "(id INTEGER PRIMARY KEY AUTOINCREMENT," +
             " firstName VARCHAR NOT NULL, " + 
             " lastName VARCHAR NOT NULL, " + 
             " bankBalance INTEGER NOT NULL)";
stmt.executeUpdate(sql);
```

##### Insert a record
**Method 1: Using statement object**
```Java
stmt = connection.createStatement();
sql = "INSERT INTO bankAccounts (firstName,lastName,bankBalance) " +
      "VALUES ('John', 'Doe', 10000)";
stmt.executeUpdate(sql);
```

**Method 2: Using a preparedStatement object:**
```Java
String firstName = "Jane";
String lastName = "Doe";
int bankBalance = 20000;

PreparedStatement pstmt = connection.prepareStatement("INSERT INTO bankAccounts (firstName,lastName,bankBalance) VALUES (?,?,?)");
pstmt.setString(1, firstName);
pstmt.setString(2, lastName);
pstmt.setInt(3, bankBalance);
pstmt.executeUpdate();
```

##### Update a record
```Java
int newBalance = 30000;
int id = 1;

pstmt = connection.prepareStatement("UPDATE bankAccounts SET bankBalance = ? WHERE id = ?");
pstmt.setInt(1, newBalance);
pstmt.setInt(2, id);
pstmt.executeUpdate();
```

##### Delete a record
```Java
id = 1;

pstmt = connection.prepareStatement("DELETE FROM bankAccounts WHERE id = ?");
pstmt.setInt(1, id);
pstmt.executeUpdate();
```

##### Select Records
**Scenario 1: Query All Records**
```Java
stmt = connection.createStatement();
ResultSet rs = stmt.executeQuery( "SELECT * FROM bankAccounts;" );
while ( rs.next() ) {
   int id = rs.getInt("id");
   String firstName = rs.getString("firstName");
   String lastName = rs.getString("lastName");
   int bankBalance = rs.getInt("bankBalance");
   System.out.println( "ID = " + id );
   System.out.println( "FIRST NAME = " + firstName );
   System.out.println( "LAST NAME = " + lastName );
   System.out.println( "BANK BALANCE = " + bankBalance );
   System.out.println();
}
```

**Scenario 2: Query records with a condition**
```Java
int minBalance = 15000;
pstmt = connection.prepareStatement("SELECT * FROM bankAccounts WHERE bankBalance > ?");
pstmt.setInt(1, minBalance);
ResultSet rs = pstmt.executeQuery();
while ( rs.next() ) {
   int id = rs.getInt("id");
   String firstName = rs.getString("firstName");
   String lastName = rs.getString("lastName");
   int bankBalance = rs.getInt("bankBalance");
   System.out.println( "ID = " + id );
   System.out.println( "FIRST NAME = " + firstName );
   System.out.println( "LAST NAME = " + lastName );
   System.out.println( "BANK BALANCE = " + bankBalance );
   System.out.println();
}
```

It is also possible to use string concatenation
```Java
int getBalanceForUser(String firstName, String lastName) {
    Statement stmt = connection.createStatement();
    ResultSet rs = stmt.executeQuery(
        "SELECT bankBalance FROM bankAccounts" 
        + "WHERE firstName = '" + firstName 
        + "' AND lastName = '" + lastName 
        + "'"
    );
    if (rs.next()) {
        return rs.getInt("bankBalance");
    }
    return -1;
}
```

### ResultSet
SQL queries for a **ResultSet** object, which represents the data returned from the query. This object has methods to navigate through the data and retrieve data from the columns.

In essence, a **ResultSet** object is a two-dimensional table of all rows in the database matching the query, and is navigated using the `.next()` method, which moves the cursor to the next row and returns false if there is no more rows.

To retrieve data from the ResultSet you can use the `getXXX(int columnIndex)` or `getXXX(String columnName)`, where XXX is the data in the column. Note the column index **starts from 1, not 0**

| SQL Data Type | Java Data Type     | get Method   |
|---------------|--------------------|--------------|
| BIT           | boolean            | getBoolean   |
| TINYINT       | byte               | getByte      |
| DOUBLE        | double             | getDouble    |
| REAL          | float              | getFloat     |
| SMALLINT      | short              | getShort     |
| INTEGER       | int                | getInt       |
| BIGINT        | long               | getLong      |
| VARCHAR       | String             | getString    |
| TIMESTAMP     | java.sql.Timestamp | getTimestamp |
##### Retrieval using column index:
```Java
Statement stmt = connection.createStatement();
ResultSet rs = stmt.executeQuery("SELECT firstName, bankBalance FROM bankAccounts");
while (rs.next()) {
    String firstName = rs.getString(1);
    int bankBalance = rs.getInt(2);
    // Do something with the data
}
```

##### Retrieval using column name:
```Java
Statement stmt = connection.createStatement();
ResultSet rs = stmt.executeQuery("SELECT firstName, bankBalance FROM bankAccounts");
while (rs.next()) {
    String firstName = rs.getString("firstName");
    int bankBalance = rs.getInt("bankBalance");
    // Do something with the data
}
```

##### Using ResultSet to update fields
As of JDBC 2.0 you can use `updateXXX` methods to update data in the ResultSet.  In order to do so, the createStatement or prepareStatement method must be called with the `ResultSet.TYPE_SCROLL_SENSITIVE` and `ResultSet.CONCUR_UPDATABLE` arguments. Consider the following examples:

```Java
// Adding 1000$ to the bank balance of all bank accounts
Statement stmt = connection.createStatement(
    ResultSet.TYPE_SCROLL_SENSITIVE, 
    ResultSet.CONCUR_UPDATABLE
);
ResultSet rs = stmt.executeQuery("SELECT * FROM bankAccounts");
while (rs.next()) {
    rs.updateInt("bankBalance", rs.getInt("bankBalance") + 1000);
    rs.updateRow();
}
```

```Java
// Adding $1000 to the bank balance of accounts with a balance less than $15000:
int maxBalance = 15000;
PreparedStatement pstmt = connection.prepareStatement(
    "SELECT * FROM bankAccounts WHERE bankBalance < ?",
    ResultSet.TYPE_SCROLL_SENSITIVE,
    ResultSet.CONCUR_UPDATABLE
);
pstmt.setInt(1, maxBalance);
ResultSet rs = pstmt.executeQuery();
while (rs.next()) {
    rs.updateInt("bankBalance", rs.getInt("bankBalance") + 1000);
    rs.updateRow();
}
```

##### Additional requirements for createStatement and prepareStatement

The `createStatement` and `prepareStatement` methods can take two additional arguments, called the `resultSetType` and `resultSetConcurrency`. The `resultSetType` argument specifies the type of the `ResultSet`, and can be one of the following values:

`ResultSet.TYPE_FORWARD_ONLY`: The default type, which allows the cursor to move forward only.
`ResultSet.TYPE_SCROLL_INSENSITIVE`: Allows the cursor to move forward and backward, but does not reflect changes made by others.
`ResultSet.TYPE_SCROLL_SENSITIVE`: Allows the cursor to move forward and backward, and reflects changes made by others.
The `resultSetConcurrency` argument specifies the concurrency of the `ResultSet`, and can be one of the following values:

`ResultSet.CONCUR_READ_ONLY`: The default concurrency, which allows read-only access to the ResultSet.
`ResultSet.CONCUR_UPDATABLE`: Allows read and write access to the ResultSet

### Closing Connections
When operations are finished its a good idea to close it to free the resources. This can be done by calling the `close()` method on the `Connection` object
`connection.close();`

