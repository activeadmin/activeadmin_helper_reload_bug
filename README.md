# ActiveAdmin Helper Reload Bug

This app is to reproduce [activeadmin/activeadmin#697](https://github.com/activeadmin/activeadmin/issues/697#issuecomment-78875499).

## Setup

1. `git clone git@github.com:activeadmin/activeadmin_helper_reload_bug.git`
2. `bundle install`
3. `rake db:migrate`
4. `rails server`

## Reproduce 1

1. go to [http://localhost:3000/admin](http://localhost:3000/admin) or what ever your host / port is
2. you should see `23` as value
4. edit `app/helpers/application_helper.rb` and change `23` to `42`
5. reload the dashboard in the browser and you still see `23` and not the expected `42`

## Reproduce 2

1. go to [http://localhost:3000/admin](http://localhost:3000/admin) or what ever your host / port is
2. you should see `23` as value
4. edit `app/admin/dashboard.rb` and rename `a_static_value` to `a_other_static_value`
4. edit `app/helpers/application_helper.rb` and rename `a_static_value` to `a_other_static_value`
5. reload the dashboard in the browser and you get this error:
```
undefined local variable or method `a_other_static_value' for #<ActiveAdmin::Views::Pages::Page:0x007fab52f82ac8>
```
