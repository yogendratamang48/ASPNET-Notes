## Connecting SQLite with .NET Core Console Application  
In this section we will connect to SQLite Database from our .NET Core Console Application using ADO.NET (`Microsoft.Data.SQLite` package which is based on ADO.NET).  
### Steps ###  
1. Create Console Application  
First Create Console Application in your desired folder (For my case `D:\aspnet`). Go to you command prompt and type in following command:  
>`D:\aspnet> dotnet new console -o ConsoleSQLite`  
You will have your .NET Console Standard template in the folder ConsoleSQLite. Now cd into `ConsoleSQLite` Directory.  
1. Add Required Package and Perform Restore  
Add `Microsfot.Data.SQLite` package in your project.
> `D:\aspnet\ConsoleSQLite> dotnet add package Microsoft.Data.SQLite`  
Now you have successfully added this package in your porject. Now perform Restore. 
>`D:\aspnet> dotnet restore`  
Running this command will update your `ConsoleSQLite.csproj` into 
```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Microsoft.Data.SQLite" Version="2.0.0" />
  </ItemGroup>
</Project>
```
_(**Note**: If your application is based on .net core 1, make sure to change Version of `Microsoft.Data.SQLite`  to `1.0.0`  )_
### Creating Database and Table from your application  
You can create a new database(or point to existing one) from .NET Console Application. Lets create our first Method `CreateConnection()` inside `Main()`. The function will Create connection Create new database and the table Student.  
1. Create Connection and provide datasource file or location [var connection=new SqliteConnection("DataSource=nec.db")]
2. Write down your query [ `string query="select * from Student" `]
3. Create your command object using connection [ `var command =  connection.CreateCommand()]
4. Pass query to the command
command.CommandText=query;
4. Open Connection [ connection.Open() ]
5. Execute you command:
command.ExecuteNonQuery();
4. Perform Read Operation using DataReader if needed.
```cs
private static void CreateConnection()
        {
           using (var connection=new SqliteConnection("DataSource=abc.db"))
           {
               string query = "CREATE TABLE Student("
                            +"StudentID INT PRIMARY KEY NOT NULL," 
                            + "FullName TEXT NOT NULL,"
                            + "Roll TEXT NOT NULL, Age INT)";
               // Create New Command Object using the connection.
               var command=connection.CreateCommand();
               // Send the query to commandText property
               command.CommandText=query;
               //Open Connection
               connection.Open();
               //Execute your command
               command.ExecuteNonQuery();
        }
```
1. Inserting Data  
Lets Create Student Class with equivalent to table `Student`.
```cs
public class Student
    {
        public int StudentID { get; set; }
        public string FullName {get;set;}
        public string Roll { get; set; }
        public int Age { get; set; }
    }
```
Now We Create Function `AddStudent()` to add student Object in the database. We will follow same steps as we did in `CreateConnection()` method.
```cs
    private static void AddStudent(Student s)
        {
            using (var connection=new SqliteConnection("DataSource=abc.db"))
            {
               // Create New Command Object using the connection.
                var command=connection.CreateCommand();
                // Create your Query
                string query = "INSERT INTO Student(StudentID, FullName, Roll, Age)"
                               + " VALUES(" + s.StudentID +","
                               + "'"+ s.FullName +"'"+ ","
                               + "'"+ s.Roll + "'"+ ","
                               + s.Age
                               + ");";
               // Send the query to commandText property
                command.CommandText=query;
               //Open Connection
                connection.Open();
                // Execute your command
                command.ExecuteNonQuery();
                Console.WriteLine("Student is Inserted");
            }
        }
```
Now our function for inserting Student data is ready. We will create Student Object and save it using the function.
```cs
 // Create New Student Object
            Student ashish=new Student();
            ashish.FullName="Ashis Thapamagar";
            ashish.Age=22;
            ashish.Roll="NEC-014-407";
            ashish.StudentID=7;
            // Similarly Create Other Students
            AddStudent(ashish);
```

1. Reading Data  
Now we have data in our database. In order to read them, We need DataReader. We will return those data in List object.
```cs
private static List<Student> GetStudents()
        {

            using (var connection=new SqliteConnection("DataSource=abc.db"))
            {
               // Create New Command Object using the connection.
                var command=connection.CreateCommand();
                // Create your Query
                string query = "SELECT StudentID, FullName, Roll, Age FROM Student";
               // Send the query to commandText property
                command.CommandText=query;
               //Open Connection
                connection.Open();
                // Execute your command
                // Since we are Reading operation We need DataReader.
                var reader=command.ExecuteReader();
                List<Student> lstStudents=new List<Student>();
                while (reader.Read())
                {
                //Create Stuent object
                 Student s=new Student();
                 s.StudentID=Convert.ToInt32(reader["StudentID"]);
                 s.FullName=Convert.ToString(reader["FullName"]);
                 s.Age=Convert.ToInt32(reader["Age"]);
                 s.Roll=Convert.ToString(reader["Roll"]);
                 //Add this student to List
                 lstStudents.Add(s);
                }
                return lstStudents;
            }
        }
```
1. Updating Data
1. Deleting Data