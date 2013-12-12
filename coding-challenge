/**
 * Created with JetBrains WebStorm.
 * User: massimo
 * Date: 12/12/13
 * Time: 11:09 AM
 * To change this template use File | Settings | File Templates.
 */


function Value(specs) {

    var that = {};
    var value = 0; // private variable, let's use closures to access it

    // enumerable, writable, configurable are false by default

    Object.defineProperty(that,"min",
        {
            value: ((specs && specs.min != void 0) ? specs.min : 0)
        });


    Object.defineProperty(that,"max",
        {
            value: (specs && (specs.max != void 0) ? specs.max : void 0)

        });

    Object.defineProperty(that, "value",
        {
            get: function() {
                return value;
            },
            set: function(newValue) {
                var minCond = true, maxCond = true;

                if(this.min != void 0) // using != we guard both undefined and null
                {
                    if(newValue < this.min)
                        minCond = false;
                }

                if(this.max != void 0)
                {
                    if(newValue > this.max)
                        maxCond = false;
                }

                if(!(minCond && maxCond))
                    throw "Error: Out of bound";
                else
                    value = newValue;
            }

        });

    // let's fake / override the function used by the + operator
    Object.defineProperty(that, 'valueOf', {
        value: function(){
            return this.value; // using getter
        }
    });

    // init the value invoking the setter
    if(specs && specs.value != void 0)
        that.value = specs.value;

    return that;
}

