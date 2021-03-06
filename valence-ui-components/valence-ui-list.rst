##################
List
##################

The `vui-list <https://www.npmjs.com/browse/keyword/vui>`_ library contains Less mixins and CSS that you can use to style lists. 

.. role:: example
	
:example:`Examples`

.. raw:: html
  
  <p><strong>Default list with separators and padding</strong></p>
  <div class="vuiexamplebox vui-typography">
    <div class="vui-docs-example">
      <ul class="vui-list">
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li>
      </ul>
    </div>
  </div>

  <p><strong>Compact list with no separators</strong></p>
  <div class="vuiexamplebox vui-typography">
    <div class="vui-docs-example">
      <ul class="vui-list vui-compact vui-no-separator">
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li>
      </ul>
    </div>
  </div>

*********************
Styling with Less 
*********************
If you're familiar with `Less <http://lesscss.org/>`_, you can style lists with our Less mixins.  First, you'll need to import the following library into your Less file:

.. code-block:: console
  
  @import '<npm module path>/vui-list/list';


To apply list styling, call the ``#vui.List()`` mixin within your list's CSS selector:

.. code-block:: css
  
  ul {
    #vui.List();
  }

Lists can be rendered without separators by also calling the ``#vui.List.noSeparator()`` sub-mixin:

.. code-block:: css

  ul {
    #vui.List();
    #vui.List.noSeparator();
  }

To render lists with less padding inside the items, also call the ``#vui.List.compact()`` sub-mixin:

.. code-block:: css

  ul {
    #vui.List();
    #vui.List.compact();
  }

Item States
==================
List items can be in two different states (or a combination of both states),
and we expose different mixins for each state:

- **selected**: This state is reserved for lists that support the selection of items, either with checkboxes or radio buttons.

- **active**: Clickable or selectable items are typically put into this state when the user's mouse hovers over them, or when they receive keyboard focus.

To apply states to list items, call the ``#vui.ListItem.selected()`` and ``#vui.ListItem.active()`` sub-mixins. For items that are both selected and active, call ``#vui.ListItem.selected.active()``.

  .. role:: example
  
:example:`Example`

.. raw:: html

  <div class="vuiexamplebox vui-typography">
    <div class="vui-docs-example2">
      <ul id="liststates" class="vui-compact vui-no-separator">
        <li class="vradio"><label><input type="radio" name="list_group_1" checked /> item 1</label></li>
        <li class="vradio"><label><input name="list_group_1" type="radio" /> item 2</label></li>
        <li class="vradio"><label><input name="list_group_1" type="radio" /> item 3</label></li>
      </ul>
    </div>
  </div>
  <br>


.. code-block:: css
  
  @import '<npm module path>/vui-list/list-item';

  li:hover, li:focus {
    #vui.ListItem.active();
  }

  li.selected {
    #vui.ListItem.selected();
    &:hover, &:focus {
      #vui.ListItem.selected.active();
    }
  }

In this example, we applied the *active* state to any list items that receive focus or hover.  Also, we created a new selector to apply the *selected* state.  Some JavaScript is used to toggle the ``selected`` class when the radio button is checked.

*********************
Styling with CSS
*********************
If you'd prefer to use CSS to style lists, bundle the provided **list.css** file with your application's CSS. 


Apply the ``.vui-list`` class to your list elements:

.. code-block:: css

  <ul class="vui-list">
    <li>item 1</li>
  </ul>


Similar to the Less mixin, you can disable the separators between list items
by adding the ``.vui-no-separator`` class:

.. code-block:: css
	
  <ul class="vui-list vui-no-separator"></ul>

To reduce padding inside the items, apply the ``.vui-compact`` class:

.. code-block:: css

  <ul class="vui-list vui-compact"></ul>

To apply the ``selected`` and ``active`` states to items, use the ``.vui-selected`` and ``.vui-active`` classes.
