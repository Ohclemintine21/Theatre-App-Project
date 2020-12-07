# Code Summary C-sharp Asp.NET MVC app

Theatre Project App

![resizedWebsiteFile](https://user-images.githubusercontent.com/60559963/101213271-f878e480-362e-11eb-83c0-246d4d5726ec.png)


Project Overview

I worked with a team of developers to create a exceptional theatre app using a full scale MVC/MVVM Web Application in C#. Our job was to create functionality by using C#, Bootstrap, CSS, HTML, Javascript, Jquery, SQL Database Asp.NetFramework etc. My job was to create new user roles to separate cast member login from regular users. This was done by seeding the new user to the database from the Startup.cs and the IdentityModels.cs, which is shown below. 

Working on this project was a great opportunity to learn how to fix bugs, clean and rebuild code, and add requested features to the app. I was able to obtain the skills as a good developer to work with what is given to create a quality product. My main focus for this app was working on back end stories and successfully sumbitted a few. I am proud of the work I have done on this project and know these skills will be very useful on many future projects.


Back End Stories

Seed a new User Role to the Database from the Startup.cs and IdentityModels.cs 

![Screenshot (193)](https://user-images.githubusercontent.com/60559963/101213646-881e9300-362f-11eb-8590-09da3094d4dd.png)


Startup.cs


            //Creating User role
            if (!roleManager.RoleExists("User"))
            {
                var role = new Microsoft.AspNet.Identity.EntityFramework.IdentityRole();
                role.Name = "User";
                roleManager.Create(role);
            }

            var userRole = new ApplicationUser()
            {
                UserName = "UserTest",
                FirstName = "Bobby",
                LastName = "Schulz",
                Email = "user.test@gmail.com",
                StreetAddress = "314 Pi Ct",
                City = "Detroit",
                //State could be Enum later
                State = "FL",
                ZipCode = "12345",
                Role = "User"
            };

            string UserRolePWD = "Ih@ve20cats";

            var UserChkRole = userManager.Create(userRole, UserRolePWD);
            if (UserChkRole.Succeeded)
            {
                var result2 = userManager.AddToRole(userRole.Id, "User");
            }
                      

IdentityModels.cs


    [Required]
           public string FirstName { get; set; }
           [Required]
           public string LastName { get; set; }
           public string StreetAddress { get; set; }
           public string City { get; set; }
           public string State { get; set; }
           public string ZipCode { get; set; }
           public string Role { get; set; } = "User";            // role of user for website
           
           

Added Photo title, create button and Options column


          @*Create is for admin only*@
          @*Create button to add new cast members*@
          @if (User.IsInRole("Admin"))
          {
            <div class="text-center m-3">
              <h3 class="d-inline-block"> Photos </h3>
              <button class="iconBtn " onclick="location.href='@Url.Action("Create")'">
              <i class="fa fa-plus-square fa-fw"></i>Create New
              </button>
            </div>
          }
          
          
  In conclusion, this project was one of my first experiences working with a team to create and build a functional and interactive website. I learned how cloning an app can cause rosyln errors to occur over and over again and several ways to clean and rebuild the app to get it working. It was satisifying seeing all the pieces of code both Front End and Back End languages come together to create a functional/beautiful website.
          
