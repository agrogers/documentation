=====
Chile
=====

Webinars
========

The videos below show a general description of the localization and the tutorials show specific
useful workflows while using Odoo in Chile.

- `Webinar recording: Chilean localization intro and demo <https://youtu.be/BHnByZiyYcM>`_.
- `Webinar recording: Chilean localization delivery guide <https://youtu.be/X7i4PftnEdU>`_.
- `Chile localization: playlist of tutorials
  <https://youtube.com/playlist?list=PL1-aSABtP6AB6UY7VUFnVgeYOaz33fb4P>`_.

.. seealso::
   - `App Tour - Localización de Chile <https://www.youtube.com/watch?v=3qYkgbmBYHw>`_
   - `Smart Tutorial - Localización de Chile
     <https://www.odoo.com/slides/smart-tutorial-localizacion-de-chile-131>`_

.. _chile/configuration:

Configuration
=============

:ref:`Install <general/install>` the following modules to get all the features of the Chilean
localization.

.. list-table::
   :header-rows: 1

   * - Name
     - Technical name
     - Description
   * - :guilabel:`Chile - Accounting`
     - `l10n_cl`
     - Adds accounting features for the Chilean localization, which represent the minimal
       configuration required for a company to operate in Chile and under the SII (Servicio de
       Impuestos Internos) regulations and guidelines.
   * - :guilabel:`Chile - Accounting Reports`
     - `l10n_cl_reports`
     - Adds the reports Propuesta F29 y Balance Tributario (8 columnas).
   * - :guilabel:`Chile - E-invoiving`
     - `l10n_cl_edi`
     - Includes all technical and functional requirements to generate and receive electronic invoice
       via web service, based on the :abbr:`SII (Servicio de Impuestos Internos)` regulations.
   * - :guilabel:`Chile - Electronic Receipt`
     - `l10n_cl_boletas`
     - Includes all technical and functional requirements to generate and receive electronic
       receipts via web service, based on the :abbr:`SII (Servicio de Impuestos Internos)`
       regulations.
   * - :guilabel:`Electronic Esports of Goods for Chile`
     - `l10n_cl_edi_exports`
     - Includes all technical and functional requirements to generate electronic invoices for
       exporting goods, based on the :abbr:`SII (Servicio de Impuestos Internos)` and customs
       regulations.
   * - :guilabel:`Chile - E-Invoicing Delivery Guide`
     - `l10n_cl_edi_stock`
     - Includes all technical and functional requirements to generate delivery guides via web
       service, based on the :abbr:`SII (Servicio de Impuestos Internos)` regulations.
   * - :guilabel:`Chile - E-Invoicing Delivery Guide`
     - `l10n_cl_edi_stock`
     - Includes all technical and functional requirements to generate delivery guides via web
       service, based on the :abbr:`SII (Servicio de Impuestos Internos)` regulations.

.. note::
   - Odoo automatically installs the appropriate package for your company, according to the country
     selected at the creation of the database.
   - The module *Chile - E-Invoicing Delivery Guide* is dependent on the *Inventory* application.

.. important::
   All the following configuration and functionality is only available in Odoo if your company
   already passed the `Certification process
   <https://www.sii.cl/factura_electronica/factura_mercado/proceso_certificacion.htm>`_ in the
   :abbr:`SII (Servicio de Impuestos Internos)` - Sistema de Facturación de Mercado, this
   certification enables you to generate electronic invoices from your ERP and send them
   automatically to the :abbr:`SII (Servicio de Impuestos Internos)`. If your company has not passed
   this certification yet, make sure you communicate this to your Account Manager as a special
   process outside Odoo is required in order to complete this certification.

Accounting settings
-------------------

Begin by setting up the company data. To do so, navigating to :menuselection:`Settings -->
Companies: Update Info`. Then, edit the contact form to configure the following information:

- Company name.
- :guilabel:`Address`: Including :guilabel:`City`, :guilabel:`State`, and :guilabel:`ZIP` code.
- :guilabel:`Tax ID`: Enter the identification number for the selected *Taxpayer Type*.
- :guilabel:`Activity Names`: A maximum of four activity codes can be registered.
- :guilabel:`Company Activity Description`: Enter an activity description for the company.

Next, configure *electronic invoicing* by going to :menuselection:`Accounting --> Configuration -->
Settings --> Chilean Localization section`. Follow the instructions to configure the :ref:`fiscal
information <chile/fiscal-info>`, :ref:`electronic invoice data <chile/electronic-invoice>`,
:ref:`DTE incoming email server <chile/dte-email>`, and :ref:`signature certificates
<chile/certificate>`.

.. _chile/fiscal-info:

Fiscal information
~~~~~~~~~~~~~~~~~~

Fill in the required fiscal information for your company. First configure the following fields for
your company in the :guilabel:`Tax payer information` section:

- :guilabel:`Taxpayer`: Select the taxpayer type that applies to your company.

  - `VAT Affected (1st Category)`: Used in most cases.
  - `Fees Receipt Issuer (2nd Category)`: Applies to suppliers who issue fees receipt.
  - `End consumer`: Only issues receipts.
  - `Foreigner`.

- :guilabel:`SII Office`: :abbr:`SII (Servicio de Impuestos Internos)` regional office fields for
  your company.

.. _chile/electronic-invoice:

Electronic invoice data
~~~~~~~~~~~~~~~~~~~~~~~

