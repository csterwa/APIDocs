{{{
  "title": "ServerMaintenance",
  "date": "9-26-2014",
  "author": "Peter Kowalczyk",
  "attachments": []
}}}

Enables or disables maintenance mode on a Server.

## URL

    REST: https://api.ctl.io/REST/Server/ServerMaintenance/<format>
    SOAP: https://api.ctl.io/SOAP/Server.asmx?op=ServerMaintenance

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
      <td>The name of the Server.</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td>Enable</td>
      <td>Boolean</td>
      <td>Turn maintenance mode on or off.</td>
      <td>&nbsp;Yes</td>
    </tr>
  </tbody>
</table>

### Examples

#### JSON

    {

      "Name": "DEMOFIRST01",

      "AccountAlias": "UNK",

      "Enable": true

    }

#### XML

    <ServerMaintenanceRequest>

        <AccountAlias>ACCT</AccountAlias>

        <Name>DEMOFIRST01</Name>

        <Enable>true</Enable>

    </ServerMaintenanceRequest>

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
        "RequestID:1,
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
      <td>Unknown Error. &nbsp;An application error occurred processing your request, contact Tier3 support to resolve the issue.</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Invalid Request Format. This value indicates that the XML or JSON requests do not match the expected format.</td>
    </tr>
    <tr>
      <td>5</td>
      <td>Resource Not Found. &nbsp;A Server with the specified Name cannot be found.</td>
    </tr>
    <tr>
      <td>6</td>
      <td>Invalid Operation. &nbsp;Server must be in an active state.</td>
    </tr>
    <tr>
      <td>100</td>
      <td>Authentication Failed. &nbsp;You must logon to the API prior to calling this method.</td>
    </tr>
    <tr>
      <td>1410</td>
      <td>Name required. &nbsp;The name parameter must be specified.</td>
    </tr>
  </tbody>
</table>