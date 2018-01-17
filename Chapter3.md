### Chapter 3 MVC Pattern
#### ASP.NET MVC 
* In 2002, ASP.NET 1.0 was released. Back then ASP.NET and Web Form were thought to be same thing. ASP.NET has always supported two layers of abstraction:
    * System.Web.UI
    * System.Web
* ASP.NET MVC Introduced in 2007 and became mainstream framework for builidng .NET web applications.

#### 3.1 MVC Architecture
* It is important architectural pattern in computer science for many years. It is powerful and elegant means of separating concerns within an applications. These concerns may be data access logic, display logic etc.
* ASPNET MVCE is a framework for building web applications that applies the general Model View Controller pattern to the ASP.NET framework.
* MVC separates application into three main aspects:  
i. Model  
A set of classes that describes the data you are working with as well as business rules for how the data can be changed or manipulated. Models implement application's data domain logic.  
ii. View  
Defines how the application's User Interface(UI) will be displayed  
iii. Controller:  
A set of classes that handles communication from the use, overall application flow, and application-specific logic.
#### 3.2 Controller
##### Role
* Conrollers are responsible for responding to user input, often making changes to the model in response to user input. They are concerned with the flow of application, working with data coming in and providing data going out to the relevant view.
* Rather than having a direct relationship between the URL and a file in a servers's disk, a relationship exists between the URL and a method on a controller class. 
* Theses relationships are described by Action Methods.
* The controller sits infront of every-thing except the routing subsystem.
#### 3.3 Views
* View is what users see when they use your application.
* After controller has executed the appropriate logic for the requested URL, it delegates the display to the view.
* Views are not themselves directly accessible. Instead, a view is always rendered by a controller, which provides the data to the view.
#### ViewData and Strongly Typed Views 
##### Passing data using ViewBag 
* ViewBags are useful if you want to send tiny bit of data from the controller to the view.
* They are can be sent in controller method using ViewBag keyword or in View inside @{ } block.
* Example (Sending data from Controller to View):
>```cs
public ActionResult About()
{
 ViewBag.Message = "Hello Everyone";
 return View();
}
```
* Corresponding View may be:
>```
@{
ViewBag.Title = "Elective";

}
<h2>@ViewBag.Title</h2>
<h2>@ViewBag.Message</h2>
```
##### Disadvantages of ViewBag
* Type Conversion needed
* If used dynamic keyword, IntelliSensce is lost
#### Passing Data using Strongly Typed Views
* Strongly Typed views allows you to pass model object from the controller to the view.
* This gives advantage of IntelliSense, compiler checking.
* You can pass in model via View Overloading in Controller Method
* Example:
>```cs
public ActionResult List()
{
    var students = new List<Student>();
    for (int i=o;i<5;i++)
    {
      students.add(new Student{Name = "Student "+ i});
    }
    return View(students);
}
```
* Corresponding View may be:
>```html
@model IEnumerable<NECProject.Models.Student>
<ul>
@foreach (Student s in Model) {
<li>@p.Name</li>
}
```
##### ViewData and ViewBag
* You can send data from controllers to views using ViewDataDicitionary(specialized dicitionary class) called __ViewData__.
* You can set/read values to the ViewData dicitionary using standard dicitionary sytanx, as follows:
>```cs
ViewData["CollegeName"] = "Nepal Engineering College";
```
* ViewBag is Syntactic sugar(dot[.] notation) that some people prefer over the dicitionary syntax.
* ViewBag is dynamic wrapper around ViewData. It allows you to set values in dot notation like this:
>``` ViewBag.CollegeName = "Nepal Engineering College";```
* Main differences between __ViewBag__ and __ViewData__ are:
    * __ViewBag__ works only when the key you are using is a valid C# indentifier.
    * You can not use __ViewBag__ to access data set by __ViewData__ in following code.
    >```
    ViewData["Key With Spaces"] = "Value of Key";
    ```
    * You can not pass in dynamic values as parameters to extension methods.
    * Example: The following line will fail. To work around this either use `ViewData["Name"]` or cast the value to a specific type: `(string)ViewBag.Name`
    >```
    @Html.TextBox("name", ViewBag.Name)
    ```
#### ViewDataDicitionary
* It is a specialized dicitionary class. It has additional `Model` property that allows you for a specific model object to be abailable to the view
* You can take advantage of strong typing by sending view-specific `Model` from the `Controller`.
#### View Models
* These are view-specific Model class to obtain Strongly Typed Views.
* Suppose you have Student Admission form, you want to bring dropdowns for interested faculties, address districts, completed education etc. General approach is sending main 'Model' from the controller class and others through ViewBag as follows:
>```public ActionResult StudentForm
{
    Student s = new Student();
    ViewBag.Districts = DAL.GetDistricts();
    ViewBag.Faculties = DAL.GetFaculties();
    View(s);
}
```
* Another approach may be to create View-specific model like:
>```
public class StudentFormModel
{
   public IEnumerable<District> districts { get; set; }
   public IEnumerable<Faculty> faculties { get; set; }
   public Student student { get; set; }
}
```
* This model is then passed from controller to view.
* This gives benefits of a strongly typed view without changing `Model` class.
>```public ActionResult StudentForm
{
    StudentFormModel s = new StudentFormModel();
    View(s);
}
```
##### View Engines
* 
#### 3.4 Models
* Models
