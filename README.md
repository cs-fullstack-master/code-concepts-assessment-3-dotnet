# coding-concepts-assessment-3-.NET

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
- Should have at minimum 4 endpoints/actions restricted by User role (admin, employee):
  - List all bank accounts - admin, employee
  - Create a new bank account - admin
  - View bank account from list - admin, employee
  - Deposit into bank account - admin
  - Withdraw from bank account - admin

- Should have entity model for `BankAccountModel` with all properties being **required**:
  - `accountNumber` - int
  - `accountType` - string that specifies either `Checking` or `Savings`
  - `accountName` - string
  - `accountBalance` - number (integer value is OK)

### Frontend
  
`Account List`
  - Should contain at least a basic header of `Available Accounts` and **should be the home page** after a User signs in
  - Should display the list of bank accounts
    - `account number`, `type`, `name`, and `balance` 
    - `account number` should be hyperlinked to the bank account details page
  
`Account Details`
  - Should display the `account number`, `type`, `name`, and `balance` (read only)
  - A form that allows the User to enter an amount to add or subtract from the account balance (i.e. positive number for deposit or negative number for withdrawal)
  - Submitting a **valid form** should update account and return to the list of accounts

`Add Account Form`
- Contains the form for creating a new bank account
  - `accountNumber` An input field for entering the account number for the new account
  - `accountType` An input field for specifying 'checking' or 'savings'
  - `accountName` An input field for entering a name for the account 
  - `accountBalance` An input field for specifying starting balance
  - A button for submission of the data from the form
  - When the form is submitted, should return to account list
  
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
### Challenges
- Add the ability to modify an account's details 
- Add the ability to delete an account
- Improve the styling and overall look of the application as you see fit

## Helpers
### Required Packages to Install
```
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Microsoft.EntityFrameworkCore.Sqlite
dotnet add package Microsoft.AspNetCore.MVC.Razor.RuntimeCompilation
```

### Startup.cs Code Snippets
- Razor View Compilation
`services.AddControllersWithViews().AddRazorRuntimeCompilation();`

- Authentication/Authorization
```
services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
.AddRoles<IdentityRole>() // <- Add This 
.AddEntityFrameworkStores<ApplicationDbContext>();

services.AddMvc(obj =>
{
	var policy = new AuthorizationPolicyBuilder()
		.RequireAuthenticatedUser()
		.Build();
});
```
