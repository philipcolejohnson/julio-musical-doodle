# Basic Associations Assessment




## Google Form Q+As | **Don't forget the Q+As!!!**


#### Complete the questions at [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSeOn3xqCFj1SkPGJ6wJ4tPhuCauP_4qL-m3IiZnZbq-1IvA7w/viewform) and sumbit!




## Build a raw HTML Rails form given a params hash

Here is a ruby hash that represents the params
submitted by a form.

```ruby
{
  :utf8 => '✓',
  :authenticity_token => '401b09eab3c013d4ca54922bb802bec8fd5318192b0a75f201d8b3727429080fb337591abd3e44453b954555b7a0812e1081c39b740293f765eae731f5a65ed1',
  :user => {
    :username => 'foobar1234',
    :email => 'foo1234@bar.com',
    :password => 'password1234',
    :password_confirm => 'password1234'
  }
}
```

Given the hash above, complete the following:

- create a file in the root directory of this project called `form.html`
- in the file you must write a raw HTML form (**NO `form_for` NO `form_tag` or anything but HTML**)
- the form should be setup so that when submitted:
    - it nests attributes exactly like the hash above
    - password inputs are used where needed
    - sensitive data must not be displayed to the user
    - unnecessary data must not be display to the user
- some inputs will require values to be set
- other inputs must be left blank for the user to provide a value
- **remember you are working in a raw HTML file without ERB!**
- don't forget the default functionality of HTML input types!





## Rails Associations

### Setup

1. Install the local gems with bundler

    ```shell
    $ bundle install
    ```

1. Check that RSpec is working

    ```shell
    $ bundle exec rspec
    ```

1. Make sure guard is working

    ```shell
    $ bundle exec guard
    ```

1. **Once everything is set and you run guard or rspec,
you will most likely see errors that**:

    - the schema doesn't exist
    - a model doesn't exist

Follow these errors to create/run the necessary commands to set up your database
and create the models that the tests expect!



### Schema

You will need to create a schema with a structure and relationships
that make the below associations possible.

**Think about**

- what tables you need
- what foreign keys you need
- what tables get the foreign keys

**This is for you! Don't make this pretty or post it anywhere for grading.**
This is a step for you to think about how your data model is structured
before you begin implementing.


### Migrations

Once you have your schema you will need to create the migrations
that setup the database.

Generating a model automatically creates a migration file for that model's table.

**NOTE: Make sure to use the option of `--no-test-framework`. This ensures that test files that will conflict with existing ones will NOT be created.**

```shell
$ rails g model MyModel --no-test-framework
```

Populate your migrations with the schema you created above and get associating!


### Models

Create Rails models that have the following attributes and associations:

**NOTE we have purposely left out a join model for your many-to-many relationship to allow you to name that model how you wish. You WILL need to create a join model to correctly implement your associations.**

1. Employee
    - attributes:
        - `first_name:string`
        - `last_name:string`
        - `email:string`
    - associations:
        - has many `teams`
            - teams of which the employee is a member
        - has many `progress reports`
            - progress reports the employee wrote about a team
        - has many `owned teams`
            - teams of which the employee is the owner

1. Team
    - attributes:
        - `name:string`
    - associations:
        - belongs to `owner`
            - employee that owns the team
        - has many `members`
            - employees that are members of the team
        - has many `progress_reports`
            - progress reports written about this team

1. Progress Report
    - attributes:
        - `body:text`
    - associations:
        - belongs to `author`
            - employee that wrote the progress report
        - belongs to `team`
            - team that the progress report is written about

### Seeding

Create a barebones seeds file that populates the database with records in all tables.

The seeds should generate records that use all of the above associations where appropriate.

The seeds should be minimal and only to help you verify your associations work.

The [Faker gem](https://github.com/stympy/faker) has been provided for you to make this process easier!

**Focus on making the associations work and make sure they return what is expected!**


## Good Luck!


Employee

-has_many :memberships

has_many :teams
has_many :progress_reports
has_many :owned_teams

Team
-owner_id

belongs_to :owner
has_many :members
has_many :progress_reports

Report
author_id
team_id
belongs_to :author
belongs_to :team

Membership
-employee_id
-team_id
