#Agile Software Development Using Ruby on Rails: Basics

##Software as a Service (Saas)
Like renting software
Benefits:
- No installation worries
- No worries about data loss
- Collaboration
- 1 copy of large / changing data sets
- Easier to develop

###Service-oriented architecture
Essential idea: Design software in a modular way

###Hardware for Saas
Needs:
- Communication
- Scalability
- Dependability

Solution: Clusters (Regular commodity computers connected by ethernet switches)
- More scalable
- Cheaper (20x!! due to economy of scale)
- Dependable by redundancy rather than individual machine quality

##Legacy code vs. beautiful code
People in industry say: Learn to deal with legacy code!

##Software quality
###Principles
1. Satisfy customer needs
2. Easy to develop

###Validation vs. verification
Verification means: Did you build the thing right?
Validation means: Did you build the right thing?

###Testing
####Levels of testing
- Unit tests
- Module or functional tests
- Integration tests: Tests interfaces between units
- Acceptance tests: Customer is satisfied

####Terminology
- Black box vs. white box testing
- Test coverage
- Regression testing
- Continuous integration (CI): Continuous integration testing

##Productivity
- Clarity via conciceness
    - Syntax
    - Abstraction
- Synthesis
    - Auto-generated code
- Reuse
- Automation and tools

##Software Development Processes
Can software development be as dependable as building a bridge?
###Plan and Document
- Project manager makes a plan
- Progress measured against the plan

####Waterfall lifecycle (1970)
1. Requirements analysis
2. Architecture
3. Implementation and integration
4. Verification
5. Operation & maintainance

Problem: It's just what we asked for, but not what we want.
"Throw away the first iteration...you will anyhow."

####Spiral
Similar to waterfall, but with short iterations on the process

Benefits:
- Iterations involve customers
- Riskmanagement
- Easier to monitor project
- Schedule projections get more realistic over time

Downsides:
- Iterations 6 to 24 months long
- Lots of documentation
- Cost of process is high
- Hard to meet budget and schedule targets

####Rational Unified Process (RUP)
Phases:
- Inception: Business case set schedule and budget
- Elaboration: use cases SW architecture, prototype
- Construction
- Transition

Benefits:
- Business processes tied to development
- Lots of tools
- Tools support gradual improvement

Downsides:
- Expensive tools
- Only good for medium to large projects
- Requires good judgement by project management

####Project management
- Plan and develop strategy requires strong project management
- Teams are larger
- Communication time grows with team size
- Groups of 4 to 9, but many such groups on large projects
- "Adding manpower to a late project makes it later"

###Agile Process

####The Agile Manifesto (2001)
We are uncovering better ways of developing SW by doing it and helping others to do it. Through this work we have come to value
- Individuals and interactions over processes & tools
- Working software over comprehensive documentation
- Customer collaboration over contract negotiation
- Responding to change over following a plan

That is, while there is value in the items on the right,
we value the items on the left more.

####Extreme Programming (XP)
- Short iterations (weeks vs. years)
- Do the *simplest* thing that could possibly work
- Test all the time. Write tests before you write the code
- Review code continuously by pair programming

####Agile lifecycle
- Embrace change
- Refine prototypes
- Test driven development, user stories, velocity (measuring progress to predict future progress)

####Agile Team Management: Scrum
- "2 pizza" team size
- Short "standup" meeting every day (15 minutes) everyone answers 3 questions:
    1. What have you done since yesterday?
    2. What are you planning to do today?
    3. Are there any impediments or stumbling blocks?

##### Scrum roles
- Team
- Scrum Master
    - Acts as buffer between team and external distractions
    - Keeps team focused on task at hand
    - Enforces team rules (coding standards)
    - Removes impediments
- Product Owner
    - Prioritizes user stories

##### Resolving conflicts
- List all items on which we agree
- Each side articulates the other's arguments
- Constructive confrontation
- Disagree and commit

### Pair Programming
Driver and Observer

## Ruby

### Conventions
- Class names use UpperCamelCase
- Methods and variables use snake_case
- Boolean methods end with "?"
- Methods with side effects end with "!"
- Constants are in UPPERCASE

### Important quirks
- Double quoted strings can be interpolated, single quoted strings are verbatim
- Implicit return
- Metaprogramming: Writing and running new code *at runtime*

### Regular expressions
- use ~= to compare a string against a regular expressions
- `"fox@berkeley.EDU" ~= /(.*)@(.*)\.edu$/i` returns true
- `^` begins with
- `$` end of string

### Metaprogramming & Reflection
Metaprogramming: Write new code at runtime
Reflection: You can ask an object questions about itself and have it modify itself at runtime

`method_missing`: A special method that is called whenever an object receives a method call
that it doesn't recognize.
`def method_missing(method_id, *args, &block)`
`method_missing` can be used to combine many different methods that would all
do essentially the same thing (for example, it could be used to allow a FixNum
to have methods to convert to many different currencies, eg `5.euros`)

### Blocks and Iterators

Blocks are *closures*

### Duck Typing
Ruby emphasizes "What do you do?" instead of "What class are you?"

#### Modules
Modules can be mixed into a class

-`Enumerable` assumes that the target object responds to `each`
-`sort` is a method of `Enumerable`, but it requires that the *elements* of the object respond to `<=>`.
-`Comparable` assumes that the target object responds to `<=>`, and provides all of the other comparisons for free

## Behavior-Driven Design (BDD) and Test-Driven Development (TDD)

- Develop user stories (the features you wish you had)
- Cucumber turns user stories into runnable acceptance and integration tests

### Unit Testing
Unit tests should be FIRST:
 - Fast
 - Independent (this can be challenging, because SaaS apps usually store data persistently)
 - Repeatable
 - Self-checking
 - Timely

Use RSpec for unit tests in Ruby, also set up something like autotest
relishapp.com/rspec/rspec-expectations/docs/built-in-matchers





