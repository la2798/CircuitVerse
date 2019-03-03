# README

[![Gitter](https://badges.gitter.im/CircuitVerse/community.svg)](https://gitter.im/CircuitVerse/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

## Steps to make your first pull request
- Fork the project 
- Clone your local project
- To see that your local copy has a reference to your forked remote repository in github, run the following command
```
$ git remote -v
```
You should see the following output:
```
origin https://github.com/your_username/CircuitVerse.git (fetch)
origin https://github.com/your_username/CircuitVerse.git (push)
```
Now add a reference to the original CircuitVerse repository
```
$ git remote add upstream https://github/CircuitVerse/CircuitVerse.git
```
See the changes using
```
$ git remote -v
```
```
origin https://github.com/your_username/CircuitVerse.git (fetch)
origin https://github.com/your_username/CircuitVerse.git (push)
upstream https://github.com/CircuitVerse/CircuitVerse.git (fetch)
upstream https://github.com/CircuitVerse/CircuitVerse.git (push)
```
- Sync it
In a regular internval and before making any changes, run the following commands carefully to update your local repository
```
# to fetch all remote repositories and delete any deleted remote branches
$ git fetch --all --prune

# switch to master branch
$ git checkout master

# Reset local master branch to match upstream repository master branch
$ git reset --hard upstream/master

# Push the changes to your forked repo
$ git push origin master
```
- Create a new Branch
After completing the above steps, you are good to start contributing to our Issues. Please create a seperate branch and keep your master branch clean
```
# To create a new branch and switch to it
$ git checkout -b branch_name
```
To switch to a desired branch
```
$ git checkout branch_name
```
- Make changes, commit and push it 
```
# To add all the files to branch branch_name
$ git add .

# To commit the changes (This message gets associated with all the files that you have changed)
$ git commit -m 'commit message'

#To push your work to your remote repository
$ git push -u origin branch_name
```
- Open a pull request : The final step 
```
- Go to your repository in browser
- Click on compare and pull requests
- Add a title and description to your pull request
- And its done!
```

## Steps for opening issues
![alt test](https://help.github.com/assets/images/help/repository/repo-tabs-issues.png)
## Versions
- Ruby Version: ruby-2.5.1
- Rails Version: Rails 5.1.6
- PostgreSQL Version: 9.5

## Setup Instructions

**Note:** You might want to use the docker instructions if you do not want to setup your own environment. 

* Install ruby using RVM, use ruby-2.5.1
* Install Dependencies: `bundle install --without production`
* Configure your DB in config/database.yml, copy config/database.yml.example
* Create database: `rails db:create`
* Run Migrations: `rails db:migrate`
* At this point, local development can be started with ```rails s -b 127.0.0.1 -p 8080```

Additional software:
* Install imagemagick
* Start Redis server process.
* To start sidekiq: `bundle exec sidekiq -e development -q default -q mailers -d -L tmp/sidekiq.log` (In development)

## Docker Instructions

* Install docker and docker-compose
* Run: `docker-compose up`

If you need to rebuild, run this before `docker-compose up`
```
docker-compose down 
docker-compose build --no-cache
```

## Developer Instructions
Developers can quickly get started by setting up the dev environment using the instructions above. The database is seeded with the following admin account. 
```
User: Admin
Email: admin@circuitverse.org
Password: password
```

For debugging include `binding.pry` anywhere inside the code to open the `pry` console.

## Additional setup instructions for Ubuntu
Additional instructions can be found [here](https://www.howtoforge.com/tutorial/ubuntu-ruby-on-rails/) and there are some extra notes for single user installations:
- If setting up Postgres with these instructions, use your user name instead of 'rails_dev'.
- [Run Terminal as a login shell](https://rvm.io/integration/gnome-terminal/) so ruby and rails will be available.
- You can remove `gem mysql2` from the gemfile (but don't check it in), move `gem pg` up and create the database.yml file with just Postgres. Example:
```
default: &default
  adapter: postgresql
  encoding: unicode
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: <your user name>
  password: <postgres password>

development:
  <<: *default
  database: circuitverse_development

test:
  <<: *default
  database: circuitverse_test

production:
  <<: *default
  database: circuitverse_production
  username: circuitverse
  password: <%= ENV['circuitverse_DATABASE_PASSWORD'] %>
```

- If you are facing difficulties installing RVM, most probably it is because of an older version of rvm shipped with Ubuntu's desktop edition and updating the same resolves the problem.

  Removing RVM
  ```  
  sudo apt-get --purge remove ruby-rvm` <br /> 
  sudo rm -rf /usr/share/ruby-rvm /etc/rvmrc /etc/profile.d/rvm.sh
  ```
  Installing new version of RVM
  ```
  curl -L https://get.rvm.io | 
  bash -s stable --ruby --autolibs=enable --auto-dotfiles
  ```
- If you are facing errors running the `rails db:create` ensure that the socket file(i.e mysql.sock) is present in that location.   Some possible locations where it might be present is `/run/mysqld/mysqld.sock`  or `/var/lib/mysql/mysql.sock` and mention the exact location.


## Production Specific Instructions

```
bundle install --without development test
RAILS_ENV=production bundle exec rake assets:precompile
bundle exec sidekiq -e production -q default -q mailers -d -L tmp/sidekiq.log` (In production)
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) for details.
