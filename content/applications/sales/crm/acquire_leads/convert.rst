================================
Convert leads into opportunities
================================

*Leads* act as qualifying steps before an opportunity is created. This allows for additional time
before a potential opportunity is assigned to a sales person.

Configuration
=============

To activate the *leads* setting, navigate to :menuselection:`CRM --> Configuration --> Settings`
and check the box labeled :guilabel:`Leads`. Click :guilabel:`Save`.

.. image:: convert/convert-leads-leads-setting.png
    :align: center
    :alt: Leads setting on CRM configuration page.

This adds a new menu, :guilabel:`Leads`, to the menu bar at the top of the screen.

.. image:: convert/convert-leads-leads-menu.png
    :align: center
    :alt: Leads menu on CRM application.

Once the *leads* setting has been activated, it will apply to all sales teams by default. To turn
off leads for a specific team, navigate to :menuselection:`Configuration --> Sales Team`. Select a
team from the list to open the record, then uncheck the :guilabel:`Leads` box. Click
:guilabel:`Save`.

   .. image:: convert/convert-leads-leads-button.png
       :align: center
       :alt: Leads menu on CRM application.

Convert a lead into an opportunity
==================================

To convert a lead into an *opportunity*, navigate to :menuselection:`CRM --> Leads` and click on a
:guilabel:`Lead` from the list to open it. In the upper-left corner of the screen, click the
:guilabel:`Convert to Opportunity` button, which opens a pop-up window.

.. image:: convert/convert-leads-convert-opp-button.png
    :align: center
    :alt: Create opportunity button on a lead record.

In the :guilabel:`Conversion action` field, select :guilabel:`Convert to opportunity`.

.. note::
   If a lead or an opportunity already exists in the database with this customer, Odoo will
   automatically suggest to merge with that lead/opportunity. For more information on merging leads
   and opportunities, :ref:`Merge leads <sales/crm/acquire_leads/merge-leads>` below.

Select a :guilabel:`Salesperson` and a :guilabel:`Sales Team` to assign the opportunity to. If the
lead has already been assigned to a sales person or a team, these fields will automatically populate
with that information.

.. image:: convert/convert-leads-conversion-action.png
    :align: center
    :alt: Create opportunity pop-up.

Under the :guilabel:`Customer` heading, choose from the following options:
- :guilabel:`Create a new customer`: This option creates a new customer record using the information
   provided on the lead record.
- :guilabel:`Link to an existing customer`: Choose a customer from the drop-down menu to link this
   opportunity.
- :guilabel:`Do not link to a customer`:

.. _sales/crm/acquire_leads/merge-leads:

Merge leads and opportunities
=============================

Odoo will also automatically propose to merge opportunities if they have the same email address.
When merging opportunities, Odoo merges the information into the opportunity which was created
first, giving priority to the information present on the first opportunity.

.. image:: convert/convert-leads-similar-leads.png
    :align: center
    :alt: Similar leads smart button.

No information is lost: data from the other opportunity is logged in the chatter and the information
fields for easy access.

Would you find a duplicate yourself, ...you can also merge opportunities or leads even if the system
doesn't propose it.

Here's how, from the list view. Select the opportunities or leads you want to merge and the action
button will appear. Then, you can select merge.

.. image:: convert/convert-leads-merge.png
    :align: center
    :alt: Merge option from action menu in list view.

.. note::
   It is also possible to merge more than 2 opportunities or leads.
