# C Sharp And .Net Live Project

## Introduction:
I was also able to gain real-world experience during the C# and .NET Live Project at The Tech Academy. I worked on a Basic MVC 5 Web Application named Vertigo Theatre, which utilized Entity Framework that required both Front(HTML/RAZR, Bootstrap/CSS, JavaScript) and Back-End (C#, JSON) programming strategies and techniques. I was able to complete 3 stories and participated in daily stand-up meetings and weekly code retrospectives. I utilized Azure DevOps with my development team, Visual Studio 2019 as my IDE, SQLServer2019 for our dB, and Discord for communicating with project members and instructors. Clean version control was a crucial element to our project, as I was required to properly create seperate branches, pull the master daily, merge changes into my open branches, and submit pull requests when submitting work into the master. The Live project was a challenge and I feel that I was able to properly demostrate on how to work with a team of developers in a live enviroment.

## Project Layout

The following was our project layout. I was instructed to work on the Rental section, which was essential for users in submitting cost and other information towards our database with prompted input selection boxes.

![image](https://user-images.githubusercontent.com/79550661/136676956-4f34bb8f-6865-4781-97a6-56ccb48b6eea.png)


## Project Story Table of Contents
* [Working with JSON](#working-with-json)
* [Creating My Model](#creating-my-model)
* [Style Create and Edit Pages](#style-create-and-edit-pages)

*Jump to: [Page Top](#c-sharp-and-.net-live-project)*


## Working with JSON

1.) For this assignment, I was tasked in creating a JSON file for storing static data that the team of developers could change in the future.

![image](https://user-images.githubusercontent.com/79550661/136677214-2617dc34-f0d6-4e77-937a-965ca51e8660.png)

2.) I created a JSON file called SiteSettings.json in the main project (which was in the same level as the project's Models, Views, and Controllers folders). In this JSON file, I created a JSON integer called "Copyright" and set the value equal to 2021 for a basic template.

3.) I then created a new C# class in the main project's Models folder called SiteSettings.cs. This class contained an integer property that will be used to deserialize the JSON into.

4.) Then finally, to test if the JSON is being deserialized correctly, I created a method in the SiteSettings class called ReadSiteSettings. This method return void for the time being. The method read the SiteSettings.json file and created a SiteSettings C# object. I utilized breakpoints and the Visual Studio debugger to confirm that the JSON is being deserialized into a SiteSettings object. I utilzed the Startup.cs file and was able to visualize the deserialization for this story.


### Final Story Result:
![image](https://user-images.githubusercontent.com/79550661/136677266-c2dad658-7dd0-4fbc-8908-3fd12d0e9f09.png)
![image](https://user-images.githubusercontent.com/79550661/136677287-b4bcf91a-cade-4b8f-a2b3-2fcd3231b942.png)

*Jump to: [Page Top](#c-sharp-and-.net-live-project)*




## Creating My Model
1.) For this assignment, I utilized and created an Entity Model that produced CRUD pages and demonstrated functionality and that could be saved to the projects database. There were multiple parts of this assignment, which when completed, worked successfully.

2.) First, I created the Rental class as well as the RentalEquipment and RentalRoom classes. These two classes (RentalEquipment and RentalRoom inherited from Rental. When scaffolding CRUD pages/controller, I did not create a new DbContext and instead utilized the DbContext in the IdentityModels.cs file in the main project.

![image](https://user-images.githubusercontent.com/79550661/136677542-f324bba4-7f39-40b7-8e7c-844d06288a24.png)
![image](https://user-images.githubusercontent.com/79550661/136677535-acb65b3f-319e-4938-ab71-21795f6f7578.png)

3.) Thereafter, I was tasked in creating the controller and scaffold the CRUD pages for it. I utilized the MVC 5 Controller with views, utilizing Entity Framework that was installed in the project via NuGet. I created the model and scaffoled the pages within Areas > Rental. 

![image](https://user-images.githubusercontent.com/79550661/136677418-90ac0b3d-9530-484a-b262-2d5d0dbf21bf.png)

4.) After I created the model, I updated the database which created a table in the database via the NuGet Package manager command, 'update-database'. I was then able to use the SQL Server Object Explorer in Visual Studio to check that the table had been created correctly. 
 
5.) Finally, I was able to properly display and create the Index, Create, Details, Delete, and Edit pages. I was able to navigate to each page by typing in the address of the page in the URL. At this time for the assignment, the model Rental could be created, edited, and deleted successfully. RentalEquipment and RentalRooms would be worked on when needed in the future as I was only required to set up Rental.


*Jump to: [Page Top](#c#-and-.net-live-project)*


## Style Create and Edit Pages
1.) For this assignment, I was instructed to style the Create and Edit Pages for the user. The project director solely wanted the Rental section to be displayed.

2.) I added a header above the form with the following text "Create Rental" on a single line.

3.) I then styled the Submit and Back to List buttons (with background color, rounded corners, subtle hover effect, etc.). I included a color distinction between these two buttons and were both centered on the page.

4.) I added placeholders to all input fields. I then was able to place the form in a centered container.

5.) Lastly I styled the input fields' border color to change when clicked. I matched the color changes to match the theme of our website. Then, I was able add color of the input field to change when clicked as well. Both Create and Edit pages contained fluid styling and what the project director needed. One important aspect to mention is that I had to follow writing CSS rule-sets in order prevent existing rule-sets from being overridden accidentally. In my Rent.css page, my styling had to follow a naming convention for new classes and ids that were created to greatly reduce the likelihood of CSS being overridden.


### Create Page
```
@model TheatreCMS3.Areas.Rent.Models.Rental

@{
  ViewBag.Title = "Create";
  Layout = "~/Views/Shared/_Layout.cshtml"; //Add full site layout to Create Page
}
<link href="~/Content/Areas/Rent.css" rel="Stylesheet" type="text/css" />

<h2 class="rental-create--heading">Create Rental</h2>


@using (Html.BeginForm())
{
  @Html.AntiForgeryToken()

  @*@Html.DropDownList("Rentals", new List<SelectListItem>
{
    new SelectListItem { Text = "-- Select Department --", Value = "0", Selected=true},
    new SelectListItem { Text = "Rentals", Value = "1"},
    new SelectListItem { Text = "Rental-Equipment", Value = "2"},
    new SelectListItem { Text = "Rental-Room", Value = "3"},
})*@

  <div id="rental-create--form" class="form-horizontal container pr-0 pt-1">
    <h4 class="rental-create--heading" style="text-align:center">Rental Request Form</h4>
    <hr />
    <div class="flex-column">

      @Html.ValidationSummary(true, "", new { @class = "text-danger" })

      <div class="row justify-content-start col-12">
        <div class="form-group col-12 px-0 justify-content-center">
          @Html.LabelFor(model => model.RentalName, htmlAttributes: new { @class = "control-label col-md-2" })
          <div class="input-group input-group-lg mx-auto col-lg-12">
            @Html.EditorFor(model => model.RentalName, new { htmlAttributes = new { @class = "form-control rental-create--input", @placeholder = "Enter Your Name" } })
            @Html.ValidationMessageFor(model => model.RentalName, "", new { @class = "text-danger" })
          </div>
        </div>
      </div>

      <div class="row justify-content-start col-12">
        <div class="form-group col-12 px-0 justify-content-center">
          @Html.LabelFor(model => model.RentalCost, htmlAttributes: new { @class = "control-label col-md-2" })
          <div class="input-group input-group-lg mx-auto col-lg-12">
            @Html.EditorFor(model => model.RentalCost, new { htmlAttributes = new { @class = "form-control rental-create--input", @placeholder = "Enter Your Total Rental Cost" } })
            @Html.ValidationMessageFor(model => model.RentalCost, "", new { @class = "text-danger" })
          </div>
        </div>
      </div>

      <div class="row justify-content-start col-12">
        <div class="form-group col-12 px-0 justify-content-center">
          @Html.LabelFor(model => model.FlawsAndDamages, htmlAttributes: new { @class = "control-label col-md-3" })
          <div class="input-group input-group-lg mx-auto col-lg-12">
            @Html.EditorFor(model => model.FlawsAndDamages, new { htmlAttributes = new { @class = "form-control rental-create--input", @placeholder = "Enter Any Flaws Or Damages" } })
            @Html.ValidationMessageFor(model => model.FlawsAndDamages, "", new { @class = "text-danger" })
          </div>
        </div>
      </div>

      <div class="row justify-content-center col-12">
        <div class="pr-1">
          @Html.ActionLink("Back to List", "Index", null, new { @class = "btn btn-secondary" })
        </div>
        <div class="form-group">
          <input type="submit" value="Create" class="btn btn-danger" />
        </div>
      </div>
    </div>
  </div>
}


@section Scripts {
  @Scripts.Render("~/bundles/jqueryval")
}
```
### Edit Page
```
@model TheatreCMS3.Areas.Rent.Models.Rental

@{
    ViewBag.Title = "Edit";
    Layout = "~/Views/Shared/_Layout.cshtml"; //Add full site layout to Edit Page
}
<link href="~/Content/Areas/Rent.css" rel="Stylesheet" type="text/css" />

<h2 class="rental-create--heading">Edit Page</h2>


@using (Html.BeginForm())
{
  @Html.AntiForgeryToken()

<div id="rental-edit--form" class="form-horizontal container pr-0 pt-1">
  <h4 class="rental-create--heading" style="text-align:center">Rental Edit Page</h4>
  <hr />

  @Html.ValidationSummary(true, "", new { @class = "text-white" })
  @Html.HiddenFor(model => model.RentalId)

  <div class="row justify-content-center col-12">
    <div class="form-group col-12 px-0">
      @Html.LabelFor(model => model.RentalName, htmlAttributes: new { @class = "control-label col-md-2" })
      <div class="input-group input-group-lg mx-auto col-lg-12">
        @Html.EditorFor(model => model.RentalName, new { htmlAttributes = new { @class = "form-control rental-edit--input" } })
        @Html.ValidationMessageFor(model => model.RentalName, "", new { @class = "text-white" })
      </div>
    </div>

    <div class="form-group col-12 px-0">
      @Html.LabelFor(model => model.RentalCost, htmlAttributes: new { @class = "control-label col-md-2" })
      <div class="input-group input-group-lg mx-auto col-lg-12">
        @Html.EditorFor(model => model.RentalCost, new { htmlAttributes = new { @class = "form-control rental-edit--input" } })
        @Html.ValidationMessageFor(model => model.RentalCost, "", new { @class = "text-white" })
      </div>
    </div>

    <div class="form-group col-12 px-0">
      @Html.LabelFor(model => model.FlawsAndDamages, htmlAttributes: new { @class = "control-label col-md-3" })
      <div class="input-group input-group-lg mx-auto col-lg-12">
        @Html.EditorFor(model => model.FlawsAndDamages, new { htmlAttributes = new { @class = "form-control rental-edit--input" } })
        @Html.ValidationMessageFor(model => model.FlawsAndDamages, "", new { @class = "text-white" })
      </div>
    </div>

    <div class="row justify-content-center col-12">
      <div class="pr-1">
        @Html.ActionLink("Back to List", "Index", null, new { @class = "btn btn-secondary" })
      </div>
      <div class="form-group">
        <input type="submit" value="Save" class="btn btn-danger" />
      </div>
    </div>
  </div>
</div>
}



@section Scripts {
  @Scripts.Render("~/bundles/jqueryval")
}
```
### Styling
```
/*Rental Create and Edit Page Start*/

.rental-create--heading, rental-edit--heading {
    padding: 25px;
    text-align:center;
}

#rental-create--form, #rental-edit--form {
    text-align:center;
    background-color: var(--main-color--light);
    border-radius: 20px;
    box-sizing: border-box;
    height: 500px;
    padding: 20px;
    width: 600px;
    
}

/*Rental Input Field Color Change*/
.rental-create--input:focus, .rental-edit--input:focus {
    opacity: 1;
    border: 2px solid var(--main-color--light);
    background-color: var(--secondary-color);
}

/*Rental Create and Edit Page End*/
```


### Final Story Result:
![image](https://user-images.githubusercontent.com/79550661/136678222-a394955c-4ef1-4b3f-a9c9-581dd8c17159.png)
![image](https://user-images.githubusercontent.com/79550661/136678267-588b222e-6e4e-4b54-8cb6-26a7f7c3bf2f.png)


*Jump to: [Page Top](#c#-and-.net-live-project)*




### Agile Methodologies & Ending Notes:
We used Agile and Scrum as our method of development. I participated in a sprint-planning meeting, daily stand-ups, and a code-retrospective to discuss what worked well and what didn't. During the daily meetings, I had to mention what I worked on the day prior, what we were going to work on the day of, and what roadblocks we were facing. It was a great way to gain soft skills. The meetings held us accountable and even though for most of the Live Project I worked by myself, I still was able to complete the tasks needed for completion. It was also an opportunity to discuss things we were struggling with, which the instructors were great about reaching out and walking me through any roadblocks. My major take-aways from this project were:

1. Be patient and studious. There exists multiple solutions to the problem at hand and most IDE's have built in functionality to construct simple code solutions.
2. Even though you work on stories alone you really are apart of a team. Communicate with other team members if they need assistance.
3. While it is OK to ask for help, it shows that you care and are involved with the outcome. But do your research, you might surprise yourself and figure a lot out on your own.
4. Code is time-consuming but extremely rewarding. The more you code and practice the more efficient you'll become. 

*Jump to: [Page Top](#c#-and-.net-live-project)*
