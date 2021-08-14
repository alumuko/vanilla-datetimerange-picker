# vanilla-datetimerange-picker

## Overview.
A JavaScript component that is a date &amp; time range picker, no need to build, no dependencies except Moment.js, that is inspired by [Dan Grossman's bootstrap-daterangepicker](https://github.com/dangrossman/daterangepicker).

Actually, this program is base on Dan Grossman's bootstrap-daterangepicker (version 3.1).
I just changed the code a bit to not need jquery.


## Requirements
-  [Moment.js](https://momentjs.com/)
### IE11
If you want to use on Internet Explorer 11, include [Polyfill](https://polyfill.io/v3/polyfill.js?ua=ie/11) to use CustomEvent, Object.assign, Element.prototype.closest and Element.prototype.matches features.


## Quick start using CDN.
1. Include Moment.js and Date Range Picker's css and js files in your webpage:
```
<link type="text/css" rel="stylesheet" href="https://cdn.jsdelivr.net/gh/alumuko/vanilla-datetimerange-picker@latest/dist/vanilla-datetimerange-picker.css">

<script src="https://cdn.jsdelivr.net/momentjs/latest/moment.min.js" type="text/javascript"></script>
<script src="https://cdn.jsdelivr.net/gh/alumuko/vanilla-datetimerange-picker@latest/dist/vanilla-datetimerange-picker.js"></script>
```
2. Put "INPUT" element into "BODY", and bind DateRangePicker instance.
```
<input type="text" id="datetimerange-input1" size="24" style="text-align:center">

<script>
    window.addEventListener("load", function (event) {
        new DateRangePicker('datetimerange-input1');
    });
</script>
```

See [simple example page](/examples/simple-example.html)</a>.
## Usage
```
new DateRangePicker(bindElement, options, callback);
```

| parameter | type | means |
----|----|---- 
| bindElement | string or object | bind element id or bind HTMLElement object |
| options | object | option set (see Options) |
| callback | function(momemt, moment) | change datetime callback, 2 parameters: start and end datetime |

## Options
<details>
<summary>Almost same as Dan Grossman's bootstrap-daterangepicker Version 3.1</summary>

| name | type | means |
----|----|---- 
| startDate | Date or string | The beginning date of the initially selected date range. If you provide a string, it must match the date format string set in your locale setting.|
| endDate | Date or string | The end date of the initially selected date range.|
| minDate | Date or string | The earliest date a user may select.|
| maxDate | Date or string | The latest date a user may select. |
| maxSapn | object | The maximum span between the selected start and end dates. Check off **maxSpan** in the configuration generator for an example of how to use this. You can provide any object the moment library would let you add to a date. |
|showDropdowns | true/false | Show year and month select boxes above calendars to jump to a specific month and year. |
 minYear | number | The minimum year shown in the dropdowns when **showDropdowns** is set to true.|
| maxYear | number | The maximum year shown in the dropdowns when **showDropdowns** is set to true.|
| showWeekNumbers | true/**false** | Show localized week numbers at the start of each week on the calendars.|
| showISOWeekNumbers | true/**false** | Show ISO week numbers at the start of each week on the calendars.|
| timePicker | true/**false** | Adds select boxes to choose times in addition to dates.|
| timePickerIncrement | number | Increment of the minutes selection list for times (i.e. 30 to allow only selection of times ending in 0 or 30).|
  timePicker24Hour | true/**false** | Use 24-hour instead of 12-hour times, removing the AM/PM selection.|
| timePickerSeconds | true/**false** | Show seconds in the timePicker. |
| ranges | object |Set predefined date ranges the user can select from. Each key is the label for the range, and its value an array with two dates representing the bounds of the range. See example code.|
| showCustomRangeLabel | **true**/false | Displays "Custom Range" at the end of the list of predefined ranges, when the ranges option is used. This option will be highlighted whenever the current date range selection does not match one of the predefined ranges. Clicking it will display the calendars to select a new range. |
| alwaysShowCalendars | true/**false** | Normally, if you use the ranges option to specify pre-defined date ranges, calendars for choosing a custom date range are not shown until the user clicks "Custom Range". When this option is set to true, the calendars for choosing a custom date range are always shown instead. |
| opens | 'left'/**'right'**/'center' | Whether the picker appears aligned to the left, to the right, or centered under the HTML element it's attached to. |
| drops | **'down'**/'up'/'auto' | Whether the picker appears below (default) or above the HTML element it's attached to. |
| buttonClasses | string | CSS class names that will be added to both the apply and cancel buttons.|
| applyButtonClasses | string | CSS class names that will be added only to the apply button.|
| cancelButtonClasses | string | CSS class names that will be added only to the cancel button. |
| locale | object | Allows you to provide localized strings for buttons and labels, customize the date format, and change the first day of week for the calendars. See "locale option object".|
| singleDatePicker | true/**false** | Show only a single calendar to choose one date, instead of a range picker with two calendars. The start and end dates provided to your callback will be the same single date chosen.|
| autoApply | true/**false** Hide the apply and cancel buttons, and automatically apply a new date range as soon as two dates are clicked.|
| linkedCalendars | **true**/false | When enabled, the two calendars displayed will always be for two sequential months (i.e. January and February), and both will be advanced when clicking the left or right arrows above the calendars. When disabled, the two calendars can be individually advanced and display any month/year.|
| isInvalidDate | function(moment) | A function that is passed each date in the two calendars before they are displayed, and may return true or false to indicate whether that date should be available for selection or not.|
| isCustomDate | function(moment) | A function that is passed each date in the two calendars before they are displayed, and may return a string or array of CSS class names to apply to that date's calendar cell.|
| autoUpdateInput | **true**/false Indicates whether the date range picker should automatically update the value of the &lt;input&gt; element it's attached to at initialization and when the selected dates change.|
| parentEl | string | jQuery selector of the parent element that the date range picker will be added to, if not provided this will be 'body'|
> **strong text value** means default value.

</details>


## Methods
<details>
<summary> You can programmatically update the startDate and endDate in the picker using the setStartDate and setEndDate methods. You can access the Date Range Picker object and its functions and properties through data properties of the element you attached it to.</summary>

| name | type | means |
----|----|---- 
| setStartDate | Date or string | Sets the date range picker's currently selected start date to the provided date |
| setEndDate | Date or string | Sets the date range picker's currently selected end date to the provided date |

### Usage
```
    let drp = new DateRangePicker('datetimerange-input1', { alwaysShowCalendars: true });,
    drp.setStartDate('2014/03/01');
    drp.setEndDate('2014/03/03');
```
</details>

## Events
<details>
<summary> Several events are triggered on the element you attach the picker to, which you can listen for.</summary>

| name |  means |
----|---- 
| show.daterangepicker | Triggered when the picker is shown |
| hide.daterangepicker | Triggered when the picker is hidden |
| showCalendar.daterangepicker | Triggered when the calendar(s) are shown |
| hideCalendar.daterangepicker | Triggered when the calendar(s) are hidden |
| apply.daterangepicker |Triggered when the apply button is clicked, or when a predefined range is clicked |
| cancel.daterangepicker |Triggered when the cancel button is clicked |

### Usage
```
    window.addEventListener('apply.daterangepicker', function (ev) {
        console.log(ev.detail.startDate.format('YYYY-MM-DD'));
        console.log(ev.detail.endDate.format('YYYY-MM-DD'));
    });
```
</details>

## Examples
### Data Time Range Picker with a Callback.
![Data Time Range Picker](/examples/vanilla-datatime-range-picker.png)

```
<input type="text" id="datetimerange-input1" size="40" style="text-align:center">

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
