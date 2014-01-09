# ng-grid : An Angular DataGrid ( forked )

This is a fork of the ng-grid project to allow user customize some gridOptions not available by default like:
* An property called 'extraColumnsWhenGrouping' to don't add extra columns in the row when there are groups.
* Now 'aggregateTemplate' can accept an array instead of the template string. In that way we can specify different templates for each group level.
* Added @semeltheone performance improvement to this folk.
* New mode 'keepUncollapsedRowsOpen' added ( false by default ) which will store the last uncollapsed group in the 'uncollapsedRowsList' list property and when you print the grid again, it will keep the label-name groups matched open by default. It's up to you to store this 'uncollapsedRowsList' variable safe in a localstorage, the scope of your application, etc. to keep them open depending on where it is stored.
* Now internal search mechanism don't go into object of rows. So in that way, it avoid the bug of returning prematurely when a cell contains an object (https://github.com/angular-ui/ng-grid/issues/603) and it focus on plain properties which makes it even faster.
* New property 'leftOffsetForGroupRows' added make able don't add this left side offset in grouped rows ( when leftOffsetForGroupRows === false, true by default ).

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
