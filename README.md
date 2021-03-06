# exchange_rate

## Product aim:

```ruby
gem 'exchange_rate'
```

## Introduction

This production-ready Ruby code builds a library of FX rates pulled from the European Central Bank: https://www.ecb.europa.eu/stats/eurofxref/eurofxref-hist-90d.xml

The definition of production-ready: I believe this is when the app can accurately supply exchange rates detailed in the European Central bank api to GBP. This code is production-ready as it passes all tests for all currencies.

## How does it work?

This code provides a library for Ruby. Download it or, if you have time, gem install it. Here's how a client would expect to use the library where GBP is the base currency
and USD is the counter currency:
```
ExchangeRate.at(Date.today,'GBP','USD')
ExchangeRate.at(Date.yesterday, "GBP", "USD")
ExchangeRate.at(Date.today, "GBP", "EUR")
```
The code has been setup to start working as a simple UI with sinatra and Sinatra-contrib. For this reason we have the two files: app.rb and views/index.erb. This can be developed to a fuller extent and given more views with time. To run this, simply use the following in the command line:
```
ruby app.rb
```

## Dependencies

- This app calls the ECB api. While the data depends on this service, the data can be prefetched and stored locally. This means that you should be able to access the most recent exchange rates from the store.  
- You will also need to :
```
gem install nokogiri
gem install open-uri
```

## What if the service is down?

If ECB service is down then the library is designed to return an error message. Once the data has been fetched, you should still have previous data to obtain most recent rates.

## Limitations

This app will only return your requested exchange rates on the requested day. It isn't currently configured to return an exchange rate to a requested amount. This is something I'd happily add with more development.

Finally, I have only just made this into a gem with Bundler. For this reason further development work is required to make a CLI with Thor and to release the gem.  

## Additional resources

Please feel free to have a quick look at the trello board I was working with throughout the project:

![Trello](trello.png)
