# ng-grid : An Angular DataGrid

This is a fork of the ng-grid project. The focus on this fork is to provide some needed performance improvements and
style changes.

## Testing

The testing setup is based on the [angular-seed project](https://github.com/angular/angular-seed/).

Make sure to set your CHROME_BIN environment variable to the full path to chrome.exe (not just its directory).

### Grunt tasks

There are a few grunt tasks for running tests:
    
    # Run unit tests
    > grunt karma:unit
    # Or use this alias:
    > grunt test

    # Run end-to-end tests (make sure to first start a web server as specified below)
    > grunt karma:e2e

    # Run midway tests
    > grunt karma:midway

### End-to-end tests

The e2e tests need a webserver to run. A simple one from the angular-seed project is included:

    > ./scripts/web-server.js

### Automated testing and building

Running this task will automatically rebuild `build/ng-grid.debug.js` when source files change, and run unit tests when `build/ng-grid.debug.js` or unit test files change. Youc an use this for testing during development.

    # Run this in its own window
    > grunt testwatch

### Integration testing

There is a task for CI testing with PhantomJS

1. Make sure the PHANTOMJS_BIN environment variable  is set properly
2. PhantomJS with the singleRun option doesn't appear to function properly in Windows. The tests will run but PhantomJS will not automatically close.
3. This task first builds the debug version of the source files and does not clean them up. If you run it you will have uncommitted changes in your working directory that you probably want to lose. `git checkout build` to lose them.

    > grunt test-ci

### Selecting browsers

All the test tasks accept a `--browsers` command line option that will be passed to karma.
    
    # Automatically re-run tests in both Chrome and FF.
    grunt testwatch --browsers=Chrome,Firefox
