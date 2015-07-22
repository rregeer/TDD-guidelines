#TDD guidelines:
To have a better TDD experience we set up some guidelines.
For unit testing we use xUnit terminology. The [xUnit book](http://www.amazon.co.uk/dp/0131495054/ref=as_sl_pd_tf_lc?tag=xunittestpa&camp=1406&creative=6394&linkCode=as1&creativeASIN=0131495054&adid=1GHQ4W3ZV97B6B847DCT&&ref-refURL=http%3A%2F%2Fxunitpatterns.com%2Findex.html) is written by [Gerard Meszaros](http://xunitpatterns.com/gerardmeszaros.html).
Online information about xUnit can be on the [xUnit website](http://xunitpatterns.com/index.html).

##Code Coverage:
- The code coverage of the application must be at least 90%
- The build process must fail if the coverage is lower then 90%
- The coverage report must be available on the build server and should be available locally.
- The coverage must be calculated over the complete library not only the files that are covered by unit tests.
- Files that can be excluded from coverage:
  - Bootstrappers
  - Definition or configuration files.
  - Main method or starting point of the application.
  - Queries
  - Third party code
  - Templates

##General testing guidelines
- First think of the scenario's and create the tests after that create the implementation.
- Tests that are [unfinished](http://xunitpatterns.com/Unfinished%20Test%20Assertion.html) or not not implemented must fail.
- Tests should be reliable and fast.
- A test must have at least one meaningful assertion. No AssertTrue(true) for example.
- A test must be build using the [AAA pattern](http://www.agile-code.com/blog/the-anatomy-of-a-unit-test/).
- A bug that is fixed should be covered by a test. Unless the bug is in a file that is excluded for testing.
- Only test one scenario in a test. It's allowed testing the same scenario with different [parameters](http://xunitpatterns.com/Parameterized%20Test.html).
- Tests should not have any dependencies to other tests.
- All tests must be able to run on his own in any order.
- Only create tests for scenarios's that are in scoop of the code.
- Don't repeat yourself with every scenario. Test the [behavior](http://xunitpatterns.com/Behavior%20Verification.html) only in the happy path and only if needed in other scenarios.
- Make use of test suites to group the test by functionality.
- The tests must use the same folder structure as the library.
- For every file or class create a test file. Different types of testing (Unit test, Integration test and Acceptance test) must have there own file.
- If [fake](http://xunitpatterns.com/Fake%20Object.html) [test doubles](http://xunitpatterns.com/Test%20Double%20Patterns.html) are created and stored with the test. At "Fake" suffix to the filename.    for example clientFake.php.

###Unit tests
 - Always use [test doubles](http://xunitpatterns.com/Test%20Double%20Patterns.html) in the tests.
 - Always try to test the [behavior](http://xunitpatterns.com/Behavior%20Verification.html), [state](http://xunitpatterns.com/State%20Verification.html) or output.
 - Use "Test" suffix in the name of the file. For example if the file client.php is tested call the test file clientTest.php.

###Integration tests
 - Only use [test doubles](http://xunitpatterns.com/Test%20Double%20Patterns.html) where needed for example to [mock](http://xunitpatterns.com/Mock%20Object.html) the database connection.
   Use [spies](http://xunitpatterns.com/Test%20Spy.html) to test the [behavior](http://xunitpatterns.com/Behavior%20Verification.html).
 - Use "IntegrationTest" suffix in the name of the file. For example if the file client.php is tested call the test file clientIntegrationTest.php.

###Test doubles
Use the correct [test double](http://xunitpatterns.com/Test%20Double%20Patterns.html) for the job.
- Use a [fake](http://xunitpatterns.com/Fake%20Object.html) for a static implementation that doesn't need to be tested.
- Use a [spy](http://xunitpatterns.com/Test%20Stub.html) for [behavior](http://xunitpatterns.com/Behavior%20Verification.html) verification, but use a real implementation.
- Use a [mock](http://xunitpatterns.com/Mock%20Object.html) for [behavior](http://xunitpatterns.com/Behavior%20Verification.html) verification, but use a fake implementation and set expectations.
- Use a [stub](http://xunitpatterns.com/Test%20Stub.html#Stub) for a fake implementation to manipulate the results.

If the test double is assigned to a variable in the test, use the test double type in the variable name for example: clientFake, clientMock, clientStub or clientSpy.
