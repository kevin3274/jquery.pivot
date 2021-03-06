#jquery.pivot plugin

##Description

The jquery.pivot plugin can be used for presenting table data in pivot form. It is made and maintained me, Janus Schmidt, currently employed by [Metalogic.dk](http://Metalogic.dk).

The project lives on [github](http://github.com/janusschmidt/jquery.pivot).

##Demo
For further info on how to use the plugin, have a look at the [demo](http://metalogic.dk/jquery.pivot/demo/demo.htm)

<!--
##Compatibility (Jasmine test results)
[![browser support](https://ci.testling.com/janusschmidt/jquery.pivot.png)](https://ci.testling.com/janusschmidt/jquery.pivot)
-->

##History

I made this some time ago, for a web application that enables people to keep track of time [styrpaatiden.dk](http://styrpaatiden.dk). As i am a big fan of jQuery, i decided, it was time for
me to give back to the community.

##Usage:

This is only a scarce description, so look in the examples to get more information.
The data can be parsed from a html table with special markup or from json data. As i live in denmark i've built in the possibility to pass in format and parse functions for numbers.
You can also supply a function that will be called when the user clicks a result cell. The function is passed info on which groupby value and pivot value is clicked. This can be used
to fetch and present more details from the server.

To use the plugin you need a script reference to `jquery`, the plugin `build/jquery.pivot.min.js` and maybe the `demo/stylesheet.css` if you don't want to style the pivot
yourself. The fold unfold images are defined in the css.

The plugins accepts these parameters:

```javascript
$.fn.pivot.defaults = {
    source: null, //Must be json or a jquery element containing a table
    bTotals: true, //Includes total row and column
    bCollapsible: true, // Set to false to expand all and remove open/close buttons
    aggregatefunc: calcsum, //defaults to sum. Set to null for no totals. Set to function that concatenates for strings.
    formatFunc: function (n) { return n; }, //A function to format numeric result/total cells. Ie. for non US numeric formats
    parseNumFunc: function (n) { return +n; },  //Can be used if parsing a html table and want a non standard method of parsing data. 
                                                //Ie. for non US numeric formats.
                                                //Set to null if result column should be considered string data.
    onResultCellClicked: null,  //Method thats called when a result cell is clicked. This can be used to call server and present details for that cell. 
                                //Signature = function(dataObjectWithInformationOnClikedCell, jqueryElementThatsClicked)
    noGroupByText: "No value", //Text used if no data is available for specific groupby and pivot value.
    noDataText: "No data" //Text used if source data is empty.
    sortPivotColumnHeaders: true //if false pivot columns will appear in the order they are discovered in the source.
};
```

##Development
The source is in Typescript.

When developing edit the `src\ts\*.ts` files and check your changes in `src\devdemo.htm` and `tests\specrunner.html`. 

Either use an editor that can compile typescript to javascript or use *grunt* via *node* 

1. Install node.
2. In *node* console install grunt `npm install -g grunt-cli`.
2. In *node* console `cd` to project directory and run `npm install`
3. In *node* console run `grunt`command

*grunt* is set up to:

1. Generate javascript files from typescripts.
2. Jshint all (non minified) javascript.
3. Minify selected files.
4. Run jasmine tests via phantomjs.

If you wan't to send a pull request, make sure you run *grunt* without errors first.

If you for some reason don't want to use typescript, You're welcome to send bugs/change suggestions in plain javacript

##License
The project uses the MIT license.
