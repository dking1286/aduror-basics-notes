# Agile Software Development Using Ruby on Rails: Basics

## Software as a Service (Saas)
Like renting software
Benefits:
- No installation worries
- No worries about data loss
- Collaboration
- 1 copy of large / changing data sets
- Easier to develop

### Service-oriented architecture
Essential idea: Design software in a modular way

### Hardware for Saas
Needs:
- Communication
- Scalability
- Dependability

Solution: Clusters (Regular commodity computers connected by ethernet switches)
- More scalable
- Cheaper (20x!! due to economy of scale)
- Dependable by redundancy rather than individual machine quality

## Legacy code vs. beautiful code
People in industry say: Learn to deal with legacy code!

## Software quality
### Principles
1. Satisfy customer needs
2. Easy to develop

### Validation vs. verification
Verification means: Did you build the thing right?
Validation means: Did you build the right thing?

### Testing
#### Levels of testing
- Unit tests
- Module or functional tests
- Integration tests: Tests interfaces between units
- Acceptance tests: Customer is satisfied

#### Terminology
- Black box vs. white box testing
- Test coverage
- Regression testing
- Continuous integration (CI): Continuous integration testing

## Productivity
- Clarity via conciceness
    - Syntax
    - Abstraction
- Synthesis
    - Auto-generated code
- Reuse
- Automation and tools

## Software Development Processes
Can software development be as dependable as building a bridge?
### Plan and Document
- Project manager makes a plan
- Progress measured against the plan

#### Waterfall lifecycle (1970)
1. Requirements analysis
2. Architecture
3. Implementation and integration
4. Verification
5. Operation & maintainance

Problem: It's just what we asked for, but not what we want.
"Throw away the first iteration...you will anyhow."

#### Spiral
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

#### Rational Unified Process (RUP)
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

#### Project management
- Plan and develop strategy requires strong project management
- Teams are larger
- Communication time grows with team size
- Groups of 4 to 9, but many such groups on large projects
- "Adding manpower to a late project makes it later"

### Agile Process

#### The Agile Manifesto (2001)
We are uncovering better ways of developing SW by doing it and helping others to do it. Through this work we have come to value
- Individuals and interactions over processes & tools
- Working software over comprehensive documentation
- Customer collaboration over contract negotiation
- Responding to change over following a plan

That is, while there is value in the items on the right,
we value the items on the left more.

#### Extreme Programming (XP)
- Short iterations (weeks vs. years)
- Do the *simplest* thing that could possibly work
- Test all the time. Write tests before you write the code
- Review code continuously by pair programming

#### Agile lifecycle
- Embrace change
- Refine prototypes
- Test driven development, user stories, velocity (measuring progress to predict future progress)

#### Agile Team Management: Scrum
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

## Web Architecture

- The web is a *client/server* architecture.
- The web is *request/reply* oriented.
- TCP/IP "Transmission control protocol and Internet protocol"
    - IP address identifies a physical network
        - Special address 127.0.0.1 is "this computer", named `localhost`, even when not connected to the internet.
    - TCP monitors IP packets, making sure that all of the packets are delivered, and that they are delivered in the correct order.
        - "port number" is used by TCP to determine which data is destined for which program.
        - Port 80 is the standard port on which web servers listen for traffic.
- DNS "Domain name server" allows us to use meaningful names for websites rather than pure IP addresses
- HTTP "Hypertext transfer protocol"
    - An HTTP request includes:
        - request method (GET, POST, etc)
        - Uniform Resource Identifier
        - HTTP protocol version understood by the client
        - headers -- extra info regarding transfer request
    - An HTTP response includes
        - Protocol version and status code
            - 2xx All is well
            - 3xx resource moved
            - 4xx access problem
            - 5xx server error
        - Response headers
        - Response body
    - HTTP requests are stateless, so to preserve state across requests, cookies are used.
    - In Saas apps, most URIs cause a program to be run, rather than getting a static page file

### Share-nothing architecture

