# SetLocale

This is a work in progress. Features are tested within the main Rails application that makes use of this gem.

## Usage

```
# Gemfile

gem 'set_locale', git: 'https://github.com/debreczeni/set_locale.git'
```

```
# config.initializers/set_locale.rb

# Hook into another controller than ApplicationController, for example if you
# have a different application controller for you Admin and your public Front-end
# SetLocale.controller = "FrontendController"

# Override default strategies in order of precedence:
# if the locale cannot be found as a parameter it will fall back to the cookie and so on...
SetLocale.strategies = [
  SetLocale::Strategies::Parameter.new, # default strategy
  # SetLocale::Strategies::UserPreference.new(locale_method: :preferred_locale), # Persist and retrive user's preferred locale
  SetLocale::Strategies::Cookie.new('i18next'), # default strategy
  # SetLocale::Strategies::HttpHeader.new # Try to get locale from HTTP_ACCEPT_LANGUAGE
]
```
