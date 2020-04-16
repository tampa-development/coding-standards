# .NET

## Naming
### Solution Naming
Solutions should be descriptively named to reflect the purpose of the solution. The name of the solution should usually match the name of repository in source control. Use hyphen to separate the words instead of space to avoid URL encoding.  

Examples
- Payment-Gateway-Api
- Cake-Api
- Free-Radio-Project-of-America

### Project Naming
Project names should contain the [Company].[Project].[Intention] with dot notation separators. The name of the output assembly should match the name of the project. Project names should use PascalCase. Only the first letter of each “word” should be upper-cased.

Examples:
- Bank.PaymentGateway.Reports
- Bakery.Catalog.Api
- Restaurant.KitchenDisplaySystem.Api.Tests

### Namespace Naming
Namespaces should match the project naming guidance and extend to sub-folders.
- Extension Methods will always end with a .Extensions namespace.
- Auto-Generated code MUST always exist in a sub folder.

Examples:
- Bakery.Catalog.Api
- Restaurant.KitchenDisplaySystem.Api.Tests.Mocks

### Class Naming
Classes should be named with a noun or noun phrase. Classes should use PascalCase. Classes should only use the letters A-Z. Numbers are only appropriate when they are significant to the name, for example an ISO code number.
When inheriting from a class the derived class should always be on the left.
When creating an abstract or base class avoid terms like Abstract or Base to describe that they are a base class.

Examples:

- Account
- SavingsAccount
- Iso4712Currency


### Variable Naming
All variables should describe their usage. Abbreviations should be avoided unless they are common. Consistency is very important here. Consider that you won't be the only person to work on your code.

### Properties
Properties should always be PascalCased independent of accessibility. General naming guidance should be followed.

### Private Fields
Private members should be _camelCased with a leading underscore. General naming guidance should be followed.

### Protected, Public, and Static Fields
- Protected fields should be avoided but when used, they should be PascalCased. General naming guidance should be followed.
- Public fields should be avoided but when used, they should be PascalCased. General naming guidance should be followed.
- Static fields should be PascalCased. General naming guidance should be followed.

### Parameters
Parameters should be camelCased. General naming guidance should be followed; but may be abandoned when used for state management, i.e. loop indices, etc.

### Local Variables
Local variables should be camelCased. General naming guidance should be followed; but may be abandoned when used for state management, i.e. loop indices, etc.

### Constants
Should follow the naming convention for public fields.

### Method Naming
PascalCase names

Avoid abbreviations

Should clearly convey the purpose

Examples:

- RetrieveAccountFromDataStore - <span style="color:green">Good</span>
- GCAT - <span style="color:red">Bad</span>


### Configuration Variable Naming
Configuration variables in appSettings sections should be namespaced such that it is clear what application is using this setting, e.g., PaymentConnector.FinancingTermsUrl

### Configuration Sections

Configuration sections are preferred over using the more generic appSettings; as intention is clear as to what your design is. There are open topics of discussions about how these should be used as overly using configuration sections can feel burdensome and become a bit of an anti-pattern

## Code Layout
### Project Layout
Do not use solution folders for projects
### Class Layout
#### Order of Members
- Non-Public Fields and Properties - Private members when initialized from a constructor should be marked as `readonly` unless other conditions prevent this
- Public Properties
- Constructors - Constructors should flow from simplest implementation to most complex implementation
- Public Methods - Overloads should go from least to most complex
- Non-Public Methods

### Comments
#### XML Comments
- XML comments MUST always exist for classes
- XML summary comments MUST exist for all public methods
- XML parameter comments MAY be skipped for public methods
- Elaboration required
- Describe Exceptions in Xml Comments
- Developer responsibility to keep comments fresh

#### Inline Comments
Inline Comments should be used to only describe very unobvious logic

Do not comment out code for posterity, i.e. delete it; favor source control

When using Tokens e.g., `//TODO`, `//HACK`
- Use creator's Initials, e.g. `//TODO: RLV - Illuminating comment here`
- Clearly explain what the token is for

Coding Styles
- SOLID  - We ascribe good code with SOLID practices. Adhere to such principles wherever possible

- Don't use regions, e.g. #region. Regions hide code. Ask yourself "why do I want to hide this code?" The reason is probably that your class is too long or doing too many things. Regions are a code smell.

- Use abstractions where possible

- Favor composition over inheritance

- Favor Dependency Injection
  - Use constructor injection - dependencies should be clearly spelled out in the constructor of a class
  - Do not use the service locator pattern

## Testing (Consult Lead Developer for Testing Tools/Methods)
### Quality Gates
#### Code Coverage
- **Green Field: Percentage of Code Coverage should be no less than 80%
- Brown Field: Create dedicated backlog items to account for code coverage less than 80%
#### Unit test pass 100%
- Commenting out tests is not a valid strategy

## Error Handling

### When to handle errors
- Only catch errors you can handle
- Bubble up all others

### Throw vs Rethrow vs Swallow
- Swallow exceptions only in a very limited number of scenarios, e.g. an exception while handling or logging an exception
- Do not rethrow exceptions

Example

Do not:
```
try 
{
…
}
catch (Exception ex)
{ 
    throw ex;
}
```
Instead do:
```
try
{
…
}
catch (Exception ex)
{
    throw;
}
```
The exception thrown should match the domain, e.g, initialization exception received by the user should indicate exception in the initialization

## Stuff To Avoid
#### Code Smells - The following list includes code practices we consider poor or that may indicate refactoring may be necessary
- Manager Classes
- God Classes
- Utility or "Util" Classes, static or otherwise
- Extension Methods Inside a Single Project
- Large Class Methods
- Large/Nested Switch Statements
- Direct Configuration Handling using AppSettings
- Don't mix business logic and code logic together
