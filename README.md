# Outside-In TDD in React

## Features

- A login page with just one login button
- Once clicked, a loading screen will appear while fetching some data
- When ready, the data will be displayed
- Each item will have a delete button that will remove it

## Goals

- Build the ui logic without any concern about layout, styling etc.
- Only assert conditional rendering component interactions and properties

## Acceptance tests

### Login button

```gherkin
Scenario: The login button is displayed by default
Given the main page
Then I should see the login button

Scenario: Logging in will display loading section
Given the main page
When I click on the login button
Then I should see the loading section
And The login button should disappear
```

### Loading section

```gherkin
Scenario: Loading section should be displayed while the data is pending
  Given the main page with the loading section displayed
  When The data is pending
  Then I should see the loading section
  But I shouldn't see the data section

Scenario: Loading section will disappear once the data is ready
Given the main page with the loading section displayed
When The data is ready
Then I should see the data section
```

### Data section

```gherkin
Scenario: Data section should display each item
Given the main page with the data section
Then I should see all the items

Scenario: Each data item should have a delete button
Given A data item
Then I should see its delete button

Scenario: The delete button should delete the item
Given A data item
When I click on the delete button
Then I shouldn't see the item anymore 
```
