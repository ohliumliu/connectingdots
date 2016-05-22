When writing test, need to run reload after changing the database so that the test variables are aware of the change.
For example, `users(:test_user)` is in fixture, and it is changed in the database in the controller under testing. 
`users(:test_user).reload` is needed to update the record in memory for assertion.
