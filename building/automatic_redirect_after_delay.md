set up automatic redirection in html tag

```
<body onload="timer=setTimeout(function(){ window.location='/';}, 3000)">
<p>Thank you, <%= @user.name %></p>
<p>You will be redirected in 3 seconds</p>
</body>
```
