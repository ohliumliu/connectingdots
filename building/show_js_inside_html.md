How to call javascript inside html

```
<script> 
showAllAlerts(<%= @user_alerts.to_json.to_s.html_safe %>);
</script>
```

Notice that rails instance variable can be converted to jason, which is a valid jQuery object.
