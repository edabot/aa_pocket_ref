

###Flash and Flash.now
Flash is used for the *next* request

Flash.now is used for *this* request

See Partials for rendering Flash errors

###BCrypt
```
pasword_digest = BCrypt::Password.create(password)
bcrypt_object = BCrypt::Password.new(password_digest)
bcrypt_object.password_is?(password) --> true
```
###authenticity token

What you need to include inside a form to be CSRF safe

```
<input type="hidden" name="authenticity_token" value="<%= form_authenticity_token %>"
```

###view helpers

.html_safe keeps html from being converted into text. Brackets stay as brackets

.h(text) converts html into text. Works with .html_safe

Ex.

```
html = "<a href=\"#{that_url}\">
html += "#{h(name)} (#{h(description)})"
html += "</a>"

html.html_safe
```

###layouts

all of the content from the other pages goes in the layout here:
```
<%= yield %>
```

If you want to specify a different part of the layout page, that would look like this in the layout:
```
<%= yield :footer %>
```
That would be passed to using this in the view:
```
<% content_for :footer do %>
Hi!
<% end %>
```

###partials

called like this:
```
<%= render "shared/errors" %>
```

this will call the file in "shared/_errors"
```
<% if flash[:errors] %>
  <ul>
  <% flash[:errors].each do |error| %>
    <li><%= error %></li>
  <% end %>
  </ul>
<% end %>
```

###partials rendering collections

partial filename = _cat.html.erb

longhand method

```
<% @cats.each do |cat| %>
  <%= render "cat", cat: cat %>
<% end %>
```
shorthand method
```
<%= render @cats %>
```
this one works if you're rendering Cat model objects. Names need to match (I think)

###working with form partials for users logged in vs. out

the call on the edit and new pages. Note that the form itself is now *not* working with an instance variable
```
<%= render "form", cat: @cat %>
```
the partial

```
<% action = (cat.persisted? ? cat_url(cat) : cats_url) %>
<% method = (cat.persisted? ? :patch : :post) %>

<form action="<%= action %>" method="post">
  <input type="hidden" name="_method" value="<%= method %>">
  ```
###session token

making one
```
SecureRandom.urlsafe_base64(16)
```
assigned to cookie like this:
```
session[:session_token] = user.reset_session_token!
```
session is the cookie on your computer. This exact name needs to be used.

from
```  
def reset_session_token!
    self.session_token = SecureRandom.urlsafe_base64(16)
    self.save!
    self.session_token
  end
```