In order to generate electronic invoices, the following configuration is required. First, select
your environment from the :guilabel:`SII Web Services` section:

- :guilabel:`SII - Test`: Select this option if using a testing database.
- :guilabel:`SII - Production`: Select this option only if using the database in production.
- :guilabel:`SII - Demo Mode`: Avoid selecting this option in a production database.

Then configure the :guilabel:`SII Resolution N°` and :guilabel:`SII Resolution Date` legal
information in the :guilabel:`Legal Electronic Invoicing Data` section.

.. image:: chile/electronic-invoice-data.png
   :alt: Required information for electronic invoice.

.. _chile/dte-email:

DTE incoming email server
~~~~~~~~~~~~~~~~~~~~~~~~~

In order to receive the claim and acceptance emails from your customers, it is required to define
the :abbr:`DTE (Documentos Tributarios Electrónicos)` incoming email server. To do so, select
:guilabel:`Configure DTE Incoming Email` from the :guilabel:`Email Box Electronic Invoicing`
section. Then, select the :guilabel:`New` button to begin the configuration:

- :guilabel:`Name`: Title the incoming mail server.
- :guilabel:`Server Type`:

  - :guilabel:`IMAP Server`
  - :guilabel:`POP Server`
  - :guilabel:`Local Server`
  - :guilabel:`Gmail OAuth Authentication`

- :guilabel:`DTE Server`: Check this option to configure the server to receive electronic invoices.

In the :guilabel:`Server & Login` tab, fill in the following:

- :guilabel:`Server Name`: The hostname or IP of the server.
- :guilabel:`Port`: The server port.
- :guilabel:`SSL/TLS`: Check this option if connections are encrypted with.
- :guilabel:`Username`: Server login username.
- :guilabel:`Password`: Server login password.

.. image:: chile/dte-incoming-email.png
   :alt: Incoming email server configuration for Chilean DTE.

.. tip::
   Before going live, make sure you archive/remove all the emails related to vendor bills that are
   not required to be processed in Odoo from your inbox.

.. _chile/certificate:

Certificate
~~~~~~~~~~~

In order to generate the electronic invoice signature, a digital certificate with the extension
:file:`.pfx` is required, proceed to select :guilabel:`Configure Signature Certificates` from the
:guilabel:`Signature Certificates` section. Then, select the :guilabel:`New` button to begin the
configuration. On the certificate form, upload your :guilabel:`Certificate Key` and enter your
:guilabel:`Certificate Passkey`.

A certificate can be shared between several users. If this is the case leave the user field empty,
so all your billing users can use the same one. On the other hand, if you need to restrict the
certificate for a particular user, just define the users in the certificate.

.. note::
   In some cases, depending on the certificate format, it is possible that the field
   :guilabel:`Subject Serial Number` is not loaded automatically. If this is the case, you can
   manually edit this field by filling it with the Certificate's legal representative RUT.

.. image:: chile/new-certificate.png
   :alt: Digital certificate configuration.

Multicurrency
-------------

The official currency rate in Chile is provided by the Chilean service `mindicador.cl
<https://mindicador.cl>`_. This service can be managed from :menuselection:`Settings --> Accounting
--> Currencies`. A predefined interval for the rate updates can be configured by selecting an
:guilabel:`Interval` in the :guilabel:`Automatic Currency Rates` section and setting the
:guilabel:`Service` to `Chilean minidicador.c`.

.. image:: chile/currency-rate-config.png
   :alt: Currency rate configurator for Chile.

Chart of accounts
-----------------

The :doc:`chart of accounts <../accounting/get_started/chart_of_accounts>` is installed by default
as part of the set of data included in the localization module. The accounts are mapped
automatically in:

- Taxes.
- Default Account Payable.
- Default Account Receivable.
- Transfer Accounts.
- Conversion Rate.

Master data
-----------

Partner
~~~~~~~

To create a new partner contact, navigate to :menuselection:`Contacts --> New`. Then, on the partner
form, complete the following required fields.

Identification type and VAT
***************************

As part of the Chilean localization, the identification types defined by the :abbr:`SII (Servicio de
Impuestos Internos)` are now available on the partner form. This information is essential for most
transactions. Select an :guilabel:`Identification Number` for the partner contact.

Taxpayer type
*************

In Chile, the document type associated with customers and vendors transactions is defined based on
the :guilabel:`Taxpayer Type`. This field should be defined in the partner form.

Electronic invoice data
***********************

As part of the information sent in the electronic invoice, the :guilabel:`Activity Description`
needs to be defined. Next, from the :guilabel:`Electronic Invoicing` tab, configure the
:guilabel:`DTE Email` that will appear as the sender to the customer as well as select the
:guilabel:`Delivery Guide Price`:

- :guilabel:`From Sales Order`: Delivery guide takes the product price from the sales order and
  shows it on the document.
- :guilabel:`From Product Template`: Odoo takes the price configured in the product template and
  shows it on the document.
- :guilabel:`Do Not Show price`: No price is shown in the delivery guide.

.. image:: chile/dte-email-electronic-invoice.png
   :alt: Chilean electronic invoice data for partners.

Taxes
~~~~~

As part of the localization module, the taxes are created automatically with their related financial
account and configuration. These taxes can be managed from :menuselection:`Accounting -->
Configuration --> Taxes`.

