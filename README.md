# vanilla-datetimerange-picker

## Overview.
A JavaScript component that is a date &amp; time range picker, no need to build, no dependencies except Moment.js, that is inspired by Dan Grossman's bootstrap-daterangepicker.

Actually, this program is base on Dan Grossman's bootstrap-daterangepicker (version 3.1).
I just changed the code a bit to not need jquery.


## Requirements
-  Moment.js https://momentjs.com/
### IE11
If you want to use on Internet Explorer 11, include Polyfill ( https://polyfill.io/v3/polyfill.js ) to use CustomEvent, Object.assign, Element.prototype.closest and Element.prototype.matches features.


## Quick start using CDN.
1. Include Moment.js and Date Range Picker's css and js files in your webpage:
```
<link type="text/css" rel="stylesheet" href="https://cdn.jsdelivr.net/gh/alumuko/vanilla-datetimerange-picker@latest/dist/vanilla-datetimerange-picker.css">

<script src="https://cdn.jsdelivr.net/momentjs/latest/moment.min.js" type="text/javascript"></script>
<script src="https://cdn.jsdelivr.net/gh/alumuko/vanilla-datetimerange-picker@latest/dist/vanilla-datetimerange-picker.js"></script>
```
2. Put "INPUT" element into "BODY", and bind DateRangePicker instance.
```
<input type="text" id="datetimerange-input1" size="24" style="text-align:center"></input>

<script>
    window.addEventListener("load", function (event) {
        new DateRangePicker('datetimerange-input1');
    });
</script>
```

See [simple example page](/examples/simple-example.html)</a>.
## Usage
```
new DateRangePicker(bindElementId, options, callback);
```

| parameter | type | means |
----|----|---- 
| bindElementId | string | bind element id |
| options | object | option set (see Options) |
| callback | function(momemt, moment) | change datetime callback, 2 parameters: start and end datetime |

## Options
Same as [Dan Grossman's bootstrap-daterangepicker.](http://www.daterangepicker.com/) (version 3.1)

## Examples
### Data Time Range Picker with a Callback.
![Data Time Range Picker](/examples/vanilla-datatime-range-picker.png)

```
<input type="text" id="datetimerange-input1" size="40" style="text-align:center"></input>

<script>
    window.addEventListener("load", function (event) {
        new DateRangePicker('datetimerange-input1',
            {
                timePicker: true,
                opens: 'left',
                ranges: {
                    'Today': [moment().startOf('day'), moment().endOf('day')],
                    'Yesterday': [moment().subtract(1, 'days').startOf('day'), moment().subtract(1, 'days').endOf('day')],
                    'Last 7 Days': [moment().subtract(6, 'days').startOf('day'), moment().endOf('day')],
                    'This Month': [moment().startOf('month').startOf('day'), moment().endOf('month').endOf('day')],
                },
                locale: {
                    format: "YYYY-MM-DD HH:mm:ss",
                }
            },
            function (start, end) {
                alert(start.format() + " - " + end.format());
            })
    });
</script>
```
See [datetime example page](/examples/datetime-example.html)</a>.

## Special Thanks
 Special thanks to [Dan Grossman](http://www.dangrossman.info/)

## License
 [MIT License](LICENSE)
