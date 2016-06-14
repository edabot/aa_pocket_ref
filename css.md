Recommended default CSS from Jon's CSS video

```
html, body, section, arcticle, h1, h2, p {

  margin: 0;
  border: 0;
  padding: 0;
  
  font: inherit;
  text-align: inherit;
  text-decoration: inherit;
  color: inherit;
  
  backround: transparent;
}
```

###Clear the float

```
.group:after{
  content: "";
  display:block;
  clear: both;
}
```
