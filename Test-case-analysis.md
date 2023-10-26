# Assignment Submission

## Project Selected: <Flask (Python)>

## I. Introduction
- This section examines two specific test cases extracted from the Flask open-source project's testing suite. The purpose is to comprehensively understand the test cases, their objectives, and the underlying mechanisms employed for quality assurance within the Flask project. Through analyzing these test cases, we gain insights into Flask's configuration management in handling different sources and formats.

## II. Test Case 1: [test_config_from_file_json()]
### A. Description
- This test case is designed to verify Flask's ability to load configuration from a JSON file. It ensures the Flask application can read and integrate configuration settings from a specified JSON file.
### B. Gherkin Syntax (if applicable)
- Scenario: Loading configuration from a JSON file
    Given the Flask application is running
    When the Flask application loads configuration from a JSON file
    Then the configuration should include the settings defined in the JSON file
### C. Test Steps
- 1. Start the Flask application.
  2. Instruct the application to load configuration from a JSON file.
  3. Validate that the configuration includes the settings defined in the JSON file.
### D. Code Segments Under Test
- Identify specific code segments or functions that are being tested in this case.

```Java
app = flask.Flask(__name__)
current_dir = os.path.dirname(os.path.abspath(__file__))
app.config.from_file(os.path.join(current_dir, "static", "config.json"), json.load)
```
### E. Initial State
- The initial state is the Flask application running.
### F. Transition
- The transition occurs when the Flask application is instructed to load configuration from a JSON file.
### G. Expected State
- After executing the test steps, the expected state is that the configuration of the Flask application should include the settings defined in the specified JSON file.

## III. Test Case 2: [test_from_prefixed_env_custom_prefix(monkeypatch)]
### A. Description
- This test case is designed to validate the ability of Flask to load configuration settings from environment variables with a custom prefix. It ensures that only the environment variables with the specified custom prefix are used to update the configuration, while other environment variables do not affect it.
### B. Gherkin Syntax (if applicable)
- Scenario: Loading configuration from environment variables with a custom prefix
    Given the Flask application is running
    When environment variables with a custom prefix are set
    And the Flask application loads configuration with the custom prefix
    Then the configuration should include settings from the custom environment variables
    And other environment variables should not affect the configuration
### C. Test Steps
- 1. Start the Flask application.
  2. Set environment variables with a custom prefix.
  3. Instruct the Flask application to load configuration with the custom prefix.
  4. Validate that the configuration includes settings from the custom environment variables.
  5. Ensure that other environment variables do not affect the configuration.
### D. Code Segments Under Test
- Identify specific code segments or functions that are being tested in this case.
```Java
monkeypatch.setenv("FLASK_A", "a")
monkeypatch.setenv("NOT_FLASK_A", "b")

app = flask.Flask(__name__)
app.config.from_prefixed_env("NOT_FLASK")
```
### E. Initial State
- The initial state is the Flask application running.
### F. Transition
- The transition occurs when the Flask application is instructed to load configuration settings from environment variables with a custom prefix.
### G. Expected State
- After executing the test steps, the expected state is that the configuration of the Flask application should include settings from the custom environment variables, and other environment variables should not affect the configuration.

