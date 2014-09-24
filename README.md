# Snackbar
[![Build Status](https://travis-ci.org/wmora/snackbar.svg?branch=master)](https://travis-ci.org/wmora/snackbar)

Library that implements <a href="http://www.google.com/design/spec/components/snackbars-and-toasts.html">Snackbars</a> from Google's <a href="http://www.google.com/design/spec/material-design/introduction.html">Material Design documentation</a>.

<a href="http://1.bp.blogspot.com/-5OkYxr59g10/U_Ps-4vV3XI/AAAAAAAAGyQ/RPX1BAd9eHU/s1600/Screenshot_2014-08-19-19-14-07.png" imageanchor="1"><img border="0" src="http://1.bp.blogspot.com/-5OkYxr59g10/U_Ps-4vV3XI/AAAAAAAAGyQ/RPX1BAd9eHU/s320/Screenshot_2014-08-19-19-14-07.png" /></a>&nbsp;&nbsp;<a href="http://3.bp.blogspot.com/-rqMpr9nysSY/U_Ps-zvhgOI/AAAAAAAAGyM/38M0N_j4i6U/s1600/Screenshot_2014-08-19-19-14-16.png" imageanchor="1"><img border="0" src="http://3.bp.blogspot.com/-rqMpr9nysSY/U_Ps-zvhgOI/AAAAAAAAGyM/38M0N_j4i6U/s320/Screenshot_2014-08-19-19-14-16.png" /></a>&nbsp;&nbsp;<a href="http://2.bp.blogspot.com/-AwjqlrBiAfs/U_Ps-2L_uqI/AAAAAAAAGyI/YJRtC21ocp8/s1600/Screenshot_2014-08-19-19-14-24.png" imageanchor="1"><img border="0" src="http://2.bp.blogspot.com/-AwjqlrBiAfs/U_Ps-2L_uqI/AAAAAAAAGyI/YJRtC21ocp8/s320/Screenshot_2014-08-19-19-14-24.png" /></a><br />
<a href="http://2.bp.blogspot.com/-W5S5LB61fOM/U_PtADkAmWI/AAAAAAAAGys/xFAb3FbYnls/s1600/Screenshot_2014-08-19-19-14-31.png" imageanchor="1"><img border="0" src="http://2.bp.blogspot.com/-W5S5LB61fOM/U_PtADkAmWI/AAAAAAAAGys/xFAb3FbYnls/s320/Screenshot_2014-08-19-19-14-31.png" /></a>&nbsp;&nbsp;<a href="http://2.bp.blogspot.com/-mpoO1PpIZfU/U_PtAbT9NdI/AAAAAAAAGyU/xvDYuIC1nsM/s1600/Screenshot_2014-08-19-19-14-43.png" imageanchor="1"><img border="0" src="http://2.bp.blogspot.com/-mpoO1PpIZfU/U_PtAbT9NdI/AAAAAAAAGyU/xvDYuIC1nsM/s320/Screenshot_2014-08-19-19-14-43.png" /></a>&nbsp;&nbsp;<a href="http://1.bp.blogspot.com/-6FuxqQH1d3E/U_PtBKyjcsI/AAAAAAAAGyY/kc-qMazyk9c/s1600/Screenshot_2014-08-19-19-15-07.png" imageanchor="1"><img border="0" src="http://1.bp.blogspot.com/-6FuxqQH1d3E/U_PtBKyjcsI/AAAAAAAAGyY/kc-qMazyk9c/s320/Screenshot_2014-08-19-19-15-07.png" /></a>
## Installation
You can import the library from source as a module or grab via Gradle:
 <br />
 ```groovy
 compile 'com.williammora:snackbar:1.2.0'
 ```
## Usage
<br />
Using the <code>Snackbar</code> class is easy, this is how you would display it on a <code>HelloWorldActivity</code>:
<br />
```java
Snackbar.with(getApplicationContext()) // context
    .text("Single-line snackbar") // text to display
    .show(this); // activity where it is displayed
```
If you want an action button to be displayed, just assign a label and an <code>ActionClickListener</code>:
<br />
```java
Snackbar.with(getApplicationContext()) // context
    .text("Item deleted") // text to display
    .actionLabel("Undo") // action button label
    .actionListener(new Snackbar.ActionClickListener() {
        @Override
        public void onActionClicked() {
            Log.d(TAG, "Undoing something");
        }
     }) // action button's ActionClickListener
     .show(this); // activity where it is displayed
```
If you need to know when the <code>Snackbar</code> is dismissed, assign a <code>DismissListener</code>:
<br />
```java
Snackbar.with(getApplicationContext()) // context
    .text("This will do something when dismissed") // text to display
    .dismissListener(new Snackbar.DismissListener() {
        @Override
        public void onDismiss() {
            Log.d(TAG, "Snackbar dismissed");
        }
    }) // Snackbar's DismissListener
    .show(this); // activity where it is displayed
```
There are two <code>Snackbar</code> types: single-line (default) and multi-line (2 lines max). You can also set the duration of the <code>Snackbar</code> similar to a <a href="http://developer.android.com/reference/android/widget/Toast.html"><code>Toast</code></a>. Animation disabling is also possible.
<br />
```java
Snackbar.with(getApplicationContext()) // context
    .type(Snackbar.SnackbarType.MULTI_LINE) // Set is as a multi-line snackbar
    .text("This is a multi-line snackbar. Keep in mind that snackbars are " +
        "meant for VERY short messages") // text to be displayed
    .duration(Snackbar.SnackbarDuration.LENGTH_SHORT) // make it shorter
    .animation(false) // don't animate it
    .show(this); // where it is displayed
```
Finally, you can change the <code>Snackbar</code>'s colors.
<br />
```java
Snackbar.with(getApplicationContext()) // context
    .text("Different colors this time") // text to be displayed
    .textColor(Color.GREEN) // change the text color
    .color(Color.BLUE) // change the background color
    .actionLabel("Action") // action button label
    .actionColor(Color.RED) // action button label color
    .actionListener(new Snackbar.ActionClickListener() {
        @Override
        public void onActionClicked() {
            Log.d(TAG, "Doing something");
        }
     }) // action button's ActionClickListener    
    .show(this); // activity where it is displayed
```
It uses [Roman Nurik's SwipeToDismiss sample code](https://github.com/romannurik/android-swipetodismiss) to implement the swipe-to-dimiss functionality.<br /><br />
If you would like to add features to it or report any bugs, refer to the [issues](https://github.com/wmora/snackbar/issues) section.<br /><br />

# Examples
There's a sample app included in the project. [SnackbarSampleActivity](./sample/src/main/java/com/williammora/sample/snackbar/SnackbarSampleActivity.java) is where you want to start.

# Contributors
+ William Mora - [@_williammora](https://twitter.com/_williammora) - william.r.mora@gmail.com
+ [Lewis Deane](https://github.com/lewisjdeane)
+ [Andrew Hughes](https://github.com/ashughes)

## License
[MIT](./LICENSE)