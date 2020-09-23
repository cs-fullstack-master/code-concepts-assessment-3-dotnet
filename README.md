# coding-concepts-assessment-3-.NET

> DO NOT REFER TO NOTES OR PAST CODING ASSIGNMENTS. You MAY use web resources like Google/Stackoverflow

The assessment consists of 2 parts: a coding challenge and then a code walkthough with the staff where we will ask questions about your code.

## Coding Challenge - Creating a Fullstack Bank Account Manager
You will create a bank account applcation that will let you create bank accounts and manage deposits and withdrawls.

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

- Should have entity model for `BankAccountModel`:
  - `accountNumber` - int
  - `accountType` - string that specifies either `Checking` or `Savings`
  - `accountName` - string
  - `accountBalance` - number  

- Create a test case for each endpoint in Postman and export/include completed test cases in this repo

### Frontend
  
`Account List`
  - Should contain at least a basic header of `Available Accounts`
  - Should render an `Account` component for each account in the `BankAccountList` array passed down from the parent component
  
`Account Details`
  - Should list the `number`, `type`, `name`, and `balance`passed down from parent component and:
    - A button that deposits $100 to the account
    - A button that withdraws $100 from the account

`Add Account Form`
- Contains the form for creating a new bank account
  - `accountNumber` An input field for entering the account number for the new account
  - `accountType` An input field for specifying 'checking' or 'savings'
  - `accountName` An input field for entering a name for the account 
  - `accountBalance` An input field for specifying starting balance
  - A button for submisson of the data from the form
  - When the form is submitted, should return to account list
  
`Git`
- Commit and push your changes no less than *once per hour*

`Wireframes`
- Take some time at start to do some pre-thinking and design. At *minimum* you should have a basic wireframe drawn up (*ADD A PICTURE OF DESIGN TO REPO*)
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
### Packages
```
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Microsoft.EntityFrameworkCore.Sqlite

```
