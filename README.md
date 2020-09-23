###### Top
# Coding Assessment 3 - .NET
[Requirements Summary](#Functional-Requirements-Summary)

> DO NOT REFER TO NOTES OR PAST CODING ASSIGNMENTS. You MAY use web resources like Google/Stackoverflow

The assessment consists of 2 parts: a coding challenge and then a code walkthrough with the staff where we will ask questions about your code.

## Coding Challenge - Creating a Fullstack Bank Account Manager
You will create a bank account application that will let you create bank accounts and manage deposits and withdrawals.

You will implement this solution as a .NET MVC application utilizing the following:
- .NET MVC for backend and Razor templates/partials for content generation
- .NET Entity Framework for persistence
- .NET Identity Framework for User authentication and authorization
- PostMan tool for testing

### Backend
- Should have at **minimum** 5 endpoints/actions restricted by User role (admin, employee):
  - List all bank accounts - admin, employee
  - Create a new bank account - admin
  - View bank account from list - admin, employee
  - Deposit into bank account - admin
  - Withdraw from bank account - admin

- Should have entity model for `BankAccountModel` with all properties being **required**:
  - `AccountNumber` - int
  - `AccountType` - string that specifies either `Checking` or `Savings`
  - `AccountName` - string
  - `AccountBalance` - number (integer value with no decimal point is OK)

### Frontend
  
`Available Bank Account List Page`
  - Should contain at least a basic header of `Available Bank Accounts` and **should be the home page** after a User signs in
  - Should display the list of bank accounts
    - `AccountNumber`, `AccountType`, `AccountName`, and `AccountBalance` 
    - `AccountNumber` should be hyperlinked to the bank account details page
    - A Razor template partial should be used to render each account in the list
    - You may use an HTML table or BootStrap cards with Grid to display account list
  
`Bank Account Details Page`
  - Should display the `AccountNumber`, `AccountType`, `AccountName`, and `AccountBalance` (read only)
  - A form that allows the User to enter an amount to add or subtract from the account balance (i.e. positive number for deposit or negative number for withdrawal)
  - A button for submission of the data from the form
  - Submitting a **valid** form should update account and return to the list of accounts

`Add Account Form Page`
- Contains the form for creating a new bank account
  - `AccountNumber` An input field for entering the account number for the new account
  - `AccountType` An input field for specifying 'checking' or 'savings'
  - `AccountName` An input field for entering a name for the account 
  - `AccountBalance` An input field for specifying starting balance
  - A button for submission of the data from the form
  - When a **valid** form is submitted, should return to account list
  
`Git`
- Commit and push your changes no less than *once per hour*

`Test Cases`
- Create a test case for each endpoint in Postman and export/include completed test cases in this repo
  
`Wire Frames`
- Take some time at start to do some pre-thinking and design. At *minimum* you should have a basic wire frame drawn up (*ADD A PICTURE OF DESIGN TO REPO*)
----------------------------------------------------------------------------------------------------
If you need clarification of requirements *ASK EARLY*. Do not wait until right before it is due.

Read errors *CAREFULLY* when solving issues as Code School staff cannot help with bugs in your code

Take your time. Code a little, test a little, and Good Luck!

----------------------------------------------------------------------------------------------------
## Helpers
### Required Packages to Install
```
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Microsoft.EntityFrameworkCore.Sqlite
dotnet add package Microsoft.AspNetCore.MVC.Razor.RuntimeCompilation
```

### Code Snippets
`Startup.cs`
- Razor View Compilation
```
services.AddControllersWithViews().AddRazorRuntimeCompilation();
```

- Authentication/Authorization
```
services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
.AddRoles<IdentityRole>() // <- Add This 
.AddEntityFrameworkStores<ApplicationDbContext>();

// Add support for user roles
services.AddMvc(obj =>
{
	var policy = new AuthorizationPolicyBuilder()
		.RequireAuthenticatedUser()
		.Build();
});
```
`User and User Roles`
- Use the sqlite program to insert roles and associate roles to registered users using SQL
```
INSERT INTO `AspNetRoles` (Id, ConcurrencyStamp, Name, NormalizedName) VALUES (1,'','admin','ADMIN')

INSERT INTO `AspNetRoles` (Id, ConcurrencyStamp, Name, NormalizedName) VALUES (2,'','employee','EMPLOYEE')

INSERT INTO `AspNetUserRoles` (UserId, RoleId)
VALUES (`UserIdGUIDValueFromAspNetUsers','1');

INSERT INTO `AspNetUserRoles` (UserId, RoleId)
VALUES (`UserIdGUIDValueFromAspNetUsers','2');

```
## Functional-Requirements-Summary
1. Require User Registration/Login and create Admin and Employee roles with at least one registered user for each role
2. Support for the following features:
  - List bank accounts
  - View bank account
  - Deposit/withdraw from a bank account (Properly restrict feature access by user role)
3. Submission of wire frames
4. Submission of Postman test cases
5. Proper use of Git for version control


[Back to Top](#Top)