### Concepts
- MVC (Model, View, Controller): Design pattern to describe how the Logic tier handles data
    - Model: Handles communication with the persistance tier
    - View: Handles presenting content to the user
    - Controller: Handles user input, is the intermediary between Models and Views
        - User actions and inputs cause the methods of some Controller to be called (these methods are called "controller actions" to disambiguate from HTTP methods (GET, POST, etc.)
        - Mapping the correct incoming HTTP request to the correct Controller method is called a *route*
        - Routes come in the form `<HTTP method, URI>`. For example, `GET /movies/3`
    - Active Record: Design pattern in which each Model knows how to perform CRUD operations on the persistance tier for itself (Create, Read, Update, Destroy)
- REST: Representational State Transfer: Design routes in such a way that any HTTP request contains all of the necessary information about what resource you are asking for and what actions should be performed on it.
    - URIs and APIs thata re designed in accordance with this principle are called RESTful
    - "Don't think of a URI as naming a page, or an action--instead think of it as naming a *resource*, and the thing that you want to do with that resource."
- Marshalling / serialization: Changing the format of data so that you can do something with it.
    Usually, the term is used to refer to converting a piece of data from an *in-memory* representation to an *in-storage* representation.
    (For example, if you are storing the value of a variable into a database)

### Relational databases
Rails Models store data in *Relational Databases*
- Each Model gets its own database table
    - All rows in that table have the same structure
    - Each row has a unique value for the primary key (In Rails, this is an integer called `id`)
- The collection of all tables and their structure is called the *Schema*

#### Components
- Presentation tier: Web server (front end, Apache, Microsoft IIS, WEBrick)
- Logic tier: App server (rack) (This is where the application code runs)
- Persistance tier: Database

A Saas application needs to do the following:
- map the URI to the correct program

#### The MVC pattern

In the MVC pattern, the Model handles reading and writing data to the persistance tier. Each type of "thing" the app manipulates will have it's own type of model

The Views handle presenting data to the user. Each "thing" may have several views associated with it.

The Controllers mediate the interaction between the user and the Models. Each "thing" will have it's own Controller associated with it.

Depending on the structure of your app, there may be interrelations between the Models and Controllers of your app.
(For example, if yuo're talking about a movie review, you're also going to need to talk about the movie itself, and which user reviewed the movie.)

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

## Sinatra
Sinatra has several built-in hashes:
- `session[]` records values that you want to persist across many requests
- `flash[]` records values that you want to persist only until the *next* request (like error messages)
- `params[]` records any non-blank form fields that were submitted with the request. Each key in the hash is the `name` attribute of one of the form fields.

## Cucumber / Capybara
- Cucumber acceptance tests are put in a `features` folder and are written in `.feature` files, e.g. `/features/start_new_game.feature`
- Each `.feature` file begins with `Feature: <description>`
- Under that `Feature`, one or more `Scenario`s can be specified
- Test cases for each scenario are laid out using the words `Given`, `When`, `And`, and `Then`. These are actually all aliases for the same underlying method
- Each cucumber test case calls one test case ("step") from the `game_steps.rb` based on matching a regex, and runs that test case
    - QUESTION: How does Cucumber know where to look for `game_steps.rb` file?
- If we want to "intercept" a request coming from our app to an external service and fake a return value, we can use the `stub_request().to_return()` technique (see the `hw-sinatra-saas-hangperson` app for an example).
- In Capybara, the command `save_and_open_page` is provided by the `launchy` gem and causes a browser to open showing what the app looks like at that point in execution.

## Rails

- In Rails, Template Views are done in a language called Haml or erb
### Basics
- Models are subclasses of `ActiveRecord::Base`
- Views are subclasses of `ActionView`
- Controllers are subclasses of `ApplicationController`

### Trip through a Rails App
- Routes (in `routes.rb`) map incoming URL's to *controller actions* and extract any optional *parameters* (Route's "wildcard parameters" and anything after `?` are put into `params[]` hash accesible in controller actions)
- The controller does some computation, and any instance variables that are set inside the controller are automatically usable by the view (this is done in the background by metaprogramming).
- As long as there is a view that has the same name as the controller action,
there is no need to specify where to look for the view, it will render
the correct view automatically. (In order for this to work, there needs to be
matching names for the model, view, and controller. e.g., there is a model called
`app/models/movie.rb`, a folder `app/views/movies` for storing views related to `movies`, and
a Controller named `controllers/movies_controller.rb`)

### Model
Models subclass from `ActiveRecord::Base`

A database table name is created automatically when a model is created.
They are created with matching names. E.g. if you create a model
called `Movie`, there will be a database table called `movies`. (This is
an example of "Convention over configuration").

Database table column names are getters and setter for model attributes. Note:
The getters and setters do NOT simply modify instance variables! They actually
automatically talk to the database. (You need to call `save` or `save!` on an
AR model instance to actually save the changes to the database. The `!` version
throws an exception if the operation fails, the regular one just returns `nil`).

If `x.id` is `nil` or `x.new_record?` is true, it means that you haven't saved
`x` yet.

#### Databases and Migrations
Focus question: How do we avoid messing it up when we experiment with new
features? How do we track and manage *schema changes*? Answer: Automation!

In Rails, development, production, and test environments each have their own
DB, because different DB types are appropriate for each environment.

Migrations are done by Ruby code, and you can test the migration in the test
environment. Once you are satisfied that it is working properly, you can just do
the same migration in the production environment.

Advantages of this technique:
- Can identify each migration and know which ones applied and when, using
version control.
- Automated == reliably repeatable

