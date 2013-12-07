Your Grocer Spree Delivery Date 
=================

This gem is a fork from [spree_delivery_date](from 'https://github.com/sgringwe/spree_delivery_date'), and it has been updated to work with spree_core 2.1.3, as well as other changes. 

Requires user to enter a delivery date and delivery time during checkout (delivery section).

Features
-------

* Delivery date validation
	* Creates a cut off time for deliveries done the day after
	* If order is being done before cut off time, delivery date can be set to the day after
	* If order is after cut off time, delivery date can only be set to the day after + 1

* Shows delivery date and time during checkout confirmation.
* Shows delivery date when viewing or editing order as admin.
* Allows admin to filter orders by delivery date and time (date range).
* Allows admin to sort orders by delivery date and time.
* Adds delivery date column to orders index page table.


Installation
------------

Add the gem to your Gemfile

    $ gem 'yg_spree_delivery_date'

bundle with
  
    $ bundle update

and run

    $ rails g yg_spree_delivery_date:install

to install and (be asken to) run the migrations. This migration simply adds the delivery_date field to Spree::Order.

Configuration
-------------

Both the delivery cut off hour and the delivery time options can be configured in your application.rb file

     config.after_initialize do
        delivery_time_options = {      
          pre_dawn: "Before 6am",        
          early_morning: "Between 6am-8am"
        }.to_json
        YgSpreeDeliveryDate::Config.delivery_time_options = delivery_time_options
        YgSpreeDeliveryDate::Config.delivery_cut_off_hour = 12
      end       

