# Turkey Hayat Eve Sığar Corona Statistics and Prevention App API

### API Details
<table>
	<tbody>
		<tr>
			<td>Host</td>
			<td>https://hessvc.saglik.gov.tr</td>
		</tr>
		<tr>
			<td>Protocol</td>
			<td>HTTP/1.1</td>
		</tr>
	</tbody>
</table>

### Required Headers
<table>
	<thead>
		<tr>
			<th>Header</th>
			<th>Example</th>
			<th>Note</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Authorization</td>
			<td>See "Authorization" below</td>
			<td>Expires in 1 MONTH</td>
		</tr>
		<tr>
			<td>Content-Type</td>
			<td>application/json</td>
			<td></td>
		</tr>
	</tbody>
</table>

### Known Endpoints
Note: All endpoints are concatenated to the host url

Note: All curls must be sent with the headers as well (the only exceptions are that the /api/send-code-to-login and /api/authenticate-with-code calls must not have the Authentication header)
<table>
   <thead>
      <tr>
         <th>Endpoint</th>
         <th>Purpose</th>
         <th>Data</th>
         <th>Method</th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td>/api/send-code-to-login</td>
         <td>For authenticating</td>
         <td>{"phone":"+905*********"}</td>
         <td>POST</td>
      </tr>
      <tr>
       <td>/api/authenticate-with-code</td>
       <td>Authentication</td>
       <td>{"password":"******","phone":"+905*********","rememberMe":true}</td>
		 <td>POST</td>
	  </tr>
      <tr>
		 <td>/api/account-with-token</td>
		 <td>All account information including SHA-256 hashed TCKNO, phone number and userId etc.</td>
		 <td>{}</td>
		 <td>GET</td>
	  </tr>
     	<tr>
		 <td>/services/hescodeproxy/api/hes-codes-tr</td>
		 <td>Create HES code</td>
		 <td>{"child_tckn":null,"description":"hes","expiration_date":null}</td>
		 <td>POST</td>
	  </tr>
      <tr>
         <td>/services/hescodeproxy/api/hes-codes</td>
         <td>Get HES codes</td>
         <td>{}</td>
         <td>GET</td>
      </tr>
	<tr>
		<td>/services/familyservice/api/add-family-member</td>
		<td>Add family member</td>
		<td>{"invitedUserPhone":"+905*********","ownerHealthInfoAllowed":true,"ownerLocationInfoAllowed":true,"relationName":"***"}</td>
		<td>POST</td>
	   </tr>
      <tr>
         <td>/services/familyservice/api/account-family-members</td>
         <td>Get family numbers</td>
         <td>{}</td>
         <td>GET</td>
      </tr>
      <tr>
         <td>/services/statisticservice/api/latest-generic-statistics</td>
         <td>LATEST STATISTICS</td>
         <td>{}</td>
         <td>GET</td>
      </tr>
   </tbody>
</table>


### Authorization
<h5> <strong> the bearer token </strong></h5>

bearer token consist of base64 encoded string with the following format and some static base64:

{"alg":"HS512"}{"sub":"000-000-000-000-000","auth":"ROLE_USER","oid":"0000000","exp": [**timestamp**] }

concatenated with some static base64 bytes

(sub is userId)