To create a new migration, Rails uses another code generator:
`rails generate migration CreateMovies`

The Migration has two pre-defined empty methods, `up` and `down`, and you have
to fill in the bodies of those methods. The `up` method describes how to go to
the next version of the database, and the `down` method describes how to reverse
that change.

To apply the migration to the development environment, run `rake db:migrate`.
Then, to apply it to the production environment, run `heroku rake db:migrate`.
The database keeps track of which migrations have already happened, so if you
say `rake db:migrate` and the migration has already happened, it
won't duplicate the work.

To add a new model to a Rails app:
1. Create a migration describing the changes (`rails generate migration` gives
you boilerplate)
2. Apply the migration (`rake db:migrate`)
3. If it's a new model, create the model file in `app/models`
4. Update test DB schema (`rake db:test:prepare`). If you forget to do this,
your tests will start failing, because the testing environment has it's own
database, which needs to be set up separately. The reason for this is that tests
can be destructive, and you want to be able to test your app without destroying
important data

#### CRUD operations
1. Create: `Movie.create` combines `new` and `save`
2. Read: 
    - `Movie.where("rating='PG'")`
        - You can provide a hash if you want to interpolate values:
            - `Movie.where('rating = :rating', :rating => 'PG')`
        - Don't do this, this is a bad idea: `Movie.where("rating=#{rating}")`
        - Bad because of SQL insertion attacks.
        - `Movie.where` doesn't actually execute the db query until you dereference
            the object. This means that `where` can be chained:
            `Movie.where().where()`
    - Find by id: `Movie.find(3)` (exception if not found) or `Movie.find_by_id(3)` (nil if not found)
    - Dynamic: `Movie.find_by_title`, `Movie.find_by_title_and_rating` (these are implemented using `method_missing` metaprogramming)
3. Update:
    - Let `m = Movie.find_by_title("The Help")`
    - Modify attributes then save the object
        - `m.release_date = '2011-Aug-10'`
        - `m.save!`
    - Update attributes on existing objects
        - `m.update_attributes :release_date => '2011-Aug-10'`
4. Destroy:
    - Several ways to do it, but the best way is by using the instance method
    `destroy`.
    - E.g. `m.destroy`
    - The reason to do this is because, if you delete a movie, there might
    be other data in your app (such as reviews) that connect to that movie,
    and the `destroy` call allows us to do some other cleanup. `destroy` does
    *not* delete the in-memory object, but it does modify the setter methods
    so that they raise an exception (because there's no longer anything in the
    database to modify)
    - There is a `delete` method as well, but it is like writing raw SQL, and
    doesn't automatically perform any cleanup.

### Controller

#### Cookbook

To add a new action to a Rails app
1. Create *route* in `config/routes.rb` if needed
2. Add the action (method) in the appropriate `app/controllers/*_controller.rb`
3. Ensure that there is something for the action to render in `app/views/<model>/<action>.html.haml

#### Details
- When you set an instance variable in a controller method, that instance
variable also becomes available to the view.
- Controller actions are called by following routes
- Unless you say otherwise, at the end of a controller action (method), Rails
will look for a view with that same name as the controller action (for example
`views/movies/show.html.haml`.

### Forms
Creating a resource usually takes 2 interactions:
1. `new`: retrieve the blank form
2. `create`: submit the filled form

Similarly, updating a resource takes 2 interactions:
1. `edit`: Show the form to the user with *existing values filled in*
2. `update`: Submit form, modify model, and redirect user

Note: To update, the form action should be `PUT` instead of `POST`
#### Cookbook

To create a new submittable form:
1. Identify the action that serves the form itself
2. Identify the action that receives the *submission*
3. Create routes, actions, views for each

`name` attributes from form elements appear as keys in `params[]`

#### Details

Only *named* form inputs will be submitted

Rails has functionality for generating the form. You can use the URI helper for
the form *action*, since the URI helper generates the correct URI (you still
need to manually input the form *method* if you do this, though.)

Often, the `create` controller action doesn't have a view of its own. Instead,
it will redirect to a more useful view (for example, if you submit a form to
create a new movie, you will be redirected to the index view)

The `flash[]` hash contains information that persists until the *end of the next
request*. `flash[:notice]` is conventionally used for information,
`flash[:warning]` for errors.


## Debugging

When working on Saas, debugging can be challenging because there is no terminal
to print to.

### Debugging techniques:
- In views, `= debug(@movie)` or `= @movie.inspect` can be used to "print" string
representations of objects into your view for debugging purposes.
- Controller methods can write to log files: `logger.debug(@movie.inspect)`
- Use `rails console`

### RASP
- Read the error messages
- Ask a colleague an informed question
- Search on the internet (StackOverflow, Google, etc)
- Post on StackOverflow




