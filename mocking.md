Mocking:
  overide or change behaviour off dependencies
  avoid unintended side effects
  isolate code being tested

Why use mocking:
  avoid relying on external services
    can't guarentee their availibility
    makes test inconsistent
  avoid unintended consequences
    accedently sending emails
    oveloading external services - for example override sending emails to users while testing
    Example: register user -> send_email()
      we can prevennt email being sent while ensure email_sent() called correctly
  Speed up tests:
    by avoiding code moking functionality that is taking time

How to mock?
  use unittest.mock
    MagicMock/Mock - replace real objects with mock objects
    Patch - overrides code for tests
