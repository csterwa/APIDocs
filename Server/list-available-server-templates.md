{{{
  "title": "ListAvailableServerTemplates",
  "date": "5-1-2013",
  "author": "Luke Bakken",
  "attachments": []
}}}

Gets the list of Templates available to the account and location.

## URL

    REST: https://api.ctl.io/REST/Server/ListAvailableServerTemplates/<format>
    SOAP: https://api.ctl.io/SOAP/Server.asmx?op=ListAvailableServerTemplates

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
      <td>Location</td>
      <td>String</td>
      <td>The data center of the server templates.</td>
      <td>
        <p>No</p>
      </td>
    </tr>
  </tbody>
</table>

### Examples

#### XML

    <ListTemplatesRequest>

        <AccountAlias>ACCT</AccountAlias>

        <Location>WA1</Location>

    </ListTemplatesRequest>

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
      <td>Templates</td>
      <td>Complex</td>
      <td>
        <p>A list of [Server Template Objects](server-template-object.md)
        </p>
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
        "StatusCode":0,
        "Templates":[
            {
                "ID":1001,"Name":"CENTOS-6-32","Description":"Cent OS 6 | 32-bit",
                "Cpu":1,"MemoryGB":2 "DiskCount":1 "TotalDiskSpaceGB":8 "OperatingSystem":6
            },
            {
                "ID":1002,"Name":"WIN2008R2STD-64","Description":"Windows 2008 R2 Standard | 64-bit",
                "Cpu":1,"MemoryGB":4 "DiskCount":1 "TotalDiskSpaceGB":16 "OperatingSystem":18
            }
         ]
    }

#### XML

    <GetTemplatesResponse Success="true" Message="Successfully retrieved templates" StatusCode="0">
        <Templates>
            <Template ID="1001" Name="CENTOS-6-32" Description="CentOS 6 | 32-bit" Cpu="1"
            MemoryGB="2" DiskCount="1" TotalDiskSpaceGB="8" OperatingSystem="6" />
            <Template ID="1001" Name="WIN2008R2STD-64" Description="Windows 2008 R2 Standard | 64-bit" 
            Cpu="1" MemoryGB="4" DiskCount="1" TotalDiskSpaceGB="16" OperatingSystem="18" />
        </Templates>
    </GetTemplatesResponse>

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
      <td>100</td>
      <td>Authentication Failed. &nbsp;You must logon to the API prior to calling this method.</td>
    </tr>
  </tbody>
</table>