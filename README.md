# Docksal

Docksal configuration is included in the .docksal directory.

## Requirements

------------
* [docksal](http://docksal.readthedocs.io/en/master/getting-started/env-setup/) >= 1.6
* (OSX & Windows)[virtualBox](https://www.virtualbox.org/wiki/Downloads) >= 5.1.x

## Getting Started

------------------

1. From inside the project root, run `fin init`
2. Enter your password when prompted
3. Visit `http://drupalcampsc.docksal/` in your browser of choice. 

## How do I work on this?

------------------

1. Navigate to http://drupalcampsc.docksal/ 
2. From inside the project root `fin` to see a list of available commands
   - `fin drush`
   - `fin uli`
3. fin acts as a wrapper to pass commands to the various running servers, 
so there's no need to log into the VM

### Code Structure
The web root lives within the /web directory.  It contains a full Drupal
installation that gets deployed to various hosting platforms to power dev,
test, staging, live, and multidev websites. 

### Module Layout
* modules/contrib -- Contrib modules from d.o
* modules/custom -- Custom modules developed for the project

## Email

(This is coming in a future iteration)

Docksal is configured to capture all emails sent locally. It will *not* send emails out beyond the VM. The emails are captured with mail hog and can be accessed at http://webmail.drupalcampsc.docksal

## Testing

(This is coming in a future iteration)

This project is complete with a testing suite. To get started copy the `behat.yml.dist` to `behat.yml` and override any system specific configurations. 

### Running tests

* `fin behat` - this will run the entire behat testing suite.
* `fin behat features/<your_feature_file>.feature` - executes a specific feature
* `fin behat --tags=<tag_name>` - Will run all tests tagged with '@tag_name'
* `fin behat -dl` - Shows all available step definitions

### Organizing tests

Following Cucumber best practices tests should be organized using the following pattern:
`{business object}_{action}_{context}.feature`
e.g 
- `user_login.feature`
- `node_translation.feature`
- `product.feature`
- `product_search.feature`
- `product_search_onebook.feature`
- `product_search_that_one_annoying_product_with_GROOV_in_the_SKU.feature`

### Writing features

* Use the `@api` tag to make the test bootstrap Drupal with the DrupalDriver
  * This will use Guotte as the browser, a glorified http client (runs extremely fast)
* use the `@javascript` to make tests run using Selenium
  * Use when we features rely on javascript (runs much slower)