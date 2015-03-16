{{{
  "title": "Deploy Blueprint",
  "date": "1-31-2014",
  "author": "Troy Schneringer",
  "attachments": []
}}}

Deploys a Blueprint with the given set of parameter values.

## URL

    REST: https://api.ctl.io/REST/Blueprint/DeployBlueprint/<format>
    SOAP: https://api.ctl.io/SOAP/Blueprints.asmx?op=DeployBlueprint

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
      <td>ID</td>
      <td>Int</td>
      <td>
        <p>The ID of the Blueprint to deploy.</p>
      </td>
      <td>
        <p>Yes</p>
      </td>
    </tr>
    <tr>
      <td>LocationAlias</td>
      <td>string</td>
      <td>
        <p>The alias of the Datacenter where you would like to deploy the blueprint to. If not provided, it will default to your primary datacenter.</p>
      </td>
      <td>
        <p>No</p>
      </td>
    </tr>
    <tr>
      <td>Parameters</td>
      <td>List (see below)</td>
      <td>
        <p>A list of Parameter values to use during the deployment of the Blueprint</p>
      </td>
      <td>
        <p>Yes</p>
      </td>
    </tr>
    <tr>
      <td>CustomFields</td>
      <td>Complex (see below)</td>
      <td>
        <p>Custom Fields that need to be set on each server created during blueprint deployment</p>
      </td>
      <td>
        <p>No</p>
      </td>
    </tr>
  </tbody>
</table>

### Parameter Attributes

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
      <td>Name</td>
      <td>String</td>
      <td>
        <p>The name of the Parameter being set.</p>
      </td>
    </tr>
    <tr>
      <td>Value</td>
      <td>String</td>
      <td>
        <p>The value for the Parameter.</p>
        <p><em>This value will be validated based on the type and validation rules specified by the Blueprint Parameter definition.</em>
        </p>
      </td>
    </tr>
  </tbody>
</table>

### CustomField Attributes

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
      <td>CustomFieldID</td>
      <td>Int</td>
      <td>Identifier that is associated with the Account Custom Field (Call Account/GetCustomFields for a list of all custom fields set at the account level)</td>
    </tr>
    <tr>
      <td>Value</td>
      <td>String</td>
      <td>For Text: Any value;&nbsp;For Option values, call Account/GetCustomFields to see possible values to pass in. Checkbox values should be "true" or "false".
        <br />
        <br />
      </td>
    </tr>
  </tbody>
</table>

### Examples

#### JSON

    {

      "ID": "1",

      "LocationAlias": "WA1",

      "Parameters": [

        { "Name":"T3.BuildServerTask.Password", "Value":"password" },

        { "Name":"T3.BuildServerTask.Network","Value":"VLAN_XXX" },

        { "Name":"T3.BuildServerTask.PrimaryDNS","Value":"192.168.64.19" },

        { "Name":"T3.BuildServerTask.SecondaryDNS","Value":"192.168.64.20" }

      ],

      "CustomFields": [

        { "CustomFieldID": 100,"Value": "A test"},

        { "CustomFieldID": 101,"Value": "2"},

        { "CustomFieldID": 102,"Value": "true"}

      ]

    }

#### XML

    <DeployBlueprintRequest>

        <ID>107</ID>

        <LocationAlias>WA1</LocationAlias>

        <Parameters>

            <Parameter Name="T3.BuildServerTask.Password" Value="Pass@word1" />

            <Parameter Name="T3.BuildServerTask.Network" Value="VLAN_XXX" />

            <Parameter Name="T3.BuildServerTask.PrimaryDNS" Value="192.168.64.19" />

            <Parameter Name="T3.BuildServerTask.SecondaryDNS" Value="192.168.64.20" />

        </Parameters>

        <CustomFields CustomFieldID="100" Value="Test text" />

        <CustomFields CustomFieldID="104" Value="2" />

        <CustomFields CustomFieldID="108" Value="true" />

    </DeployBlueprintRequest>

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
        <p>The ID of the Queued request to deploy the Blueprint.</p>
        <p>Status of the request can be obtained by calling the&nbsp;[GetDeploymentStatus](get-deployment-status.md)&nbsp;method.</p>
      </td>
    </tr>
  </tbody>
</table>

### Examples

#### JSON

    {

      "RequestID": 1,

      "Success":true,

      "Message":"Success",

      "StatusCode":0

    }

#### XML

    <QueuedItemResponse Success="true" Message="Success" StatusCode="0">

      RequestID>1</RequestID>

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
      <td>100</td>
      <td>Authentication Failed - You must logon to the API prior to calling this method.</td>
    </tr>
    <tr>
      <td>1210</td>
      <td>A required Parameter is missing.</td>
    </tr>
    <tr>
      <td>1211</td>
      <td>A Parameter value is invalid. &nbsp;Ensure that the supplied value meets the validation rules of the Blueprint Parameter.
        <br />
        <br />
      </td>
    </tr>
    <tr>
      <td>1212</td>
      <td>A Parameter type is invalid. &nbsp;Ensure that the supplied value is convertible to the type defined by the Blueprint Parameter.</td>
    </tr>
  </tbody>
</table>