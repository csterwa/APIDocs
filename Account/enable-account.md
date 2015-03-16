{{{
  "title": "Enable Account",
  "date": "2-14-2013",
  "author": "Luke Bakken",
  "attachments": []
}}}


Enable a suspended account in the  system. Calls to this operation must include an authorization cookie acquired from the <a href="/api-docs#authentication-logon">Logon operation.</a>

## URL

    REST: https://api.ctl.io/REST/Account/EnableAccount/<format> (format = XML | JSON)
    SOAP: https://api.ctl.io/SOAP/Account.asmx?op=EnableAccount

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
      <td>Account alias.</td>
      <td>Yes</td>
    </tr>
  </tbody>
</table>

### Examples

#### JSON (REST)

    {

      "AccountAlias": "ACCT"

    }

#### XML (REST)

    <AccountStatusRequest>

        <AccountAlias>ACCT</AccountAlias>

    </AccountStatusRequest>

#### XML (SOAP)

    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 

            xmlns:xsd="http://www.w3.org/2001/XMLSchema" 

            xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">

      <soap:Body>

        <EnableAccount xmlns="http://www.tier3.com/">

          <request>

             <AccountAlias>ACCT</AccountAlias>

          </request>

        </EnableAccount>

      </soap:Body>

    </soap:Envelope>  

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
      <td>The ID of the Queued request.Status of the request can be obtained by calling the&nbsp;<a href="/entries/20561586-get-deployment-status">GetDeploymentStatus</a>&nbsp;method.</td>
    </tr>
  </tbody>
</table>

### Examples

#### JSON (REST)

    {

      "Success": true,

      "Message": "Account Enabled.",

      "StatusCode": 0,

      "RequestID": 100

    }

#### XML (REST)

    <QueuedItemResponse Success="true" Message="Success" StatusCode="0">

        <RequestID>1</RequestID>

    </QueuedItemResponse>

#### XML (SOAP)

    <soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">

    <soap:Body>

        <EnableAccountResponse xmlns="http://www.tier3.com/">

        <QueuedItemResponse Success="true" Message="Account Enabled." StatusCode="0">

            <ResponseID>100</ResponseID>

        </QueuedItemResponse>

    </EnableAccountResponse>

    </soap:Body>

    </soap:Envelope>

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
      <td>5</td>
      <td>Resource Not Found. &nbsp;Provided account alias does not exist.</td>
    </tr>
    <tr>
      <td>100</td>
      <td>Authentication Failed. &nbsp;You must logon to the API prior to calling this method.</td>
    </tr>
    <tr>
      <td>1600</td>
      <td>Account Alias Required. &nbsp;You must provide an account alias when calling this method.</td>
    </tr>
  </tbody>
</table>