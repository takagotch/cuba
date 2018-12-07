### cuba
---
http://cuba.is/
.rb
https://github.com/soveran/cuba

```
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

```

```ruby
require ""
require ""
Cuba.use Rack::Session::Cookie, :secret => ""
Cuba.plugin Cuba::Safe
Cuba.defind do
end

Cuba.defind do
end

Cuba.defind do
end
```

### CUBA-Platform
---
.java
https://www.cuba-platform.com/

```
```


