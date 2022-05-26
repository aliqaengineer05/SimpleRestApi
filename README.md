
### Base framework with cypress  and BDD -


## https://reqres.in
I have created test cases on the that would get the user list, post the users, delete the users and validate all response via Cypress tool, and used to test End to End  use cases for the same. This will run test and also creates simple mochawesome report. 

## Use Cases
	Fetch Users

	Add New Users

	Edit Users    

	Delete Users

## Folder Structure 
### Integartion 
    this contains all the feature file like getUsers and getSingle users 

Ex.

	Feature: validate for all user
	
    Scenario: to access reqres.in and perform basic api test to fetch users
	
    Given I access api request end point to get users 
	Then Verify below response for the user
    | email                  | firstname | lastname | avatar |
    | george.bluth@reqres.in | George    | Bluth    | 	https://s3.amazonaws.com/uifaces/faces/twitter/calebogden/128.jpg |

### Fixtures
	This folder contains all the test data for our test like user_data.json that looks something like this 
    
    {

       "email": "janet.weaver@reqres.in",
        "first_name": "Janet",
        "last_name": "Weaver"
     }
      
 ### Plugin's
 
 	This contains index.js file that has initial hook for our test 
    const cucumber = require('cypress-cucumber-preprocessor').default;

	module.exports = (on, config) => {
	// `on` is used to hook into various events Cypress emits
	// `config` is the resolved Cypress config
	on('file:preprocessor', cucumber());
 
	return Object.assign({}, config, {
		fixturesFolder: 'cypress/fixtures',
		integrationFolder: 'cypress/integration',
		screenshotsFolder: 'cypress/screenshots',
		videosFolder: 'cypress/videos',
		supportFile: 'cypress/support/index.js'
	});
	};


### Support

	This folder contains all the step definition for out test for ex. getUser.js with BDD step definitions that read the data from BDD or from Json fixture files
    
# Mochawesome Report

	marge (mochawesome-report-generator) is the counterpart to mochawesome, a custom 		
    reporter for use with the Javascript testing framework, mocha. Marge takes the JSON 	
    output from mochawesome and generates a full fledged HTML/CSS report that helps 		
    visualize your test suites. For installation refer this link https://www.npmjs.com/package/mochawesome-report-generator
    
    Output files are generated output.html file under mochawesome-report folder, 
    and sample reports looks like this
    
![Mocha Report](/images/mochareport.png)
 
 
# How to run scripts

	in pagkage.json configured runtime scripts like
    "e2e": "cypress run",
    "cy:run": "cypress run",
    "e2eheadless": "cypress run",
    "e2e:chrome": "cypress run --browser chrome",
    "e2e:record": "cypress run --record",
    "e2e:record:parallel": "cypress run --record --parallel",
    "merge_reports": "mochawesome-merge --reportDir mochawesome-report > mochawesome-report/output.json",
    "generate_mochawesome_report": "marge mochawesome-report/output.json",
    "e2e_mochawesome": "cypress run; npm run merge_reports; npm run generate_mochawesome_report",
    
    From command prompt run for headless as -> npm run e2eheadless
    

 


