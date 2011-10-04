Creating a Jekyll App on Heroku Cedar
===

Setup Jekyll
---

The first thing you have to do, install the jekyll gem.

    gem install jekyll

Create the site structure
---

Create the app directory

    mkdir jekyll-app

and create the following files:

    cd jekyll-app
    touch _config.yml
    touch index.html
    mkdir _posts
    mkdir _layouts
    touch _layouts/default.html

"Hello World" Jekyll
---

Let's create a Layout. Open _layouts/default.html and add:

    <html>
    <body>
      {{ content }}
    </body>
    </html>

Now we need an index page. Open index.html and add:

    <h1>Hello World</h1>

Let's test it locally:

    jekyll --server --auto

Open your browser and go to http://localhost:4000

You should see "Hello World"

Deploying to Heroku
---

First, install the Heroku gem

    gem install heroku

Create a Gemfile and add:

    source :rubygems
    
    gem 'RedCloth'
    gem 'jekyll'

Create the Gemfile.lock

    bundle install

Create a Procfile

    echo "web:	jekyll --server $PORT" > Procfile

Exclude all of those files

    echo "exclude:  [ Gemfile, Gemfile.lock, Procfile, vendor]" >> _config.yml

Create a git repo and commit

    git init .
    git add .
    git commit

Create a Heroku app

    heroku create --stack cedar

Deploy!

    git push heroku master

Test it:

    heroku open

That's it!