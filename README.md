# API Todo app

* Ruby - v3.0.0

* Rails - v6.1.4

Install all gems:
```
bundle install
```
Run migrations:
```
bin/rails db:migrate
```
Seed the database:
```
bin/rails db:seed
```
Run the test suite:
```
bundle exec rspec
```
Start the rails server
```
bin/rails s
```
it will be available on http://localhost:3000

# Usage

The API is versioned. Currently, it's V1 which is also the default.

* Sign up a new user

```
http :3000/signup name=foo email=foo@email.com password=foobar password_confirmation=foobar
```

When you sign up, you will be able to get the auth token from the output of the above command. Alternatively, you can get the auth token by running:

```
http :3000/auth/login email=foo@email.com password=foobar
```

* Create a todo
```
http POST :3000/todos title=foo \
Authorization:'eyJhbGciOiJIUzI1NiJ...'
```

* View all of your todos
```
http :3000/todos Accept:'application/vnd.todos.v1+json' Authorization:'eyJhbGciOiJIUzI1NiJ...'
```

The API has pagination, it shows 20 results per page. If you wish you can view specific pages by editing the page parameter.
```
http :3000/todos page==1 Accept:'application/vnd.todos.v1+json' Authorization:'eyJhbGciOiJIUzI1NiJ...'
```

* Add an item to a todo
```
http POST :3000/todos/id/items name='foo baz' done=false Accept:'application/vnd.todos.v1+json' Authorization:'eyJhbGciOiJIUzI1NiJ...'
```

