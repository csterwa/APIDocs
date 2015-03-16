{{{
  "title": "Convert Server To Template",
  "date": "2-7-2013",
  "author": "Troy Schneringer",
  "attachments": []
}}}

Converts the server to a template.

## URL

    REST: https://api.ctl.io/REST/Server/ConvertServerToTemplate/<format>
    SOAP: https://api.ctl.io/SOAP/Server.asmx?op=ConvertServerToTemplate 

## Request

### Attributes

<table>
    <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>Description</th>
      <th>Req.</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>AccountAlias</td>
      <td>String</td>
      <td>The alias of the account that owns the server. If not provided it will assume the account to which the API user is mapped. Providing this value gives you the ability to access servers in your sub accounts.</td>
      <td>No</td>
    </tr>
    <tr>
      <td>Name</td>
      <td>String</td>
      <td>The name of the server. &nbsp;</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td>Password</td>
      <td>String</td>
      <td>The administrator/root password for the server to convert.</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td>TemplateAlias</td>
      <td>String</td>
      <td>The alias for the Template to create.</td>
      <td>Yes</td>
    </tr>
  </tbody>
</table>

### Examples

#### JSON

    {

      "Name": "WA1T3NWEB01",

      "AccountAlias": "UNK",

      "Password": "password",

      "TemplateAlias": "TEMP"

    }

#### XML

    <ConvertServerToTemplateRequest>

        <AccountAlias>ACCT</AccountAlias>

        <Name>WEB</Name>

        <Password>password</Password>

        <TemplateAlias>TEMP</TemplateAlias>

    </ConvertServerToTemplateRequest>

## Response

### Attributes

<table>
  <thead>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
</thead>
<tbody>
    <tr>
      <td>Success</td>
      <td>Boolean</td>
      <td>True if the request was successful, otherwise False.</td>
    </tr>
    <tr>
      <td>Message</td>
      <td>String</td>
      <td>A description of the result. The contents of this field does not contain any actionable information, it is purely intended to provide a human readable description of the result.</td>
    </tr>
    <tr>
      <td>StatusCode</td>
      <td>Int</td>
      <td>This value will help to identify any errors which were encountered while processing the request. The value of '0' indicates success, all non-zero StatusCodes indicate an error state.</td>
    </tr>
    <tr>
      <td>RequestID</td>
      <td>Int</td>
      <td>
        <p>The ID of the Queued request.</p>
        <p>Status of the request can be obtained by calling the&nbsp;<a href="../Blueprint/get-deployment-status.md">Get Deployment Status</a>&nbsp;method.</p>
      </td>
    </tr>
  </tbody>
</table>

### Examples

#### JSON

    {

      "RequestID":1,

      "Success":true,

      "Message":"Success",

      "StatusCode":0

    }

#### XML

    <QueuedItemResponse Success="true" Message="Success" StatusCode="0">

        <RequestID>1</RequestID>

    </QueuedItemResponse>

### Status Codes
<table>
    <thead>
  <tr>
    <th>Status Code</th>
    <th>Description</th>
  </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>Request was successfully processed</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Unknown Error - An application error occurred processing your request, contact Tier3 support to resolve the issue.</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Invalid Request Format. This value indicates that the XML or JSON requests do not match the expected format.</td>
    </tr>
    <tr>
      <td>5</td>
      <td>
        <p>Resource Not Found. &nbsp;</p>
        <p>A Server with the specified Name cannot be found&nbsp;</p>
      </td>
    </tr>
    <tr>
      <td>6</td>
      <td>
        <p>Invalid Operation. &nbsp;Server must be in an active state.</p>
      </td>
    </tr>
    <tr>
      <td>100</td>
      <td>Authentication Failed - You must logon to the API prior to calling this method.</td>
    </tr>
    <tr>
      <td>1410</td>
      <td>Name Required.</td>
    </tr>
    <tr>
      <td>1411</td>
      <td>Password Required.</td>
    </tr>
  </tbody>
</table>