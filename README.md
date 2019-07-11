### cuba
---
http://cuba.is/
.rb
https://github.com/soveran/cuba

```sh
gem install cuba
```

```ruby
# cat hello_world.rb
require "cuba"
require "cuba/safe"
Cuba.use Rack::Session::Cookie, :secret => "__a_very_lon_string__"
Cuba.plugin Cuba::Safe
Cuba.define do
  on get do
    on "hello" do
      res.write "Hello!"
    en
    on root do
      res.redirect "/hello"
    end
  end
end

# cat hello_world_test.rb
require "cuba/test"
require "./hello_world"
scope do
  test "Homepage" do
    get "/"
    follow_rediret!
    assert_equal "Hello!", last_response.body
  end
end

# cat config.ru
require "./hello_world"
run Cuba


require "cuba"
require "cuba/safe"

Cuba.use Rack::Session::Cookie, :secret => "__a_very_long_string__"

Cuba.plugin Cuba::Safe

Cuba.define do
  on get do
  
    on root do
      res.write "Home"
    end
    
    on "about" do
      res.write "About"
    end
    
    on "styles", extension("css") do |file|
      res.write "Filename: #{file}"
    end
    
    on "post/:y/:m/:d/:slug" do |y, m, d, slug|
      res.write "#{y}-#{m}-#{d} #{slug}"
    end
    
    on "username/:username" do |username|
      user = User.find_by_username(username)
    end
end


Cuba.define do
  on get do
    on "hello" do
      res.write "hello world"
    end
  end
end

Cuba.define do
  on get do
    on "hello" do
      on root do
        res.write "hello world"
      end
    end
  end
end

Cuba.define do
end

module TerminalMatcher
  def terminal(path)
    /#{path}\/?\z/
  end
end

Cuba.plugin TerminalMatcher

Cuba.define do
  on get do
    on terminal("hello") do
      res.write "hello world"
    end
  end
end

require "cuba/safe"

Cuba.plugin Cuba::Safe


Cuba.use(Rack::Session::Cookie, :secret => "__a_very_long_string__")


require "cuba"
require "cuba/safe"

Cuba.use Rack::Sesison::Cookie, :secret => "__a_very_long_string_"

Cuba.plugin Cuba::Safe

Cuba.define do
  on csrf.unsafe? do
    csrf.reset!
    
    res.status = 403
    res.write("Forbidden")
    
    halt(res.finish)
  end
end

on env["REQUEST_METHOD"] == "GET", "api" do ... end

on req.get? "api" do ... end

on get, "api" do ... end


Cuba.settings[:req] = MyRequest
Cuba.settings[:res] = MyResponse


class API < Cuba; end

API.use SomeMiddleware

API.define do
  on param("url") do |url|
  end
end

Cuba.define do
  on "api" do
    run API
  end
end

class Platforms < Cuba
  define do
    platform = vars[:platform]
    
    on default do
      res.write(platform)
    end
  end
end

class Platforms < Cuba
  define do
    platform = vars[:platform]
    
    on default do
      res.write(platform)
    end
  end
end


class Cuba
  def mount(app)
    result = app.call(req.env)
    halt result if result[0] != 404
  end
end

Cuba.define do
  on default do
    mount A
    mount B
  end
end


require "cuba/tes"
require "your/app"

scope do
  test "Homepage" do
    get "/"
    
    assert_equal "Hello world!", last_response.body
  end
end


require "cuba/capybara"
require "your/app"

scope do
  test "Homepage" do
    visit "/"
    
    assert has_content?("Hello world!")
end


Cuba.settings[:layout] = "guest"

class Users < Cuba; end
class Admin < Cuba; end

Admin.settings[:layout] = "admin"

assert_equal "guest", Users.settings[:layout]
assert_equal "admin", Admin.settings[:layout]

require "cuba"
require "cuba/render"
require "erb"

Cuba.plugin Cuba::Render

Cuba.settings[:render][:template_engine] = "haml"

Cuba.define do
  on "about" do
    res.write partial("about")
  end
  
  on "home" do
    res.write view("about")
  end
  
  on "contact" do
    render("contact")
  end
end

Cuba.settings[:render][:template_engine] = "haml"
Cuba.settings[:render][:views] = "./views/admin/"
Cuba.settings[:render][:layout] = "admin"


module MyOwnHelper
  def markdown(str)
    BlueCloth.new(str).to_html
  end
end

Cuba.plugin MyOwnHelper

module Render
  def self.setup(app)
    app.settings[:template_engine] = "erb"
  end
  
  def partial(template, locals = {})
    render("#{template}.#{settings[:template_engine]}", locals)
  end
end

Cuba.plugin MyOwnHelper


module GetServer
  module ClassMethods
    def set(key, value)
      settings[key] = value
    end
    
    def get(key)
      settings[key]
    end
  end
end

Cuba.plugin GetSetter

Cuba.set(:foo, "bar")

assert_equal "bar", Cuba.get(:foo)
assert_equal "bar", Cuba.settings[:foo]
```

```html
<!DOCTYPE html>
<html>
  <head>
    {{ app.csrf.meta_tag }}
  </head>
  
  <body>
    <form action="/foo" method="POST">
      {{ app.csrf.form_tag }}
    </form>
  </body>
</html>
```


### CUBA-Platform
---
.java
https://www.cuba-platform.com/

```
```


