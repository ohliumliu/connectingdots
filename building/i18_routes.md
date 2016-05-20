### Route configuration of i18n
```ruby
scope ':locale', locale: /#{I18n.available_locales.join("|")}/ do
  # application routes...
end

# Catch all requests without a locale and redirect to the default...
match '*path', to: redirect("/#{I18n.default_locale}/%{path}"), constraints: lambda { |req| !req.path.starts_with? "/#{I18n.default_locale}/" }
match '', to: redirect("/#{I18n.default_locale}")
```
In this configuration, locale is required in the url. If not, it will be redirected to default. [Reference](http://www.createdbypete.com/articles/working-with-locales-and-time-zones-in-rails/)
