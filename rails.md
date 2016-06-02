
###autehticity token

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
