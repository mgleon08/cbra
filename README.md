# README


### Create new project

```ruby
rails new cbra --database=mysql
```

### Remove app/

```ruby
cd cbra/
rake db:create
rm -rf app/
```

### Create new engines

```ruby
rails plugin new engines/admin --full --mountable --database=mysql
```

### Scaffold

```ruby
cd engines/admin

# 先將 gemspec "FIXME" or "TODO" 改好在跑
rails g scaffold user name
```

### Modify database

```ruby
# /config/database.yml
development:
  <<: *default
  database: cbra_development
```

```ruby
rake db:migrate
```

### Add Admin::Engine to config/routes.rb

```ruby
Rails.application.routes.draw do
  # For details on the DSL available within this file, see http://guides.rubyonrails.org/routing.html
  mount Admin::Engine, at: "/admin"
end
```

# start

```ruby
rails s
http://localhost:3000/admin/users
```

Reference

* [The Modular Monolith: Rails Architecture](https://medium.com/@dan_manges/the-modular-monolith-rails-architecture-fb1023826fc4)
* [Component Based Rails Application 模塊化的Rails_微服務以外的另一種選擇](https://speakerdeck.com/madao/component-based-rails-application-mo-kuai-hua-de-rails-wei-fu-wu-yi-wai-de-ling-chong-xuan-ze)
