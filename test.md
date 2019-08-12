# Testing

## Types of tests

- unit test: testing one isolated function, or one React component

  - Enzyme’s shallow() is a unit test.

- integration test: testing an entire React component including children components.

  - Enzyme’s mount() is an integration test.

- Mock function: Redefining a function specifically for a test to generate a result. E.g.
  - prevent the hard-coded sum issue we were discussing earlier!
  - Mock functions can be defined in jest with jest.fn(() => { //function here });.

## test terminology

- Smoke test: Verifies that a component renders without throwing.
  - Utilising Enzyme’s shallow() is indeed a smoke test, as is mount().
- Shallow rendering: rendering a component with no children.
  - Enzyme’s shallow() is a form of shallow rendering, whereas mount() is not.
- Full rendering: Rendering a component and all of its children.
  - mount() is a full rendering method whereas shallow() is not.
- Static rendering: Rendering components to static HTML files and then analysing the results.
  - Enzyme’s render() method is used for static rendering.

## Approach

- BDD: function first testing
- TDD: test first testing
