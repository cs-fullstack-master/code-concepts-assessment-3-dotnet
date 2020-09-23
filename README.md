# coding-concepts-assessment-3-.NET

> DO NOT REFER TO NOTES OR PAST CODING ASSIGNMENTS. You MAY use web resources like Google/Stackoverflow

The assessment consists of 2 parts: a coding challenge and then a code walkthough with the staff where we will ask questions about your code.

## Coding Challenge - Creating a Fullstack MERN Bank Account Manager
You will create a bank account applcation that will let you create bank accounts and manage deposits and withdrawls.
- After cloning this repo, create separate `client` and `server` directories

### Backend Express Server
- Should have at minimum 4 endpoints:
  - List all bank accounts
  - Create a new bank account
  - Deposit into bank account ($100)
  - Withdraw from bank account ($100)

- Should have at least one Mongoose Model for `BankAccountSchema`:
  - `accountNumber` - Unique number
  - `accountType` - String that specifies `Checking` or `Savings`
  - `accountName` - String
  - `accountBalance` - Number
  - `{timestamps: true}`

- Create a test case for each endpoint in Postman and export/include completed test cases in this repo

- Starter builerplate code has been provided in this repo for `index.js` that contains code for initial server setup. Copy and paste into your `index.js` and update appropriately

## Frontend React Application
- Create a react application called `client`
- Create at minimum 4 components:
  - `AppContainer` The top-level component for your application
  - `AddAccountForm` Contains the form for creating new accounts
  - `AccountList` Lists all the bank accounts
  - `Account` Lists the `number`, `type`, `name`, and `balance`
    - A button that deposits $100 to the account
    - A button that withdraws $100 from the account
  
`AppContainer`
- Displays at least an `<h1>` heading of `Bank Account Manager`
- As part of component state, have a `BankAccountList` array that contains all of the bank accounts
  - This array will be passed down to the child component `AccountList` to be rendered
- Has a callback method called `addAccount` that accepts alll parameters necessary to create a new bank account
  - When the callback method is called, the component will update the appropriate array in component state and render the updated account list
  
`AddAccountForm`
- Contains the form for creating a new bank account
  - `accountNumber` An input field for entering the account number for the new account
  - `accountType` An input field for specifying checking or savings
  - `accountName` An input field for entering the account 
  - `accountBalance` An input field for specifying starting balance
  - A button for submisson of the data from the form
  - When the form is submitted, use the callback method reference from the parent component to update the parent component's state

`AccountList`
  - Should contain at least a basic header of `Available Accounts`
  - Should render an `Account` component for each account in the `BankAccountList` array passed down from the parent component
  
  `Account`
    - Should list the `number`, `type`, `name`, and `balance`passed down from parent component and:
      - A button that deposits $100 to the account
      - A button that withdraws $100 from the account
  
Layout
- You *must* use CSS grid for this layout
- In addition to displaying the application header (from `AppContainer`) your layout should display either the list of bank accounts (by default) *or* a form to add a new bank account
  -Use *either* conditional rendering or React Router to display only the add account form or the list of current accounts
  - Provide buttons or links to return to home page (account listing) and add new account form
  
Git
- Commit and push your changes no less than *once per hour*

Take some time at start to do some pre-thinking and design. At *minimum* you should have a basic wireframe drawn up (*ADD A PICTURE OF DESIGN TO REPO*)
----------------------------------------------------------------------------------------------------
If you need clarification of requirements *ASK EARLY*. Do not wait until right before it is due

Read errors *CAREFULLY* when solving issues as Code School staff cannot help with bugs in your code

Take your time. Code a little, test a little, and Good Luck!

----------------------------------------------------------------------------------------------------
### Challenges
- Modify `account` component so you can specify a specific dollar amount to deposit or withdraw
- Add the ability to modify an account's details 
- Add the ability to delete an account
- Improve the styling and overall look of the application as you see fit
