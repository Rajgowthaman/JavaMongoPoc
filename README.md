
# Java MongoDB Connection Example

This is a simple Java program to connect to a local MongoDB instance, list all databases, and their collections.

## Code Example

```java
import java.net.UnknownHostException;
import java.util.List;
import java.util.Set;

import com.mongodb.DB;
import com.mongodb.MongoClient;

public class JavaMongoDBConnection {

    public static void main(String[] args) {
        try {
            MongoClient mongoClient = new MongoClient("localhost");

            List<String> databases = mongoClient.getDatabaseNames();

            for (String dbName : databases) {
                System.out.println("- Database: " + dbName);

                DB db = mongoClient.getDB(dbName);

                Set<String> collections = db.getCollectionNames();
                for (String colName : collections) {
                    System.out.println("\t + Collection: " + colName);
                }
            }

            mongoClient.close();

        } catch (Exception ex) {
            ex.printStackTrace();
        }
    }
}
```

## How to Run

1. Ensure MongoDB is running locally on default port 27017.
2. Add MongoDB Java driver dependency to your project. For example, with Maven:

```xml
<dependency>
    <groupId>org.mongodb</groupId>
    <artifactId>mongo-java-driver</artifactId>
    <version>3.12.10</version>
</dependency>
```

3. Compile and run the Java class.

---

Let me know if you want me to help with a build file or more detailed setup instructions!