.. image:: chile/sales-purchase-taxes.png
   :alt: Chilean Sales and Purchase Taxes.

Tax types
*********

Chile has several tax types, the most common ones are:

- VAT: Is the regular VAT and it can have several rates.
- ILA (Impuesto a la Ley de Alcholes): Taxes for alcoholic drinks. It has a different rate.

Fiscal positions
~~~~~~~~~~~~~~~~

Based on the purchase transactions, the VAT can have different affections. This will be done in Odoo
using the default purchase fiscal positions.

Document types
~~~~~~~~~~~~~~

In some Latin American countries, including Chile, some accounting transactions like invoices and
vendor bills are classified by document types defined by the government fiscal authorities (in
Chile's case, the :abbr:`SII (Servicio de Impuestos Internos)`).

The document type is essential information that needs to be displayed in the printed reports and
needs to be easily identified within the set of invoices as well as account moves.

Each document type can have a unique sequence per company. As part of the localization, the document
type includes the country on which the document is applicable, and the data is created automatically
when the localization module is installed.

Document types can be managed from :menuselection:`Accounting --> Configuration --> Document Types`.
The information required for the document types is included by default, so the user doesn't need to
fill anything on this view.

.. image:: chile/chilean-document-types.png
   :alt: Chilean fiscal document types list.

.. note::
   There are several document types that are inactive by default but can be activated if needed by
   toggling the :guilabel:`Active` option for the record.

Use on invoices
***************

The document type on each transaction will be determined by:

- The journal related to the invoice, identifying if the journal uses documents.
- Condition applied based on the type of issuer and recipient (ex. Type of fiscal regime of the
  buyer and type of fiscal regime of the vendor).

Journals
--------

*Sales journals* in Odoo usually represent a business unit or location.

.. example::
   - Ventas Santiago.
   - Ventas Valparaiso.

For retail stores it is common to have one journal per :abbr:`POS (Point of Sale)`.

.. example::
   - Cashier 1.
   - Cashier 2.

The *purchase* transactions can be managed with a single journal, but sometimes companies use more
than one journal in order to handle some accounting transactions that are not related to vendor
bills. This configuration can easily be set by using the following model.

.. example::
   - Tax payments to the government.
   - Employees payments.

Configuration
~~~~~~~~~~~~~

To create a sales journal, navigate to :menuselection:`Accounting --> Configuration --> Journals`.
Then, fill in the following required information:

- :guilabel:`Type`: Select `Sale` for customer invoice journals.
- :guilabel:`Point of sale type`: If the sales journal will be used for electronic documents, the
  option :guilabel:`Online` must be selected. Otherwise, if the journal is used for invoices
  imported from a previous system or if you are using the :abbr:`SII (Servicio de Impuestos
  Internos)` portal *Facturación MiPyme*, you can use the option :guilabel:`Manual`.
- :guilabel:`Use Documents`: Check this field if the journal will use document types. This field is
  only applicable to purchase and sales journals that can be related to the different sets of
  document types available in Chile. By default, all the sales journals created will use documents.

Next, from the :guilabel:`Jounal Entries` tab, define the :guilabel:`Default Income Account` and
:guilabel:`Dedicated Credit Note Squence` in the :guilabel:`Accounting Information` section.
Configuring these fields is required for one of the debit notes :ref:`use cases <chile/use-cases>`.

.. _chile/caf-documentation:

CAF
---

A CAF (Folio Authorization Code) is required for each document type that will be issued
electronically. The :abbr:`CAF (Folio Authorization Code)` is a file the :abbr:`SII (Servicio de
Impuestos Internos)` provides to the issuer with the folios/sequences authorized for the electronic
invoice documents.

Your company can make several requests for folios and obtain several :abbr:`CAF (Folio Authorization
Code)`s, each one associated with different ranges of folios. The :abbr:`CAF (Folio Authorization
Code)`s are shared within all the journals, this means that you only need one active :abbr:`CAF
(Folio Authorization Code)` per document type and it will be applied on all journals.

Please refer to the `SII documentation <https://palena.sii.cl/dte/mn_timbraje.html>`_ to check the
details on how to acquire the :abbr:`CAF (Folio Authorization Code)` files.

.. important::
   The :abbr:`CAFs (Folio Authorization Code)` required by the :abbr:`SII (Servicio de Impuestos
   Internos)` are different from production to test (certification mode). Make sure you have the
   correct :abbr:`CAF (Folio Authorization Code)` set depending on your environment.

Configuration
~~~~~~~~~~~~~

Once the :abbr:`CAF (Folio Authorization Code)` files have been acquired from the :abbr:`SII
(Servicio de Impuestos Internos)` portal, they need to be uploaded in the database by navigating to
:menuselection:`Accounting --> Chilean SII --> CAFs`. Then, click the :guilabel:`New` button to
begin the configuration. On the :abbr:`CAF (Folio Authorization Code)` form, upload your :abbr:`CAF
(Folio Authorization Code)` file by clicking the :guilabel:`Upload your file` button and then click
:guilabel:`Save`.

Once uploaded, the status changes to :guilabel:`In Use`. At this moment, when a transaction is used
for this document type, the invoice number takes the first folio in the sequence.

.. important::
   The document types have to be active before uploading the :abbr:`CAF (Folio Authorization Code)`
   files. In case some folios have been used in the previous system, the next valid folio has to be
   set when the first transaction is created.

Usage and testing
=================

Electronic invoice workflow
---------------------------

In the Chilean localization the electronic invoice workflow covers the emission of customer invoices
and the reception of vendor bills. In the next diagram, it is explained how the information is
transmitted to the :abbr:`SII (Servicio de Impuestos Internos)`, customers and vendors.

.. image:: chile/electronic-invoice-workflow.png
   :alt: Diagram with Electronic invoice transactions.

Customer invoice emission
-------------------------

After the partners and journals are created and configured, the invoices are created in the standard
way. For Chile, one of the differences is the document type that is automatically selected based on
the taxpayer. The document type can be changed manually if needed on the invoice by navigating to
:menuselection:`Accounting --> Customers --> Invoices`.

.. image:: chile/customer-invoice-document-type.png
   :alt: Customer invoice document type selection.

.. important::
   :guilabel:`Documents type 33` electronic invoice must have at least one item with tax, otherwise
   the :abbr:`SII (Servicio de Impuestos Internos)` rejects the document validation.

.. _chile/electronic-invoice-validation:

Validation and DTE status
~~~~~~~~~~~~~~~~~~~~~~~~~

When all the invoice information is filled, either manually or automatically when it's created from
a sales order, proceed to validate the invoice. After the invoice is posted:

- The :abbr:`DTE (Documentos Tributarios Electrónicos)` file (Electronic Tax Document) is created
  automatically and added in the :guilabel:`chatter`.
- The :abbr:`DTE (Documentos Tributarios Electrónicos)` :abbr:`SII (Servicio de Impuestos Internos)`
  status is set as :guilabel:`Pending` to be sent.

  .. image:: chile/xml-creation.png
       :alt: DTE XML File displayed in chatter.

The :abbr:`DTE (Documentos Tributarios Electrónicos)` status is updated automatically by Odoo with a
scheduled action that runs every day at night, if the response from the :abbr:`SII (Servicio de
Impuestos Internos)` is needed immediately, you can do it manually as well by following the
:abbr:`DTE (Documentos Tributarios Electrónicos)` status workflow:

.. image:: chile/dte-status-flow.png
   :alt: Transition of DTE status flow.

#. The first step is sending the :abbr:`DTE (Documentos Tributarios Electrónicos)` to the :abbr:`SII
   (Servicio de Impuestos Internos)`. This can be sent manually by clicking the :guilabel:`Enviar
   Ahora` button. This will generate a :guilabel:`SII Tack number`and assign it to the invoice, this
   number can be used to check the details the :abbr:`SII (Servicio de Impuestos Internos)` sends
   back by email. Then, the :guilabel:`DTE status` is updated to :guilabel:`Ask for Status`.
#. Once the :abbr:`SII (Servicio de Impuestos Internos)` response is received, Odoo updates the
   :guilabel:`DTE status`. To do it manually, click on the button :guilabel:`Verify on SII`. The
   result can either be :guilabel:`Accepted`, :guilabel:`Accepted With Objection` or
   :guilabel:`Rejected`.

   .. image:: chile/dte-status-steps.png
      :alt: Identification transaction for invoice and Status update.

   .. important::
      There are several internal status in the :abbr:`SII (Servicio de Impuestos Internos)` before
      you get acceptance or rejection. Continuously clicking the button :guilabel:`Verify in SII`
      will log the intermediate statuses in the chatter. These internal statuses take a few seconds
      of processing time. To avoid any issues, it is recommended to **not** continuously click the
      :guilabel:`Verify in SII` button so the flow can work smoothly.

      .. image:: chile/chatter-internal-statuses.png
         :alt: Electronic invoice data statuses.

#. The final response from the :abbr:`SII (Servicio de Impuestos Internos)` can take on of these
   values:

   - :guilabel:`Accepted`: Indicates the invoice information is correct, our document is now
     fiscally valid and it's automatically sent to the customer.
   - :guilabel:`Accepted with objections`: Indicates the invoice information is correct, but a minor
     issue was identified, nevertheless the document is now fiscally valid and it's automatically
     sent to the customer.
   - :guilabel:`Rejected`: Indicates the information in the invoice is incorrect and needs to be
     corrected, the detail of the issue is received in the emails you registered in the :abbr:`SII
     (Servicio de Impuestos Internos)`, if it is properly configured in Odoo, the details are also
     retrieved in the chatter once the email server is processed.

     If the invoice is rejected please follow these steps:

      - Change the document to :guilabel:`Draft`.
      - Make the required corrections based on the message received from the :abbr:`SII (Servicio de
        Impuestos Internos)` in the chatter.
      - Post the invoice again.

     .. image:: chile/rejected-invoice.png
        :alt: Message when an invoice is rejected.

Crossed references
~~~~~~~~~~~~~~~~~~

When the invoice is created as a result of another fiscal document, the information related to the
originator document must be registered in the :guilabel:`Cross-Reference` tab, which is commonly
used for credit or debit notes, but in some cases can be used on customer invoices as well. In the
case of the credit and debit notes, they are set automatically by Odoo.

.. image:: chile/cross-reference-tab-registration.png
   :alt: Crossed referenced document(s).

.. _chile/electronic-invoice-pdf-report:

Invoice PDF report
~~~~~~~~~~~~~~~~~~

Once the invoice is accepted and validated by the :abbr:`SII (Servicio de Impuestos Internos)` and
the PDF is printed, it includes the fiscal elements that indicate that the document is fiscally
valid:

.. image:: chile/sii-validation-elements.png
   :alt: SII Validation fiscal elements.

.. important::
   If you are hosted in Odoo SH or On-Premise, you should manually install the :guilabel:`pdf417gen`
   library. Use the following command to install it: :command:`pip install pdf417gen`.

Commercial validation
~~~~~~~~~~~~~~~~~~~~~

Once the invoice has been sent to the customer:

#. :guilabel:`DTE Partner Status` changes to :guilabel:`Sent`.
#. The customer must send a reception confirmation email.
#. Subsequently, if all the commercial terms and invoice data are correct, they will send the
   acceptance confirmation, otherwise they send a claim.
#. The field :guilabel:`DTE Acceptance Status` is updated automatically.

.. image:: chile/partner-dte-status.png
   :alt: Message with the commercial acceptance from the customer.

Processed for claimed invoices
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Once the invoice has been accepted by the :abbr:`SII (Servicio de Impuestos Internos)`, **it can not
be cancelled in Odoo**. In case you get a claim for your customer, the correct way to proceed is
with a credit note to either cancel the invoice or correct it. Please refer to the
:ref:`chile/credit-notes` section for more details.

.. image:: chile/accepted-invoice.png
   :alt: Invoice Commercial status updated to claimed.

Common errors
~~~~~~~~~~~~~

There are multiple reasons behind a rejection from the :abbr:`SII (Servicio de Impuestos Internos)`,
but these are some of the common errors you might have and how to solve them:

- | **Error:** `RECHAZO- DTE Sin Comuna Origen`
  | **Hint:** Make sure the company address is properly filled including the state and city.
- | **Error:** `en Monto - IVA debe declararse`
  | **Hint:** The invoice lines should include one VAT tax, make sure you add one on each invoice
    line.
- | **Error:** `Rut No Autorizado a Firmar`
  | **Hint:** The RUT entered is not allowed to invoice electronically, make sure the company RUT is
    correct and is valid in the :abbr:`SII (Servicio de Impuestos Internos)` to invoice
    electronically.
- | **Error:** `Fecha/Número Resolucion Invalido RECHAZO- CAF Vencido : (Firma_DTE[AAAA-MM-DD] -
    CAF[AAAA-MM-DD]) &gt; 6 meses`
  | **Hint:** Try to add a new CAF related to this document as the one you're using is expired.
- | **Error:** `Element '{http://www.sii.cl/SiiDte%7DRutReceptor': This element is not expected.
    Expected is ( {http://www.sii.cl/SiiDte%7DRutEnvia ).`
  | **Hint:** Make sure the field :guilabel:`Document Type` and :guilabel:`VAT` are set in the
    customer and in the main company.
- | **Error:** `Usuario sin permiso de envio.`
  | **Hint:** This error indicates that most likely, your company has not passed the `Certification
    process <https://www.sii.cl/factura_electronica/factura_mercado/proceso_certificacion.htm>`_ in
    the :abbr:`SII (Servicio de Impuestos Internos)` - Sistema de Facturación de Mercado. If this is
    the case, please contact your Account Manager or Customer Support as this certification is not
    part of the Odoo services, but we can give you some alternatives. If you already passed the
    certification process, this error appears when a user different from the owner of the
    certificate is trying to send :abbr:`DTE (Documentos Tributarios Electrónicos)` files to the
    :abbr:`SII (Servicio de Impuestos Internos)`.
- | **Error:** `CARATULA`
  | **Hint:** There are just five reasons why this error could show up and all of them are related
    to the *Caratula* section of the XML:

    - The company's RUT number is incorrect or missing.
    - The certificate owner RUT number is incorrect or missing.
    - The SII's RUT number (this should be correct by default).
    - The resolution date.
    - The resolution number.

.. _chile/credit-notes:

Credit notes
------------

When a cancellation or correction is needed over a validated invoice, a credit note must be
generated. It is important to consider that a :abbr:`CAF (Folio Authorization Code)` file is
required for the credit note, which is identified as :guilabel:`Document Type` :guilabel:`61` in the
:abbr:`SII (Servicio de Impuestos Internos)`. Please refer to the :ref:`CAF section
<chile/caf-documentation>` for more information on the process to load the :abbr:`CAF (Folio
Authorization Code)` on each document type.

.. image:: chile/credit-note-document-type.png
   :alt: Creation of CAF for Credit notes.

Use cases
~~~~~~~~~

Cancel referenced document
**************************

In case you need to cancel or invalid an invoice, use the button :guilabel:`Add Credit note` and
select :guilabel:`Full Refund`, in this case the :abbr:`SII (Servicio de Impuestos Internos)`
reference code is automatically set to :guilabel:`Anula Documento de referencia`.

.. image:: chile/credit-note-cancel-ref-doc.png
   :alt: Credit note canceling the referenced document.

Correct referenced document
***************************

If a correction in the invoice information is required, for example the *street name*, use the
button :guilabel:`Add Credit Note`, select :guilabel:`Partial Refund` and select the option
:guilabel:`Only Text Correction`. In this case the :guilabel:`SII Reference Code` is automatically
set to :guilabel:`Corrects Referenced Document Text`.

.. image:: chile/credit-note-correct-text.png
   :alt: Credit note correcting referenced document text.

Odoo creates a credit note with the corrected text in an invoice and :guilabel:`Price` `0.00`.

.. image:: chile/text-correction-label.png
   :alt: Credit note with the corrected value on the invoice lines.

.. important::
   It's important to define the :guilabel:`Default Credit Account` in the sales journal as it is
   taken for this use case in specific.

Corrects referenced document amount
***********************************

When a correction on the amounts is required, use the button :guilabel:`Add Credit note` and select
:guilabel:`Partial Refund`. In this case the :guilabel:`SII Reference Code` is automatically set to
:guilabel:`Corrige el monto del Documento de Referencia`.

.. image:: chile/credit-note-correct-amount.png
   :alt: Credit note for partial refund to correct amounts, using the SII reference code 3.

Debit notes
-----------

As part of the Chilean localization, besides creating credit notes from an existing document you can
also create debit notes. For this just use the button :guilabel:`Add Debit Note`. The two main use
cases for debit notes are detailed below.

.. _chile/use-cases:

Use cases
~~~~~~~~~

Add debt on invoices
********************

The most common use case for debit notes is to increase the value of an existing invoice, you need
to select option :guilabel:`3. Corrige el monto del Documento de Referencia` for the
:guilabel:`Reference Code SII` field.

.. image:: chile/debit-note-correct-amount.png
   :alt: Debit note correcting referenced document amount.

In this case Odoo automatically includes the :guilabel:`Source Invoice` in the :guilabel:`Cross
Reference` tab.

.. image:: chile/auto-ref-debit-note.png
   :alt: Automatic reference to invoice in a debit note.

.. tip::
   You can only add debit notes to an invoice already accepted by the SII.

Cancel credit notes
*******************

In Chile, the debits notes are used to cancel a valid credit note. In this case, just select the
:guilabel:`Add Debit Note` button and then select the :guilabel:`1: Anula Documentos de referencia`
option for the :guilabel:`Reference Code SII` field.

.. image:: chile/debit-note-cancel-ref-doc.png
   :alt: Debit note to cancel the referenced document (credit note).

Vendor bills
------------

As part of the Chilean localization, you can configure your incoming email server as the same you
have registered in the :abbr:`SII (Servicio de Impuestos Internos)` in order to:

- Automatically receive the vendor bills :abbr:`DTE (Documentos Tributarios Electrónicos)` and
  create the vendor bill based on this information.
- Automatically send the reception acknowledgement to your vendor.
- Accept or claim the document and send this status to your vendor.

Reception
~~~~~~~~~

As soon as the vendor email with the attached :abbr:`DTE (Documentos Tributarios Electrónicos)` is
received:

#. The vendor bill maps all the information included in the XML.
#. An email is sent to the vendor with the reception acknowledgement.
#. The :guilabel:`DTE Status` is set as :guilabel:`Acuse de Recibido Enviado`.

Acceptation
~~~~~~~~~~~

If all the commercial information is correct on your vendor bill, then you can accept the document
using the :guilabel:`Aceptar Documento` button. Once this is done, the :guilabel:`DTE Acceptation
Status` changes to :guilabel:`Accepted` and an email of acceptance is sent to the vendor.

.. image:: chile/accept-vendor-bill-btn.png
   :alt: Button for accepting vendor bills.

Claim
~~~~~

In case there is a commercial issue or the information is not correct on your vendor bill, you can
claim the document before validating it, using the :guilabel:`Claim` button, once this is done, the
:guilabel:`DTE Acceptation Status` changes to :guilabel:`Claim` and an email of rejection is sent to
the vendor.

.. image:: chile/claim-vendor-bill-btn.png
   :alt: Claim button in vendor bills to inform the vendor all the document is commercially
         rejected.

If you claim a vendor bill, the status changes from :guilabel:`Draft` to :guilabel:`Cancel`
automatically. Considering this as best practice, all the claimed documents should be canceled as
they won't be valid for your accounting records.

Delivery guide
--------------

To install the :guilabel:`Delivery Guide` module, go to :menuselection:`Apps` and search for `Chile
(l10n_cl)`. Then click :guilabel:`Install` on the module :guilabel:`Chile - E-Invoicing Delivery
Guide`.

.. note::
   :guilabel:`Chile - E-Invoicing Delivery Guide` has a dependency with :guilabel:`Chile -
   Facturación Electrónica`. Odoo will install the dependency automatically when the
   :guilabel:`Delivery Guide` module is installed.

The *delivery guide* module includes sending the :abbr:`DTE (Documentos Tributarios Electrónicos)`
to :abbr:`SII (Servicio de Impuestos Internos)` and the stamp in PDF reports for deliveries.

Once all configurations have been made for :ref:`electronic invoices <chile/electronic-invoice>`
(e.g., uploading a valid company certificate, setting up master data, etc.), delivery guides need
their own :abbr:`CAFs (Folio Authorization Code)`. Please refer to the :ref:`CAF documentation
<chile/caf-documentation>` to check the details on how to acquire the :abbr:`CAF (Folio
Authorization Code)` for electronic Delivery Guides.

Verify the following important information in the :guilabel:`Price for the Delivery Guide`
configuration:

- :guilabel:`From Sales Order`: Delivery guide takes the product price from the sales order and
  shows it on the document.
- :guilabel:`From Product Template`: Odoo takes the price configured in the product template and
  shows it on the document.
- :guilabel:`No show price`: No price is shown in the delivery guide.

Electronic delivery guides are used to move stock from one place to another and they can represent
sales, sampling, consignment, internal transfers, and basically any product move.

Delivery guide from a sales process
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. warning::
   A delivery guide should **not** be longer than one page or contain more than 60 product lines.

When a sales order is created and confirmed, a delivery order is generated. After validating the
delivery order, the option to create a delivery guide is activated.

.. image:: chile/delivery-guide-creation-btn.png
   :alt: Create Delivery Guide button on a sales process.

When clicking on :guilabel:`Create Delivery Guide` for the first time, a warning message pops up,
stating the following:

.. warning::
   "No se encontró una secuencia para la guía de despacho. Por favor, establezca el primer número
   dentro del campo número para la guía de despacho"

   .. image:: chile/delivery-guide-number-warning.png
         :alt: First Delivery Guide number warning message.

This warning message means the user needs to indicate the next sequence number Odoo has to take to
generate the delivery guide (next available CAF number), and only happens the first time a delivery
guide is created in Odoo. After the first document has been correctly generated, Odoo takes the next
available number in the CAF file to generate the following delivery guide.

After the delivery guide is created:

- The :abbr:`DTE (Documentos Tributarios Electrónicos)` file (Electronic Tax Document) is
  automatically created and added to the :guilabel:`chatter`.
- The :guilabel:`DTE SII Status` is set as :guilabel:`Pending to be sent`.

.. image:: chile/chatter-delivery-guide.png
   :alt: Chatter notes of Delivery Guide creation.

The :guilabel:`DTE Status` is automatically updated by Odoo with a scheduled action that runs every
day at night. To get a response from the :abbr:`SII (Servicio de Impuestos Internos)` immediately,
press the :guilabel:`Send now to SII` button.

Once the delivery guide is sent, it may then be printed by clicking on the :guilabel:`Print Delivery
Guide` button.

.. image:: chile/print-delivery-guide-btn.png
   :alt: Printing Delivery Guide PDF.

Delivery guide will have fiscal elements that indicate that the document is fiscally valid when
printed (if hosted in Odoo SH or on Premise remember to manually add the :guilabel:`pdf417gen`
library mentioned in the :ref:`Invoice PDF report section <chile/electronic-invoice-pdf-report>`).

Electronic receipt
------------------

To install the :guilabel:`Electronic Receipt` module, go to :menuselection:`Apps` and search for
`Chile (l10n_cl)`. Then click :guilabel:`Install` on the module :guilabel:`Chile - Electronic
Receipt`.

.. note::
   :guilabel:`Chile - Electronic Receipt` has a dependency with :guilabel:`Chile - Facturación
   Electrónica`. Odoo will install the dependency automatically when the :guilabel:`E-invoicing
   Delivery Guide` module is installed.

Once all configurations have been made for :ref:`electronic invoices <chile/electronic-invoice>`
(e.g., uploading a valid company certificate, setting up master data, etc.), electronic receipts
need their own :abbr:`CAFs (Folio Authorization Code)`. Please refer to the :ref:`CAF documentation
<chile/caf-documentation>` to check the details on how to acquire the :abbr:`CAFs (Folio
Authorization Code)` for electronic receipts.

Electronic receipts are useful when clients do not need an electronic invoice. By default, there is
a partner in the database called :guilabel:`Anonymous Final Consumer` with a generic RUT
`66666666-6` and taxpayer type of :guilabel:`Final Consumer`. This partner can be used for
electronic receipts or a new record may be created for the same purpose.

.. image:: chile/electronic-receipt-customer.png
   :alt: Electronic Receipt module.

Although electronic receipts should be used for final consumers with a generic RUT, it can also be
used for specific partners. After the partners and journals are created and configured, the
electronic receipts are created in the standard way as electronic invoice, but the type of document
:guilabel:`(39) Electronic Receipt` should be selected in the invoice form:

.. image:: chile/document-type-39.png
   :alt: Document type 39 for Electronic Receipts.

Validation and DTE status
~~~~~~~~~~~~~~~~~~~~~~~~~

When all of the electronic receipt information is filled, either manually or automatically from a
sales order, proceed to validate the receipt. By default, :guilabel:`Electronic Invoice` is selected
as the :guilabel:`Document Type`, however in order to validate the receipt correctly, make sure to
edit the :guilabel:`Document Type` and change to :guilabel:`Electronic Receipt`.

After the receipt is posted:

- The :abbr:`DTE (Documentos Tributarios Electrónicos)` file (Electronic Tax Document) is created
  automatically and added to the :guilabel:`chatter`.
- The :guilabel:`DTE SII Status` is set as :guilabel:`Pending to be sent`.

.. image:: chile/electronic-receipt-ste-status.png
   :alt: Electronic Receipts STE creation status.

The :guilabel:`DTE Status` is automatically updated by Odoo with a scheduled action that runs every
day at night. To get a response from the :abbr:`SII (Servicio de Impuestos Internos)` immediately,
press the :guilabel:`Send now to SII` button.

Please refer to the :ref:`DTE Workflow <chile/electronic-invoice-validation>` for electronic
invoices as the workflow for electronic receipt follows the same process.

Electronic export of goods
--------------------------

To install the :guilabel:`Electronic Exports of Goods` module, go to :menuselection:`Apps` and
search for `Chile (l10n_cl)`. Then click :guilabel:`Install` on the module :guilabel:`Electronic
Exports of Goods for Chile`.

.. note::
   :guilabel:`Chile - Electronic Exports of Goods for Chile` has a dependency with :guilabel:`Chile
   - Facturación Electrónica`.

Once all configurations have been made for :ref:`electronic invoices <chile/electronic-invoice>`
(e.g., uploading a valid company certificate, setting up master data, etc.), electronic exports of
goods need their own :abbr:`CAFs (Folio Authorization Code)`. Please refer to the :ref:`CAF
documentation <chile/caf-documentation>` to check the details on how to acquire the :abbr:`CAFs
(Folio Authorization Code)` for electronic receipts.

Electronic invoices for the export of goods are tax documents that are used not only for the
:abbr:`SII (Servicio de Impuestos Internos)` but are also used with customs and contain the
information required by it.

Contact configurations
~~~~~~~~~~~~~~~~~~~~~~

.. image:: chile/taxpayer-type-export-goods.png
   :alt: Taxpayer Type needed for the Electronic Exports of Goods module.

Chilean customs
~~~~~~~~~~~~~~~

When creating an electronic exports of goods invoice, these new fields in the :guilabel:`Other Info`
tab are required to comply with Chilean regulations.

.. image:: chile/chilean-custom-fields.png
   :alt: Chilean customs fields.

PDF report
~~~~~~~~~~

Once the invoice is accepted and validated by the :abbr:`SII (Servicio de Impuestos Internos)` and
the PDF is printed, it includes the fiscal elements that indicate that the document is fiscally
valid and a new section needed for customs.

.. image:: chile/pdf-report-section.png
   :alt: PDF report section for the Electronic Exports of Goods PDF Report.

Financial reports
=================

Balance tributario de 8 columnas
--------------------------------

This report presents the accounts in detail (with their respective balances), classifying them
according to their origin and determining the level of profit or loss that the business had within
the evaluated period of time.

You can find this report in :menuselection:`Accounting --> Reporting --> Balance Sheet` and
selecting in the :guilabel:`Report` field the option :guilabel:`Chilean Fiscal Balance (8 Columns)
(CL)`.

.. image:: chile/locate-fiscal-balance-report.png
   :alt: Location of the Reporte Balance Tributario de 8 Columnas.

.. image:: chile/8-col-fiscal-balance-report.png
   :alt: Chilean Fiscal Balance (8 Columns).

Propuesta F29
-------------

The form *F29* is a new system that the :abbr:`SII (Servicio de Impuestos Internos)` enabled to
taxpayers, and that replaces the *Purchase and Sales Books*. This report is integrated by Purchase
Register (CR) and the Sales Register (RV). Its purpose is to support the transactions related to
VAT, improving its control and declaration.

This record is supplied by the electronic tax documents (DTE's) that have been received by the
:abbr:`SII (Servicio de Impuestos Internos)`.

You can find this report in :menuselection:`Accounting --> Reporting --> Tax Reports` and selecting
the :guilabel:`Report` option :guilabel:`Propuesta F29 (CL)`.

.. image:: chile/locate-propuesta-f29-report.png
   :alt: Location of the Propuesta F29 (CL) Report.

It is possible to set the :abbr:`PPM (Provisional Monthly Payments rate)` and the
:guilabel:`Proportional Factor for the fiscal year` from the :menuselection:`Accounting -->
Configuration --> Settings`.

.. image:: chile/f29-report.png
   :alt: Default PPM and Proportional Factor for the Propuesta F29 Report.

Or manually in the reports by clicking on the :guilabel:`✏️ (pencil)` icon.

.. image:: chile/manual-ppm-f29-report.png
   :alt: Manual PPM for the Propuesta F29 Report.

Demo mode
=========

For a quick demonstration of the different :abbr:`DTE (Documentos Tributarios Electrónicos)`
workflows, the Chilean localization can be tested in the demo mode provided in test databases or in
`runbot.odoo.com <https://runbot.odoo.com/>`_.

.. important::
   Do not use demo mode in a production environment.

To activate demo mode in runbot you must:

- Access https://runbot.odoo.com/
- Install the :ref:`Chilean Localization modules <chile/configuration>`.

After these steps, a new Chilean company *CL Company* is installed in the database with the company
configurations needed, demo contacts, demo mode selected and test :abbr:`CAFs (Folio Authorization
Code)` installed.

.. image:: chile/demo-mode-config.png
   :alt: Demo Mode configuration in runbot.

Some important considerations to take into account when using demo mode:

- The :abbr:`DTE (Documentos Tributarios Electrónicos)` files created in demo mode are not sent to
  the :abbr:`SII (Servicio de Impuestos Internos)`, for that reason, all of the files will be
  created and accepted automatically, as this will be a simulation.
- Rejection errors or accepted with objections will not appear in this mode, these situations should
  be validated in Test/Certification mode with the files actually being sent to the :abbr:`SII
  (Servicio de Impuestos Internos)`.
- Every internal validation can be tested in demo mode.

.. tip::
   Demo mode files are not sent to the :abbr:`SII (Servicio de Impuestos Internos)`. Test mode is
   the configuration needed to use testing :abbr:`CAFs (Folio Authorization Code)` obtained from the
   :abbr:`SII (Servicio de Impuestos Internos)`. In this mode, the direct connection flows with the
   :abbr:`SII (Servicio de Impuestos Internos)` can be tested.
