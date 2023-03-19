<h1 align="center">ASP.NET Framework</h1>
<h3 align="center">Utility Framework</h3>
<p align="center">This documentation is all about how to use utility framework in your project</p>

<h1 align="center">Implementation Part</h1>
<p>Firstly, you the developer need to download the given dll file and add reference of this dll to their project file. After that, create your desired model. To demonstrate, here we are going to create product model. Here, inside the table attribute write your table name associated to that model</p>

```c#
[Table("products_tbl")]
public class Product
{
    [Key]
    public int product_id { get; set; }
    public string name { get; set; }
    public long amount { get; set; }
    public int rating { get; set; }
}
```
<p>Then after, we are going to create ApplicationDbContext which will implement DbContext file (present inside Entity framework package) and will act as a brigde between database and api. In dbContext file we are going to list all the models which are present inside the project. Here, we are going to the previously created model i.e. Product.</p>

```c#
public class ApplicationDbContext : DbContext
{
    public DbSet<Product> products { get; set; }   
}
```
<p>After that, we need to create class file inside the controller folder. Name your file according to your model name. Then after, import the using statement and implement the APIHelperController to your controller.</p>

```c#
using Utility.Framework.Generic;

public class ProductController : APIHelperController<Product, ApplicationDbContext>
{
        
}
```
<p>In the above mentioned code pass the Model and ApplicationDbContext class the were created in previous step. In my case Product and ApplicationDbContext</p>

<p>After that, we need the pass the database connection string. For that write the below mentioned code.</p>

```c#
public class ProductController : APIHelperController<Product, ApplicationDbContext>
{
    DbConnectionHelper connectionHelper = new DbConnectionHelper("Database string For Eg: Data Source=servername;Integrated Security=true;Initial Catalog=DbName");
}
```

<p>Congratulations you made it. Now you can run your project and you will be able to see the output mentioned below</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/85151048/225710395-53401abd-f8af-48ba-a913-f60a507ef21c.png" width="100%" title="Result Image">
</p>
