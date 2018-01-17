## Forms and HTML Helpers
* A form is a container for input elements: buttons, checkboxes, and more. Input elements in a form enable a user to enter information into a page and submit information to a server.
* There are two main attributes of a form tag: the `action` and the `method`
* `action` attribute tells a web browser `where` to send the information.
* `method` attribute tells the browser whether to use HTTP POST or HTTP GET when sending the information. Default value is **HTTP GET**

Example:  
```html
<form action='/Student/Create' method="post">
  <input name="fullname" type="text" />
  <input type="submit" value="Submit" />
</form>
```
### HTML Helpers
These are methods to make views easy to author. Most of them output HTML markup.  
Some HTML Helpers:
* BeginForm  
This helps to build a robust form. Example:
```html
@using (Html.BeginForm("Create",  "Student", FormMethod.Get)) {
  <input name="fullname" type="text" />
  <input type="submit" value="Submit" />
}
```
* Validation Helpers
    * Html.ValidationSummary  
This displays unordered list of all validation errors in the `ModelState` dicitionary.
    * @Html.ValidationMessage
    When an error exists for a particular field in the `ModelState` dicitionary, you can use `ValidationMessage` helper to display that message.
* Input HTML Helpers  
    * @Html.TextBox  
    `TextBox` helper renders an input tag with the type attribute set to `text`. Example:
    >`@Html.TextBox("fullname", Model.FullName)`
    results
    >`<input id="fullname" name="fullname" type="text" />`
    * @Html.TextArea  
    This will render `<textarea>` element for multiline entry.
    * @Html.Label  
    This return `<label />` element using the string parameter to determine rendered text and for attribute value.
    * @Html.DropDownList and @Html.ListBox  
    Both of these return `<select />` element. `DropDownList` allows you to select single element while `Listbox` allows you to select multiple values.
* Strongly Typed Helpers  
with strongly typed helpers, you pass a lambda expression to specify a model property for rendering.
They have same name as other helpers but with `For` suffix. Examples: `@Html.TextBoxFor`, `@Html.LabelFor`, `@Html.DropDownListFor` etc.

