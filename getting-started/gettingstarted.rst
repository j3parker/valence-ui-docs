.. title:: Getting Started with VUI

We've built the Valence UI libraries on `Less <http://lesscss.org/>`_, which is a CSS pre-processor that allows you to extend the CSS. For most components, we provide both the compiled CSS and Less mixins that you can use to style and customize your app.

All components are available as `npm modules <https://www.npmjs.org/browse/keyword/vui>`_.

************************
Comfortable with CSS?
************************
You can style VUI components by just using plain CSS. For components that include CSS files, just bundle those files with your application.

************************
Comfortable with Less?
************************
If you'd rather use `Less <http://lesscss.org/>`_ to style and customize your app, most VUI components include Less mixins that you can import into your Less files.

************************
Available components
************************
Check out the :doc:`Components <../valence-ui-components/index>` page for a list of available VUI components.

****************************
Installing the components 
****************************
All of the VUI components are available as `npm modules <https://www.npmjs.org/browse/keyword/vui>`_, so you must have `Node.js <http://nodejs.org/>`_ installed.  

To install a component, in your project directory, type the following command:

.. raw:: html

    <pre>npm install vui-<i>componentname</i></pre>

For example, to install the `vui-icons <https://www.npmjs.com/browse/keyword/vui>`_ library, type: ``npm install vui-icons``.

Once installed, the VUI component is available in the ``node-modules`` directory of your project.  

From there you can incorporate the component into your app.  Visit the :doc:`docs <../valence-ui-components/index>` to see how.

****************************
Example
****************************
Here's a simple example to get up and running with VUI. It's just a "Hello World" HTML page that displays a heading, an input field with a label, and a button. We'll include the change tracking component, which is a jQuery-based widget to track form element changes. 

.. raw:: html
    
    <div class="vuiexamplebox">
      <div class="vui-typography">
      <h2 class="docs vui-heading-2">Hello World</h2>
        <form data-track-changes="true">
          <div style="width:600px;" class="tracker vui-field-row">
            <label class="vui-label">
            Name
            <input class="input-tracking vui-input" type="text" />
            </label>
            <button class="vui-button vui-primary">Hello</button>
          </div>
        </form>
      </div>
    </div>
    <br>

1.  From the project directory, we install the VUI components that we'll use in this app:

    .. code-block:: console

      npm install vui-typography
      npm install vui-button
      npm install vui-input
      npm install vui-field
      npm install vui-change-tracking-jquery

2.  We'll style and customize our components by using Less. So, we'll create a *myapp.less* file that contains all the Less goodness and then compile the file into a CSS file.

    .. code-block:: css

      @import '<npm module path>/vui-button/button';
      @import '<npm module path>/vui-typography/typography';
      @import '<npm module path>/vui-field/field';
      @import '<npm module path>/vui-field/label';
      @import '<npm module path>/vui-input/input';
      @import '<npm module path>/vui-change-tracking-jquery/changeTracking';

      body {
        #vui.Typography();
      }
      h1 {
        #vui.Heading1();
      }
      button, input[type=button]   {
        #vui.Button();
      }
      button.primary {
        #vui.Button.primary();
      }
      .myFieldRow {
        #vui.FieldRow();
      }
      .myFieldRow label {
        #vui.Label();
      }
      input
      {
        #vui.Input();
      }
      .vui-changed {
        #vui.changed();
      }

3.  We'll create a simple HTML file to display page and its details.  Notice that because we are using :doc:`change tracking <../valence-ui-components/valence-ui-jquery-change-tracking>`, which is a jQuery-based widget, we need to include `jQuery <http://jquery.com/>`_ and `jQuery UI <http://jqueryui.com/>`_.

    .. code-block:: html

      <html lang="en">
        <head>
          ...       
          <link href="myapp.css" rel="stylesheet">
        </head>
        <body>
          <h2>Hello World</h2>
            <form data-track-changes="true">
              <div class="tracker myFieldRow">
                <label>
                  Name
                  <input class="input-tracking" type="text" />
                </label>
                <button class="primary">Hello</button>
              </div>
            </form>
        
          <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js"></script>
          <script src="http://ajax.googleapis.com/ajax/libs/jqueryui/1.10.3/jquery-ui.min.js"></script>
          <script src="node_modules/vui-change-tracking-jquery/changeTracking.js"></script>
          <script src="node_modules/vui-change-tracking-jquery/changeTracker.js"></script>
          <script>
            $(function () {
              $( '.tracker' ).vui_changeTracker();
              $( '.input-tracking' ).vui_changeTracking();
            });
          </script>
        </body>
      </html>

4.  Now, just load the HTML page into your browser.

