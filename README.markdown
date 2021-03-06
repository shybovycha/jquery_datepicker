# jQuery Datepicker Rails plugin

This simple gem allows you to add a date picker field into your views.

## Getting Started

### Rails 3.1 and higher:

* Insert into your `Gemfile`:

        gem 'jquery_datepicker'

* If you are using Rails 3.1 with the asset pipeline enabled (default), the necessary files are already in your asset pipeline. Just add (if they are not already there) to your `app/assets/javascripts/application.js`:

        //= require jquery
        //= require jquery-ujs
        //= require jquery.ui.datepicker

  If you want to use datetime picker as well, add these:

        //= require jquery-ui-timepicker-addon.js

  You can find it here: [https://github.com/trentrichardson/jQuery-Timepicker-Addon](https://github.com/trentrichardson/jQuery-Timepicker-Addon)

* Be sure to recompile your assets to apply the changes

        rake assets:precompile:all RAILS_ENV=production

  or just

        rake assets:precompile:all

### Rails 3.0 and lower:

* Add into your `Gemfile`:

        gem 'jquery-rails'

* Execute this command to install the needed js files:

        rails generate jquery:install --ui


* Insert into your Gemfile:

        gem 'jquery_datepicker'

  Don't forget to install the CSS!

## Usage

Add this to your view.

    <%= datepicker_input "user", "birthday" %>

Where "user" is your model name and "birthday" the name of the datefield.

You can also use it with the form helper like:

    <% form_for(@user) do |f| %>
      <%= f.datepicker 'birthday' %>
      <%= f.submit 'Create' %>
    <% end %>

Nested attributes are permitted as well:

    <% form_for(@user) do |f| %>

      <% f.fields_for(@nested) do |f2| %>
        <%= f2.datepicker 'birthday' %>
      <% end %>

      <%= f.submit 'Create' %>
    <% end %>

You can pass options as it would be a normal text_field, plus all the datepicker options available [http://jqueryui.com/demos/datepicker/#options](http://jqueryui.com/demos/datepicker/#options)

    <%= datepicker_input(:my_model, :my_attribute, :minDate => -20, :maxDate => "+1M +10D", :tabindex => 70) %>

For example, to use the different date format in the input, use this:

    <%= datepicker_input(:my_model, :my_attribute, :dateFormat => 'dd.mm.yy') # e.g. 29.11.2012 %>

You could also use `:minDate`, `:maxDate` and `:defaultDate` options with standard Ruby' `DateTime` object:

    <%= datepicker_input(:my_model, :my_attribute, :minDate => DateTime.now) # e.g. 29.11.2012 %>

## Use DateTime picker

If you want to use a datatime picker, download this plugin [https://github.com/trentrichardson/jQuery-Timepicker-Addon](https://github.com/trentrichardson/jQuery-Timepicker-Addon)

and add it to your project (in the assets pipeline if you are using Rails 3.1 or manually otherwise).
Don't forget the CSS! This plugin assume you have installed a jquery-ui theme.

Then you can use in your views:

    <%= datetime_picker_input "user","loged_in", :dateFormat => "yy-mm-dd" %>

or

    <% form_for(@user) do |f| %>
      <%= f.datetime_picker 'loged_in', :dateFormat => "yy-mm-dd" %>
      <%= f.submit 'Create' %>
    <% end %>

## Important notes

Be aware the way Rails stores the datetime fields cause you'll need to specify the dateFormat to `"yy-mm-dd"` or pre-process your field value on the controller. The default format won't work.

## Support

Open an issue in [https://github.com/albertopq/jquery_datepicker](https://github.com/albertopq/jquery_datepicker) if you need further support or want to report a bug
