# EoX-PSIRT-API-Usage

The EoX and PSIRT API provides a RESTful interface to return valuable information regarding End-of-Life and vulnerability product information. This brief document will be an overview of the main features of these API interfaces, how to authorize their usage, and what sort of data can be returned depending on what is provided.

**For more EoX and PSIRT API information, please visit the following links:**

EoX API: https://developer.cisco.com/docs/support-apis/#!eox

PSIRT API: https://developer.cisco.com/docs/psirt/#!api-reference

## EoX and PSIRT API Registration

- Visit https://apiconsole.cisco.com/ and sign in at the top of the page
<br/><br/>
<br/><br/>
<p align="center">
<img src="images/register1.png" alt="register1" style="width:200px;"/>
</p>

- Click on **My Keys & Apps** on the bottom right of the screen
<br/><br/>
<br/><br/>
<p align="center">
<img src="images/register2.png" alt="register2" style="width:400px;"/>
</p>

- Click on the blue **Register a New App** icon at the top right of the page
<br/><br/>
<br/><br/>
<p align="center">
<img src="images/register3.png" alt="register3" style="width:400px;"/>
</p>

- Enter a **name** and **description** (optional) for your application
<br/><br/>
<br/><br/>
<p align="center">
<img src="images/register4.png" alt="register4" style="width:400px;"/>
</p>

- Under OAuth2.0 Credentials, select **Client Credentials** only
<br/><br/>
<br/><br/>
<p align="center">
<img src="images/register5.png" alt="register5" style="width:400px;"/>
</p>
<p align="center">
<img src="images/register6.png" alt="register6" style="width:400px;"/>
</p>
<p align="center">
<img src="images/register7.png" alt="register7" style="width:400px;"/>
</p>

- Select both **Cisco PSIRT openVuln API** and **EoX V5 API***, agree to the Terms of Service at the bottom of the page, and hit Register.

 *Note: EoX V5 API and some other Support APIs will only be visible if you have a valid Smart Net Total Care Support (SNTC) or Partner Support Service (PSS) contract with Cisco, the PSIRT openVuln API is open to the public and will be available regardless of contract status*
<br/><br/>
- An email will be sent providing details of the application registration, as well as the client ID and client secret, or you can re-visit the My Apps & Keys page to view the details
<br/><br/>
<br/><br/>
<p align="center">
<img src="images/use1.png" alt="use1" style="width:400px;"/>
</p>
<p align="center">
<img src="images/use2.png" alt="use2" style="width:400px;"/>
</p>

- Once your application is registered, you can view it from the list in the **My Apps & Keys** tab
- From the **Applications** selector you can edit your application's name/description, and add additional API access
- Take note of both the **Key** and **Client Secret** for both the 'Cisco PSIRT openVuln API' and 'EOX V5 API', you will need these to authorize your API calls from your program
<br/><br/>
<br/><br/>

## API Usage in Postman

### Importing Collections
<p align="center">
<img src="images/use11.png" alt="use11" style="width:300px;"/>
</p>
<p align="center">
<img src="images/use12.png" alt="use12" style="width:300px;"/>
</p>
- In the top left, select File > Import > Upload Files, select the two downloaded Postman collection json files from the repo, and hit **Import** in the next window to import the collections locally

### Authentication 

<p align="center">
<img src="images/use8.png" alt="use8" style="width:200px;"/>
</p>

- After importing, select a query/API call you would like to use from either EoX or PSIRT collection, in this case we will use **Query by Product ID(s)**
<br/><br/>
<br/><br/>
<p align="center">
<img src="images/use3.png" alt="use3" style="width:600px;"/>
</p>

- Under the **Authentication** tab, enter a name for your token in the **Token Name** field if you wish to change it. Using the info from **My Apps & Keys** from your Cisco API Console account, enter your **key** under **Client ID** and your **Client Secret** in the **Client Secret** field, and hit **Get New Access Token**
<br/><br/>
<br/><br/>
<p align="center">
<img src="images/use4.png" alt="use4" style="width:300px;"/>
</p>
<p align="center">
<img src="images/use5.png" alt="use4" style="width:400px;"/>
</p>

- If the request returns a success, hit the **Proceed** icon, and then the orange **Use Token** icon on the next window

*Note: Generating a new token only needs to be completed once until the token expires (it expires a set time after inactivity or until aged out, you will receive a **403 Forbidden** status and **Not Authorized** in the response field if your token expires). Once the token expires, hit the orange **Get New Access Token** and ensure the new token is selected in the **Access Token** field*

- After earning an Access Token, select your new token from the **Access Token** drop down menu. For each API in the collection, your active token will need to be selected before executing your API calls. Save your newly entered authentication details (PC: **Ctrl+S** / Mac: **Command+S**)
<br/><br/>
<br/><br/>


### API Usage


<p align="center">
<img src="images/use9.png" alt="use9" style="width:600px;"/>
</p>

- Return to the API parameters by hitting the **Params** tab, and in the case of this API call, enter the **productID** you wish to have EoX data returned on. Here, we will be querying EoX data for the PID, **CISCO1811W-AG-A/K9** . We can see the API we're using in the field that **GET** provides above the tabs
- When ready to query, hit the blue **Send** button in the top right of the Postman console
<br/><br/>
<br/><br/>
<p align="center">
<img src="images/use10.png" alt="use10" style="width:600px;"/>
</p>

- The response to the query will be displayed in the bottom window under the **Body** tab, here you can view all the response data in JSON or XML *Note: Full example responses are available in the **examples** folder in this repository*