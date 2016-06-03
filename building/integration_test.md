## A high-level description of integration test

### Outline
  1. Behavior. Use [cucumber](cucumber.md) to describe behavior (feature) and generate scaffold code.
  1. Operation. In the scaffold code, tell the computer what to do and what to expect by using something like [capybara](capybara.md).
  1. Simulation. Need a headless browser, for example, phantomJS t simulate user interaction. Need a driver, for example, Poltergeist
               for capybara to talk with phantomJS. phantomJS can test javascript (such as ajax calls)
