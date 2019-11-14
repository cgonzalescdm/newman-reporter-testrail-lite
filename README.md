# newman-reporter-testrail

TestRail reporter for Newman with include_all false.

## Installation

`npm install newman-reporter-testrail-lite --global`

## Usage

### Prefix all test assertions you wish to map with the test number.
Include the letter C. You may map more than one test case to an assertion.
The plugin will only include the test cases specified in the Postman tests in the TestRail run. The include_all capability is set to false.
```
pm.test("C226750 C226746 Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

### Export the following environment variables.

| Environment Variable | Description |
| --- | --- |
| TESTRAIL_DOMAIN | TestRail domain (including protocol). |
| TESTRAIL_USERNAME | TestRail username / email. |
| TESTRAIL_APIKEY | TestRail [API key](http://docs.gurock.com/testrail-api2/accessing#username_and_api_key) or Password (if using LDAP). |
| TESTRAIL_PROJECTID | TestRail project id. |
| TESTRAIL_RUNID (optional) | TestRail run id.  Update a specific run instead of creating a new run.  Can use the string "latest" to update latest run. |
| TESTRAIL_SUITEID (optional) |TestRail suite id.  Mandatory in multi-suite projects.  Do not use in single-suite projects. |
| TESTRAIL_TITLE (optional) | Title of test run to create. |

You can use [direnv](https://github.com/direnv/direnv) to easily maintain directory-specific options.

You may also set some or all of these variables using bash exports.

### Run newman with the reporter option
`-r testrail-lite`

Example:

```
TESTRAIL_DOMAIN=https://example.testrail.com TESTRAIL_USERNAME=exampleuser 
TESTRAIL_APIKEY=yourkey TESTRAIL_PROJECTID=99 TESTRAIL_TITLE="Dev-API Regression" 
newman run my-collection.postman_collection.json -r testrail-lite,cli
```
