# Cat Tinder API Introduction

#### Overview
We've looked at connecting React apps to an external API, and seen how to use JSON data to build compelling frontend applications. Now we're going to build our own API that will serve the data to our frontend.

#### Previous Lecture (1 hour 2 min)
[![YouTube](http://img.youtube.com/vi/CSzqYFrRAtw/0.jpg)](https://www.youtube.com/watch?v=CSzqYFrRAtw)

#### Learning Objectives
- can create an API with data set to match frontend mockups

#### Process
- $ `rails new cat-tinder-backend -d postgresql -T`
- $ `cd cat-tinder-backend`
- $ `rails db:create`
- $ `bundle add rspec-rails`
- $ `rails generate rspec:install`
- Add the remote from your GitHub classroom repository
- Create a default branch (main)
- Make an initial commit to the repository
- $ `rails server`

#### Troubleshooting Tips
- Did you create your database?
- Did you migrate?
- Errors? Always look at the first error in the list.

---
## API Technologies
Creating our own API opens up a new world of possibilities for building engaging, interactive applications. We can begin to accept user input, store and manipulate that input in the backend, and then provide a personalized experience for our user, perfectly suited to the task the user is trying to achieve.

The primary tool to collect input from users is an HTML form. The user fills in form fields with information that allows them to interact with the application. As a general rule, we always want to process, validate, and store user data on the server where we have more control and processing power to handle it. To accomplish this, we need to build an API.

Once we have a functioning API, our React app can send the form data to the API and receive data back when requested. While there are many options for building backend APIs, Ruby on Rails is a fantastic platform.

In the architecture we are building, our front and backend will be two separate applications, giving us more freedom to choose the tools and technologies we want.

Throughout your career as a developer, you'll interact with many other backend platforms. APIs can be built using Ruby, PHP, Python, Java, and even JavaScript, among many others. That might seem overwhelming, but remember that the concepts are generally the same no matter what technology is used. The server is where we process data sent by the frontend, clean and store that data, and serve updated data back to the frontend app to be consumed by the user.

### RSpec
Running the install commands for RSpec will add the dependencies to our Gemfile and installs all the necessary files to create and run our tests. RSpec will only load when we are in development or test mode, and not production.


### Cat Resource
The following command will add the model, migration, controller, spec files, and all the RESTful routes for our cats.

```
$ rails generate resource Cat name:string age:integer enjoys:text image:text
$ rails db:migrate
````

### Initial Check
Let's take a look around the application and verify that everything is setup correctly. The first thing we can do is see that our test suite is running.  
```
$ rspec spec
```

Of course, we don't have any specs yet, so we won't get much feedback, but RSpec itself should run and finish successfully.

In the application, the following files should look something like this:

**db/migrate/**

```ruby
class CreateCats < ActiveRecord::Migration[6.0]
  def change
    create_table :cats do |t|
      t.string :name
      t.integer :age
      t.text :enjoys
      t.text :image

      t.timestamps
    end
  end
end
```

**config/routes.rb**
```ruby
Rails.application.routes.draw do
  resources :cats
  # For details on the DSL available within this file, see https://guides.rubyonrails.org/routing.html
end
```

## Challenge: Cat Tinder API Setup
As a developer, I have been commissioned to create an application where a user can see cute cats looking for friends. As a user, I can see a list of cats. I can click on a cat and see more information about that cat. I can also add cats to the list of cats looking for friends. If my work is acceptable to my client, I may also be asked to add the ability to remove a cat from the list as well as edit cat information.

- As a developer, I can create a new Rails application with a Postgresql database.
- As a developer, I can create a RSpec testing suite in my Rails application.
- As a developer, I can add a resource for Cat that has a name, an age, what the cat enjoys doing, and an image.

---
[Back to Syllabus](../../README.md#cat-tinder-backend)
