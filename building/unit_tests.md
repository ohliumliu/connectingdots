* Need to create the database for the test environment

* `bundle exec rake test:units` limits the tests to run

* There is an error message related to a missing rails/performance_test_help. This is needed in performance tests.   

* gem 'mocha': This gem is used to stub or mock an object.
  *  require 'mocha/test_unit'
  * Code example
```ruby
http_client = OpenUriClient.new # a mock object
http_client.expects(:get).returns(mock_xml) #provide mock return for a particular method
```

Example: test_call_browse_node_api
This test is a method defined in class ImportAmazonTest. The purpose is to test whether the parsing of call_browse_node_api works.
A mock http_client is generated to return an xml response copied from Amazon API doc site. The expected return value of 
call_browse_node_api is an array of ASIN numbers. Using https://regex101.com/, the xml response is manually parsed to 
extract all the ASIN numbers and saved as an array (using w%{a b c d} for easy construction). The expected result is compared 
with the result from calling call_browse_node_api. Note that the returned value of call_browse_node_api is a node set which 
can be converted to array by a mapping

```ruby
parsed_array = parsed_node_set.map {|node| node.content}
```
* Test whether a method is called
```ruby
instance = class.new
instance.expect(:instance_method_to_be_called).once
instance.instance_method_to_be_called # => no failure

instance.expect(:another_method).once
instance.instance_method_to_be_called # => failure
```
