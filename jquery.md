jQuery#addClass
jQuery#removeClass (removes the class from each of the elements) 
jQuery#toggleClass (removes the class from each element that has it, adds it to any that don't).

###Traversal
jQuery#parent, jQuery#children, and jQuery#siblings methods.


###attr
```
<script>
  const $ul = $("ul");
  $ul.children().attr("style", "background-color: red");
  $ul.parent().attr("style", "background-color: green");
  $ul.siblings().attr("style", "color: blue");
</script>
```
###Building DOM elements
```
    const $li = $("<li></li>");
    // sets the textContent property
    $li.text(coolThings[i]);
    $li.attr("style", "background-color: green");
    $ul.append($li)
```

###Event delegation

```
function HandleLiClick (event) {
  var text = $(event.curentTarget).text();
}

$("ul.tasks).on("click", "li.task", handleLiClick);
```
