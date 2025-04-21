# MailSend()

In the Volt MX framework, the Volt Foundry Email Adapter Integration Service enables email sending. The Email Adapter uses the Volt Foundry Engagement Server to send the email.

The `MailSend()` API for Volt MX requires the name of the Volt Foundry Email Adapter Integration Service to make the send email request. `API.setEmailService` can be used to set the Email Adapter service name that Rosetta can use. If the Email Adapter service name isn't set, the default `RosettaEmailService` name will be used.

To use `MailSend()`, the database needs to be open, and a document needs to be selected. It's up to the user to configure the Volt Foundry Email Adapter Integration Service and the Volt Foundry Engagement server. For more information on configuring an Integration Service and an Engagement server, see the [Volt MX documentation](https://help.hcl-software.com/voltmx/v9.5/index.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}.
