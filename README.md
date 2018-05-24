<p>&nbsp;</p>
<table width="100%">
<tbody>
<tr>
<td>
<p><strong>Symantec Migration</strong></p>
<p><strong>Workflow Guide</strong></p>
</td>
</tr>
</tbody>
</table>
<p><strong>&nbsp;</strong></p>
<p>Copyright &copy; 2018 AppViewX, Inc. All Rights Reserved.</p>
<p>This document may not be copied, disclosed, transferred, or modified without the prior written consent of AppViewX, Inc. While all content is believed to be correct at the time of publication, it is provided as general purpose information. The content is subject to change without notice and is provided &ldquo;as is&rdquo; and with no expressed or implied warranties whatsoever, including, but not limited to, a warranty for accuracy made by AppViewX. The software described in this document is provided under written license only, contains valuable trade secrets and proprietary information, and is protected by the copyright laws of the United States and other countries. Unauthorized use of software or its documentation can result in civil damages and criminal prosecution.</p>
<p>Trademarks</p>
<p>The trademarks, logos, and service marks displayed in this manual are the property of AppViewX or other third parties. Users are not permitted to use these marks without the prior written consent of AppViewX or such third party which may own the mark.</p>
<p>This product includes software developed by the CentOS Project (<a href="https://www.centos.org/">www.centos.org</a>).</p>
<p>This product includes software developed by Red Hat, Inc. (<a href="https://www.redhat.com/en">www.redhat.com</a>).</p>
<p>This product includes software developed by VMware, Inc. (<a href="https://www.vmware.com/in.html">www.vmware.com</a>).</p>
<p>All other trademarks mentioned in this document are the property of their respective owners.</p>
<p>Contact Information</p>
<p>AppViewX, Inc.</p>
<p>500 Yale Avenue North, Suite 100</p>
<p>Seattle, WA 98109</p>
<p>Tel: +1 (206) 207 7541</p>
<p>Email: info@appviewx.com</p>
<p>Web: <a href="http://www.appviewx.com/">www.appviewx.com</a></p>
<p>Document Information</p>
<p>Software Version: 12.3.0</p>
<p>Document Version: 1.1</p>
<p>Last updated on: April 06, 2018</p>
<p><strong>Contents</strong></p>
<p><a href="#_Toc510703013">Description. 1</a></p>
<p><a href="#_Toc510703014">Prerequisites. 1</a></p>
<p><a href="#_Toc510703015">Compatible Software Versions. 1</a></p>
<p><a href="#_Toc510703016">Log In to AppViewX. 2</a></p>
<p><a href="#_Toc510703017">Import Visual Workflows. 2</a></p>
<p><a href="#_Toc510703018">Import Helper Scripts. 3</a></p>
<p><a href="#_Toc510703019">Discover a Certificate. 4</a></p>
<p><a href="#_Toc510703020">Configure Certificate Manager Accounts. 5</a></p>
<p><a href="#_Toc510703021">Configure the SMTP.. 5</a></p>
<p><a href="#_Toc510703022">Enable a Workflow.. 6</a></p>
<p><a href="#_Toc510703023">Symantec Migration Workflow.. 6</a></p>
<p><a href="#_Toc510703024">WorkOrder flow.. 8</a></p>
<p><a href="#_Toc510703025">Rollback a workflow.. 9</a></p>
<p><a href="#_Toc510703026">WorkOrder flow.. 10</a></p>
<p><a href="#_Toc510703027">Request Inventory. 10</a></p>
<p><a href="#_Toc510703028">Schedule a Workflows. 11</a></p>
<p><a href="#_Toc510703029">View Scheduled Workflows. 12</a></p>
<p><a href="#_Toc510703030">Troubleshooting. 12</a></p>
<h1>Description</h1>
<p>The Symantec Migration workflow will migrate the Symantec certificate to the other CAs such as DigiCert, Entrust, Trustwave, and Comodo certificate manager, which are currently managed in the AppViewX instance. You can migrate up to 10 Symantec certificates using a single request.</p>
<p>The flow diagram of Symantec Migration workflow is shown in the image below:</p>
<h1>Prerequisites</h1>
<p>To run this workflow, ensure that the following pre-requisites are met:</p>
<ul>
<li>Free AppViewX or AppViewX version 12.3.0 has been downloaded and installed.</li>
<li>The Symantec certificate must be discovered and managed in the AppViewX.</li>
<li>The DigiCert, Entrust, Trustwave, and Comodo certificate manager accounts are configured on AppViewX.</li>
<li>Each CA must have the appropriate credentials.</li>
<li>The SMTP is configured in AppViewX for sending emails.</li>
<li>&ldquo;Approval required&rdquo; parameter in the policy of the selected Certificate group must be unchecked for the auto-implementation of this workflow.</li>
</ul>
<h1>Compatible Software Versions</h1>
<p>The automation temple has been tested and validated on the following software versions:</p>
<ul>
<li>AppViewX &ndash; Free AppViewX and AVX 12.3.0</li>
<li>CAs - DigiCert, Entrust, Trustwave, and Comodo certificate managers</li>
</ul>
<p><strong>Limitations</strong></p>
<ul>
<li>App connector will not handle duplicate certificate for the same CA and CA cert type.</li>
<li>The inputs to generate the CSR may differ for Symantec and the migrated CA.</li>
<li>In a single request, up to 10 Symantec certificates can be migrated.</li>
</ul>
<h1>Log In to AppViewX</h1>
<p>Log in to the AppViewX web interface. The standard format for a login URL is:</p>
<p>https://hostname:portnumber.</p>
<p>The hostname and port number are configured during deployment, with the default port number set to <sub>5004</sub> and the default web credentials set to <sub>admin</sub>/<sub>AppViewX@123</sub>.</p>
<p><strong>Note:</strong> It is recommended that you access AppViewX using Internet Explorer, Firefox, or Google Chrome.</p>
<h1>Import Visual Workflows</h1>
<p><strong>Note:</strong> Free AppViewX comes preloaded with visual workflows. You will only need to use the following import instructions when newer versions of the workflows are available.</p>
<ol>
<li>Click the (<strong>Menu</strong>) button.</li>
<li>Navigate to <strong>Workflow &gt; Studio</strong>.</li>
<li>Click the (<strong>Import</strong>) button in the Command bar.</li>
</ol>
<ol>
<li>To import a workflow, complete the following steps:</li>
<ol>
<li>Click the <strong>Browse </strong>button.</li>
<li>Select the zip file containing one or more workflows, then click <strong>Upload</strong>.</li>
<li>In the table at the bottom of the <em>Import</em> page, select the check box beside the unzipped workflow file.</li>
<li>Click <strong>Submit</strong> to deploy the workflow into your AppViewX environment.</li>
</ol>
</ol>
<p>The Symantec Migration workflow is shown in the image below:</p>
<h1>Import Helper Scripts</h1>
<p><strong>Note:</strong> Free AppViewX comes preloaded with helper scripts. You will only need to use the following import instructions when newer versions of the helper scripts are available.</p>
<ol>
<li>Click the (<strong>Menu</strong>) button.</li>
<li>Navigate to <strong>Workflow &gt; Studio</strong>.</li>
</ol>
<ol start="3">
<li>Click on the (<strong>Helper script</strong>) button in the Command bar.</li>
</ol>
<p>The <em>Helper script library</em> screen appears.</p>
<ol>
<li>Click the (<strong>Import</strong>) button.</li>
<li>Click <strong>Browse</strong> and select the helper script zip file you want to import.</li>
<li>Click <strong>Upload</strong> to import the file and view its contents.</li>
</ol>
<p><strong>Note: </strong>Select the checkbox <strong>Overwrite existing file</strong>, only if the names of the new script file that you are trying to upload and the existing script file are the same.</p>
<ol start="7">
<li>In the table at the bottom of the <em>Import</em> page, select the check boxes beside each of the helper scripts.</li>
<li>Click <strong>Submit</strong> to deploy them into your AppViewX environment.</li>
</ol>
<h1>Discover a Certificate</h1>
<p>The Discover function allows you to search for and display the list of all available certificates within the network of an organization in order to manage it in the AppViewX certificate inventory.</p>
<p>To discover a certificate by IP range, complete the following steps:</p>
<ol>
<li>Click the (<strong>Menu</strong>) button.</li>
</ol>
<ol>
<li>Navigate to <strong>Inventory</strong> &gt; <strong>Certificate</strong>.</li>
</ol>
<p>The <strong><em>Certificate</em></strong> screen opens.</p>
<ol>
<li>If the <strong>Server</strong> tab is not displayed by default, click to open it.</li>
</ol>
<ol>
<li>Click the (<strong>Discover</strong>) button in the Command bar.</li>
</ol>
<p>The related screen opens with the <strong>Discovery</strong> tab selected by default.</p>
<p><strong>Note:</strong> To schedule a certificate discovery, click the <strong>Scheduler</strong> tab and do the following.</p>
<ol>
<li>Click the (<strong>Create</strong>) button in the Command bar.</li>
<li>Select the <strong>On-demand</strong> or <strong>Schedule</strong> radio button based on how you want to discover the certificates.</li>
<li>In the <strong>Name</strong> field, enter a name that clearly identifies the certificate discovery action that you are setting up.</li>
<li>(Optional) In the <strong>Description</strong> field, enter a description for the key discovery that makes it easy for a user to immediately determine when the key discovery is scheduled to take place.</li>
<li>(<em>Only necessary if you selected Schedule in Step 6</em>) From the <strong>Occurrence</strong> type dropdown list, select one of the following frequency for the certificate discovery process: <strong>daily</strong>, <strong>weekly</strong>, <strong>monthly</strong>, or <strong>yearly</strong>.</li>
</ol>
<p>The remaining fields in the Scheduler region populate depending on what you select here. At a minimum, complete all fields designated with a red asterisk ( ) beside their names.</p>
<p><strong>Note:</strong> The time and date fields displayed next will depend on the selected option. For recurring discoveries, select the start and end dates that you want key discovery to begin and end respectively.</p>
<ol>
<li>In the <strong>Discover By</strong> field, select the method by which you want to discover the certificates:</li>
</ol>
<ul>
<li>IP range</li>
<li>Subnet</li>
<li>URL</li>
<li>Upload</li>
<li>Managed ADCs</li>
<li>Managed Servers</li>
<li>Certificate Authorities</li>
</ul>
<p>The fields that appear will vary based on the discovery source you selected.</p>
<ol>
<li>At a minimum, complete all fields designated with a red asterisk ( ) and click Add.</li>
<li>To add all the details automatically, click the <strong>Upload</strong> button and navigate to the location of the file, then select it.</li>
<li>Click <strong>Open</strong>.</li>
</ol>
<p>This retrieves and displays all the details in the table at the bottom.</p>
<ol start="14">
<li>From the <strong>Certificate group</strong> dropdown list, select the group to which the discovered certificates must be associated.</li>
</ol>
<ol>
<li>Depending on how you want the status of the certificates to be displayed when they appear in the inventory, select one of the following radio buttons:</li>
</ol>
<ul>
<li>Do not move</li>
<li>Managed</li>
<li>Monitored</li>
</ul>
<ol>
<li>Click <strong>Discover</strong> to discover all certificates that match the criteria you entered.</li>
</ol>
<h1>Configure Certificate Manager Accounts</h1>
<p>To configure DigiCert, Entrust, Trustwave, and Comodo certificate manager accounts, complete the following steps:</p>
<ol>
<li>Click the (<strong>Menu</strong>) button.</li>
</ol>
<ol>
<li>Navigate to <strong>Inventory &gt; Certificate</strong>.</li>
</ol>
<p>The <strong><em>Certificate</em></strong> screen opens.</p>
<ol>
<li>If the <strong>Server</strong> tab is not displayed, click to open it.</li>
</ol>
<ol>
<li>Click the (<strong>Settings</strong>) button in the Command bar.</li>
<li>The <strong><em>Settings</em></strong> screen opens, listing each certificate authority (CA) available in AppViewX in the left-hand column.</li>
<li>Click the vendor name for which you want to add a certificate manager account.</li>
</ol>
<p><strong>Note:</strong> Click each vendor name to view the list of certificate manager accounts it contains. You can edit those accounts if required.</p>
<ol>
<li>On the <em>Certificate authority</em> screen that appears, click the <strong>Configure now</strong> button or (<strong>Add</strong>) button.</li>
<li>At a minimum, complete all fields designated with a red asterisk ( ).</li>
<li>Click <strong>Save</strong>.</li>
<li>(Optional) Repeat steps 6-9 for any other vendors for whom you want to create certificate manager account details.</li>
</ol>
<h1>Configure the SMTP</h1>
<p>To configure an SMTP server, complete the following steps:</p>
<ol>
<li>Click the (<strong>Menu</strong>) button.</li>
</ol>
<ol>
<li>Navigate to <strong>Settings</strong> &gt; <strong>General</strong> &gt; <strong>SMTP</strong>.</li>
</ol>
<ol>
<li>In the <strong>SMTP host</strong> field, enter the host address of the SMTP server.</li>
</ol>
<ol>
<li>In the <strong>SMTP port</strong> field, enter the port number for the SMTP server.</li>
</ol>
<ol>
<li>In the <strong>From address</strong> field, enter the email address from which the notification must be sent.</li>
</ol>
<ol>
<li>If an SMTP server requires authentication to connect, click the (<strong>Disabled</strong>) button to enable it.</li>
</ol>
<ol>
<li>If you enabled authentication in Step 7, enter the user name and password that is used for authentication on the SMTP server.</li>
</ol>
<ol>
<li>In the <strong>Send email to</strong> field, enter an email address you want to use to test the configuration, then click <strong>Test</strong>. If the configuration is successful, a test email will be sent to this address verifying that everything is working correctly.</li>
<li>Click <strong>Save</strong> to save the changes you have made to the system settings.</li>
</ol>
<h1>Enable a Workflow</h1>
<p>To enable the Symantec Migration workflow, complete the following steps:</p>
<ol>
<li>Click the (<strong>Menu</strong>) button.</li>
<li>Navigate to <strong>Workflow</strong> &gt; <strong>Studio</strong>.</li>
</ol>
<p>The <em>Workflow </em>screen opens.</p>
<ol>
<li>Click the (<strong>Select</strong>) button on the Symantec Migration workflow to enable. If the workflow is already selected, a (<strong>Deselect</strong>) button appears.</li>
<li>Click the (Enable) button in the Command bar.</li>
</ol>
<p><strong>Note:</strong> You can also enable the Symantec Migration workflow from the Card view by clicking the (<strong>Disable</strong>) button.</p>
<ol>
<li>On the <em>Confirmation</em> screen that appears, click <strong>Yes</strong>.</li>
</ol>
<h1>Symantec Migration Workflow</h1>
<p>To submit the Symantec Migration workflow, complete the following steps:</p>
<ol>
<li>Click the (<strong>Menu</strong>) button.</li>
<li>Navigate to <strong>Workflow</strong> &gt; <strong>Request</strong>.</li>
</ol>
<p>The <em>Request</em> screen opens with <strong>My catalog</strong> tab displayed by default. This screen displays all enabled workflows assigned to a specific user role.</p>
<ol>
<li>Click the Play button on the Symantec Migration workflow to execute.</li>
</ol>
<ol>
<li>The <em>Form Builder</em> screen opens with the <strong>Request View</strong> tab displayed by default.</li>
</ol>
<ol>
<li>In the <strong>Symantec Certificates</strong> field, retrieve the list of Symantec certificates managed in AppViewX by clicking the (<strong>Retrieve field values</strong>) button and select the certificates that must be migrated.</li>
</ol>
<p><strong>Note:</strong> It is recommended that you select only up to 10 certificates. Though this workflow has been limited to migrate only 10 certificates, Workflow is capable of migrating more certificates in one request.</p>
<ol>
<li>In the <strong>Certificate Group</strong> field, retrieve the list of certificate groups available by clicking the (<strong>Retrieve field values</strong>) button and select the certificate group to which the migrated certificates must be assigned to.</li>
<li>In the <strong>CA to Migrate</strong> dropdown field, select the CA to which the selected Symantec certificates must be migrated.</li>
<li>In the <strong>CA Account </strong>field, retrieve the list of CA accounts available by clicking the (<strong>Retrieve field values</strong>) button and select the CA account with appropriate credentials, which will be used to create new certificates.</li>
<li>In the <strong>Certificate Type </strong>field, retrieve the list of certificate types based on the selected CA by clicking the (<strong>Retrieve field values</strong>) button and select the required certificate type.</li>
<li>In the <strong>Server Type </strong>field, retrieve the list of server types based on the selected CA by clicking the (<strong>Retrieve field values</strong>) button and select the required server type.</li>
<li>Click the <strong>Fetch Selected Symantec Details</strong> button to retrieve the certificate information selected in step 4 and load it in the table in <strong>Certificate</strong> field.</li>
</ol>
<p><strong>Note:</strong> In the <strong>Certificate</strong> field, you can delete or modify the certificate details by selecting the check box beside the certificate UUID in the table and then clicking either the (<strong>Update</strong>) or (<strong>Delete</strong>) button.</p>
<ol>
<li>In the <strong>AppViewX Username</strong> and <strong>Password</strong> fields, enter the user name and password respectively for AppViewX Web login.</li>
<li>Click the <strong>PreValidation Check</strong> button to ensure the following:</li>
<ol>
<li>Only 1 to 10 Symantec certificates are selected for migration.</li>
<li>Validity of the selected CA and certificate type are within the allowed range.</li>
<li>The required information is provided for each certificate that is being migrated.</li>
</ol>
</ol>
<p>The result of this validation is displayed in the <strong>PreValidation Check</strong> field.</p>
<ol>
<li>Click <strong>Submit </strong>to trigger the workflow immediately.</li>
</ol>
<h2>WorkOrder flow</h2>
<p>The following are the workorder tasks of Symantec Migration workflow.</p>
<p><strong>Note:</strong> You can click each task to view its details. Wherever applicable, all logs related to the selected task are displayed in the <strong>Logs</strong> pane at the bottom of the screen.</p>
<ol>
<li><strong>Fetch Symantec Certificates</strong> ─ The Symantec certificate details are retrieved after they are enrolled successfully.</li>
<li><strong>Get Session Details</strong> ─ The session details and ID will be generated to issue the required API commands.</li>
<li><strong>Get Session ID</strong> ─ The session ID is retrieved for issuing API commands for creating CA connector, submitting CSR to CA, and checking the work order status.</li>
<li><strong>Create CA Connector</strong> ─ The CA connectors for the new certificates with common names are created.</li>
<li><strong>Submit CSR to CA </strong>─ The CSR is created and submitted to the CA</li>
<li><strong>Get Request ID </strong>─ The request ID of the triggered workflow is retrieved.</li>
<li><strong>Fetch Certificates </strong>─ After successful completion of workflow execution the certificates are retrieved from the corresponding CA.</li>
<li><strong>Email Migration Report </strong>─ An email is sent to the administrator with the status, common name, and request ID of the migration.</li>
</ol>
<h1>Rollback a workflow</h1>
<p>A rollback action can be performed only on the completed workflows. To trigger a rollback action, complete the following steps:</p>
<ol>
<li>Click the (<strong>Menu</strong>) button.</li>
<li>Navigate to <strong>Workflow</strong> &gt; <strong>Request</strong>.</li>
</ol>
<p>The <em>Request</em> screen opens with <strong>My catalog</strong> tab displayed by default.</p>
<ol>
<li>Click the <strong>Request Inventory</strong> tab.</li>
</ol>
<p>This displays all workflows that have been triggered. On the <strong>Request Inventory </strong>screen, you can search for a request created for Symantec Migration workflow using the <strong>Search </strong>field and/or click the (<strong>Filter</strong>) button.</p>
<ol start="4">
<li>Right-click the request and select <strong>Rollback</strong>.</li>
<li>On the Confirmation screen that appears, click <strong>Yes</strong>.</li>
<li>Select the <strong>Request</strong> or <strong>Workorder</strong> radio button based on how you want to set the rollback type.</li>
<li>Click <strong>Rollback</strong> to trigger the action.</li>
</ol>
<h2>WorkOrder flow</h2>
<p>The following are the workorder tasks of Symantec Migration workflow, when you perform a rollback action:</p>
<p><strong>Note:</strong> You can click each task to view its details. Wherever applicable, all logs related to the selected task are displayed in the <strong>Logs</strong> pane at the bottom of the screen.</p>
<ol>
<li><strong>Get Session ID</strong> ─ The session ID is retrieved for issuing API commands for revoking the certificates.</li>
<li><strong>Submit Revoke Request</strong> ─ The request to revoke the enrolled certificate is created and submitted to the corresponding CA<strong>.</strong></li>
<li><strong>Get Revoke Request ID</strong> ─ The request ID of the triggered workflow is retrieved</li>
<li><strong>Check Certificates Revoked</strong> ─ The enrolled certificate will be revoked and a validation is done to check the workflow status.</li>
</ol>
<h1>Request Inventory</h1>
<p>To go to the Request inventory, complete the following steps:</p>
<ol>
<li>Click the (<strong>Menu</strong>) button.</li>
<li>Navigate to <strong>Workflow</strong> &gt; <strong>Request</strong>.</li>
</ol>
<p>The <em>Request</em> screen opens with <strong>My catalog</strong> tab displayed by default.</p>
<ol>
<li>Click the <strong>Request Inventory</strong> tab.</li>
</ol>
<p>This displays all workflows that have been triggered. On the <strong>Request Inventory </strong>screen, you can search for a request using the <strong>Search </strong>field and/or click the (<strong>Filter</strong>) button to select the options you want to use to sort the requests.</p>
<ol>
<li>Click the <strong>Request ID </strong>created for Symantec Migration to view its details. The screen opens with the <strong>Request View</strong> tab selected by default.</li>
</ol>
<ol>
<li>After the workflow execution is complete, the <strong>Request View</strong> tab displays the tasks or phases of a request in a tree view. For more details, refer to the <u>Work Order Flow</u> section of this guide.</li>
<li>Click the <strong>Workorder View </strong>tab to view the work order details such as work order ID, date and time when the work order was created and updated, status, RFC ID, and RFC status.</li>
</ol>
<ol>
<li>In the <em>Request Inventory</em> screen, you can also view the following details of the request: request creator, request time, last updated time, status, and activity log.</li>
<li>Click the <strong>View </strong>link in the <strong>Activity log </strong>column to display the request in a stage view. In the <strong>Summary </strong>tab, click the (<strong>Expand</strong>) icon to view the details of each task. Click the <strong>Details </strong>tab to view log messages and other particulars of a request.</li>
</ol>
<h1>Schedule a Workflows</h1>
<p>To schedule a workflow, complete the following steps:</p>
<ol>
<li>Click the (<strong>Menu</strong>) button.</li>
<li>Navigate to <strong>Workflow</strong> &gt; <strong>Request</strong>.</li>
</ol>
<p>The <em>Request</em> screen opens with <strong>My catalog</strong> tab displayed by default.</p>
<ol>
<li>Click the (<strong>Schedule workflow</strong>) button on the Symantec Migration workflow.</li>
<li>On the Symantec Migration window that opens, select the frequency of the policy migration process: once, hourly, daily, weekly, monthly, or yearly. The remaining fields in the Scheduler region update depending on what you select.</li>
<li>Click <strong>Save</strong>.</li>
</ol>
<p>View Scheduled Workflows</p>
<p>To go to the scheduled workflow screen, complete the following steps:</p>
<ol>
<li>Click the (<strong>Menu</strong>) button.</li>
<li>Navigate to <strong>Workflow</strong> &gt; <strong>Request</strong>.</li>
<li>The <em>Request</em> screen opens with <strong>My catalog</strong> tab displayed by default.</li>
<li>Click the <strong>Scheduled workflows</strong> tab.</li>
<li>On the Scheduled workflow screen that appears, you can perform the following tasks:</li>
</ol>
<ol>
<ul>
<li>In the <strong>View log</strong> column, click <strong>View</strong> to display the details of a scheduled workflow.</li>
<li>Click the (Pause) or (Resume) button to temporarily stop or continue the execution of a workflow.</li>
</ul>
</ol>
<h1>Troubleshooting</h1>
<p><strong>I cannot find the Symantec Migration workflow in the Request Catalog</strong></p>
<p>You must enable the workflow from the Studio section. For more details on how to enable a workflow, refer to the <u>Enable a Workflow</u> section of this guide.</p>
<p><strong>The Symantec certificates are not fetched</strong></p>
<p>You must ensure the Symantec certificates are discovered and added in the AppViewX inventory as managed certificates. Also, check if your user account has the required access permissions defined in RBAC to manage the Symantec certificates.</p>
<p><strong>The CA accounts are not fetched </strong></p>
<p>You must create the CA accounts to fetch them. For more details on how to configure the CA accounts, refer to <u>Configure Certificate Manager Accounts</u> section of this guide.</p>
<p><strong>The pre-validation check fails </strong></p>
<p>Select the certificate to check all the required inputs to generate the new CSR are passed. Additional inputs are required to generate CSR for few CA's. You must select less than 10 certificates for migration in single request.</p>
<p><strong>The certificate migration to the new CA fails </strong></p>
<p>Check if the selected CA account has enough credits to create new certificates for migration. Ensure the AppViewX instance can communicate with external CA's.</p>
