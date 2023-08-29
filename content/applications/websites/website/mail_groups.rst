============
Mail groups
============

The **Mail groups** feature in the **Website** app allows website visitors to have a public
discussion by email. They can join a list to reply to emails, send new messages, etc. and all
members of the mailing lists (i.e. people who have subscribed to the list) will receive the message
by email.

Mailing lists messages are accessible from the website at `/groups` by selecting the mailing list
Users can subscribe or unsubscribe from mailing list from `/groups`

To activate mail groups for your website, :ref:`install <general/install>` the :guilabel:`Website
Mail Group` (`website_mail_group`) module.

When a message has been sent to the mailing list address, it will be sent to everyone that's part of
the list and also be displayed for those users on the website portal /groups
.. note::
   The **Mailing lists** feature in the **Website** app is not to be confused with the
   :doc:`../marketing/email_marketing/mailing_lists` in the Email marketing app.

Configure mail groups
---------------------

To configure mail groups, proceed as follows:

#.Configure a custom email alias domain: Access the **General settings**, scroll down to the
  :guilabel:`Discuss` section, enable the :guilabel:`Custom Email Server` feature, and enter the
  :guilabel:`Alias domain` (e.g., `@mycompany.com`).
#. Go to :menuselection:`Website --> Groups --> Mailing list groups`, then click :guilabel:`Create`.
#. Specify a :guilabel:`Group name`, the :guilabel:`Email alias` and a :guilabel:`Description` for
   the mailing list.
#. Enable :guilabel:`Moderate this group` and specify the :guilabel:`Moderators` if you wish to
   :ref:`moderate messages <website/mailing_lists/moderate> from this list`. Alternatively, if the
   list is not moderated, you can define :guilabel:`Responsible users` who can manage the messages
   in the list.
#. In the :guilabel:`Privacy` tab, define who can subscribe to the mailing list:
   - :guilabel:`Everyone`: to make the mailing list public so anyone can subscribe and see the list;
   - :guilabel:`Members only`: to only allow users defined as members to subscribe to see the list;
   - :guilabel:`Selected group of users`: select the :guilabel:`Authorized group` from the dropdown
     list.
#. If the mailing list is moderated, you can automatically notify authors when their message
   is pending moderation by enabling :guilabel:`Automatic notification` in the :guilabel:`Notify
   members` tab and writing the :guilabel:`Notification message`.
#. If you wish to send out guidelines to new subscribers, enable :guilabel:`Send guidelines to new
   subscribers` and write the :guilabel:`Guidelines` in the :guilabel:`Guidelines` tab. This is
   particularly useful when the mailing list is moderated.

--> need to find out the difference between the two


- When the group is public, everyone can send email to the mailing list, but if the group is not public,
only member can send emails (it change the "Alias Contact Security" on the related alias to "Followers")
-
- The "unsubscribe" URLs in the footer of the email sent contains a token, so even if the current
member is not logged / not related to a partner, he's able to unsubscribe

example:
Mailing-List: https://test-auva1.odoo.com/groups/my-mailing-list-1

Post to: mylist@test-auva1.odoo.com

Unsubscribe: https://test-auva1.odoo.com/groups?unsubscribe

Internal users can join/leave a mailing list from :menuselection:`Website --> Groups -->
Mailing List Groups` using the related buttons. or using the URL in the email (see above)

.. _website/mailing_lists/moderate:

Moderating mailing list messages
--------------------------------

If the :guilabel:`Moderate this group` feature has been enabled for the mailing list, the mailing
list's messages need to be approved by one of the :guilabel:`Moderators` field before they are
dispatched to the other members.

To moderate messages, go to :menuselection:`Website --> Groups`. Select the mailing list for which
you wish to review messages and click the :guilabel:`To review` smart button. From there, select a
message and moderate it using the buttons:

- :guilabel:`Accept`: to accept the email and send it to the mailing list members
- :guilabel:`Reject`: to reject the email. In the pop-up window that opens, click
  :guilabel:`Reject Silently` to reject the email without notifying the author, or specify an
  explanation for rejecting the message, then click :guilabel:`Send & Reject` to reject the message
  and send the explanation to the author.
- :guilabel:`Whitelist`: to accept the email, as well as all other pending emails from the same
  author whitelist the author's email address. As a result, a moderation rule is created for the
  author's email address with the status "Always allow".
- :guilabel:`Ban`: to discard the email as well as all other pending emails from the same author
  and blacklist the author's email address. In the pop-up window that opens, click :guilabel:`Ban`
  to ban the author without notifying them, or specify an explanation, then click
  :guilabel:`Send & Ban` to ban the author and send them the explanation. As a result, a moderation
  rule is created for the author's email address with the status "Permanent ban".

.. note::
   The buttons are also available directly from the list of messages, or the list of messages to
   review, at the end of the message line.

   .. image:: mail_groups/mailing-list-moderation.png
      :alt: Moderation buttons in the message line.

Whitelisting/Blacklisting authors
---------------------------------

You can whitelist or blacklist an author either directly :ref:`from a mailing list message
<website/mailing_lists/moderate>` or by creating a moderation rule. To do so, go to
:menuselection:`Website --> Groups --> List moderation rulings` and click :guilabel:`Create`. Then,
selecting the :guilabel:`Group`, specify the author's :guilabel:`Email` and set the
:guilabel:`Status` field.

.. tip::
   You can also access the mailing list's moderation rules by going to :menuselection:`Website -->
   Groups --> Mailing list groups`, selecting the list, then clicking the :guilabel:`Moderations`
   smart button.