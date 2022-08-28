default image
For example, you are using a web application and displaying images from an API.

and the user's internet goes down, or a network problem occurs, or the API is unavailable.

The user will get something like this view in the front-end application.

Image description

How to fix this

 -Normally, we create an img tag like this to display an image.
```html
<img src="your image.jpg" alt="Italian Trulli">
```
by using javascript or onerror
```html
<img id="currentPhoto" src="SomeImage.jpg" onerror="this.onerror=null; this.src='Default.jpg'" alt="" width="100" height="120">
```

That's it. There are a lot of things to do  Thanks for reading my post It's my first post, and I hope you enjoyed it.
