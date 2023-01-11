Neptune new member registration API flow:

1. Verify sponsor:
	<b>GET</b> sponsors/check?sponsor_no=27617

	Response:

		{
			"success": true,
			"message": "Verification code has been sent to your sponsor's email ending with ******pam@gmail.com & mobile number ending with *******893"
		}

		{
			"success": false,
			"message": "This sponsor's left and right legs are already occupied"
		}

		{
			"success": false,
			"message": "Invalid sponsor number"
		}

2. Code verification:
	<b>POST</b> sponsors/verify

	Body:

		{
			"sponsor_id": 27617,
			"code": 123456
		}

	Response:

		{
			"success": true,
			"message": "Sponsor verification successful",
			"token": "uas987asbukdkasjd_asd9823hkksnkadad78",
			"left_node": true,
			"right_node": true
		}

		{
			"success": false,
			"message": "Invalid verificaiton code",
			"token": null,
			"left_node": null,
			"right_node": null
		}

		{
			"success": false,
			"message": "Verificaiton code has expired",
			"token": null,
			"left_node": null,
			"right_node": null
		}

3. User account registration:
	<b>POST</b>: members

	Body:

		{
			"token": "uas987asbukdkasjd_asd9823hkksnkadad78",
			"name": "Sushil Kh",
			"email": "sushil@globizs.com",
			"phone": 7629865803,
			"node": "left"
		}

	Response:

		{
			"success": true,
			"message": "Login credentials have been sent to your email address. Please check your email to proceed."
		}

		{
			"success": false,
			"message": "This email is already registered"
		}

		{
			"success": false,
			"message": "This phone number is already registered"
		}

4. User login:
	<b>POST</b>: members/login

	Body:

		{
			"username": "291029",
			"password": "98u982u938u223423kn"
		}

	Response:

		{
			"success": true,
			"message": "Login successful",
			"token": "akusndauskndasudnas9d8ashd9ash8dad",
			"unit_bought": false
		}

		{
			"success": false,
			"message": "Invalid member ID or password",
			"token": null,
			"unit_bought": false
		}

		{
			"success": false,
			"message": "This account has been suspended",
			"token": null,
			"unit_bought": false
		}

5. Fetch Neptune unit details:
	<b>GET</b>: neptune/unit

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Response:

		{
			"min": 1000,
			"max": 1000000000,
			"usd": 0.005,
			"inr": 0.034,
			"payment_modes": [{
				"id": 1, name: "With cash", "receipt_required": false
			}, {
				"id": 2, name: "Bank transfer", "receipt_required": true
			}]
		}

6. Fetch Neptune bank account details:
	<b>GET</b>: neptune/bankaccount

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Response:

		{
			"bank_name": "SBI",
			"ifsc": "SBIN0007440",
			"bank_branch": "Paona Bazar",
			"account_no": 31254795440,
			"account_holder_name": "NEPTUNE MLM"
		}

7. Buy unit:
	<b>POST</b>: neptune/buy

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Body <b>(Form data)</b>:

		"units": 2000
		"payment_mode": 2
		"reference_no": "IKUJNASSDF9390293"
		"receipt": ** MULTIPART FILE **

	Response:

		{
			"success": true,
			"message": "Success! Please wait while we verify your payment"
		}

8. Get dashboard:
	<b>GET</b>: member/dashboard

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Response:

		{
			"success": true,
			"member_id": "291029",
			"name": "Sushil Kh",
			"membership_confirmed": false,
			"kyc": false,
			"unit_balance": 0,
			"e_pocket_balance": 0,
			"usd": 0.005,
			"inr": 0.034
		}

9. Get dashboard images:
	<b>GET</b>: neptune/dashboard-images

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Response:

		{
			"images": [{
				"url": "https://mlm.neptunetourist.com/images/290nn32842342.jpg"
			}, {
				"url": "https://mlm.neptunetourist.com/images/87yh4sh348943.jpg"
			}, {
				"url": "https://mlm.neptunetourist.com/images/90jkh3675jhbs.jpg"
			}]
		}

10. Get ID proof types
	<b>GET</b>: lists/id-proof-types

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Response:

		[{
			"id": 1, "name": "AADHAAR Card"
		}, {
			"id": 2, "name": "PAN Card"
		}, {
			"id": 3, "name": "Driving License"
		}, {
			"id": 4, "name": "Passport"
		}]

11. Get countries
	<b>GET</b>: lists/countries

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Response:

		[{
			"id": 1, "name": "India"
		}, {
			"id": 2, "name": "USA"
		}, {
			"id": 3, "name": "UK"
		}, {
			"id": 4, "name": "Japan"
		}]

12. Get states
	<b>GET</b>: lists/states?country_id=1

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Response:

		[{
			"id": 1, "name": "Andhra Pradesh"
		}, {
			"id": 2, "name": "Arunachal Pradesh"
		}, {
			"id": 3, "name": "Bihar"
		}, {
			"id": 4, "name": "Chattisgarh"
		}]

13. <b>[CANCELLED]</b> Get districts
	<b>GET</b>: lists/districts?state_id=21

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Response:

		[{
			"id": 1, "name": "Bishnupur"
		}, {
			"id": 2, "name": "Chandel"
		}, {
			"id": 3, "name": "Churachandpur"
		}, {
			"id": 4, "name": "Imphal East"
		}]

14. Get KYC profile:
	<b>GET</b>: kyc/index

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Response:

		{
			"id_proof_type_id": 2,
			"id_proof_type": "PAN Card",
			"id_no": "OLFPS3023P",
			"address": "Lane no. 2, Kwakeithel Thokchom Leikai",
			"landmark": "Kwakeithel UPHC",
			"country_id": 21,
			"country": "India",
			"state_id": 23,
			"state": "Manipur",
			"district: "Imphal West",
			"pin_code": 795001,
			"id_proof_file": "https://asjdnksadsad.jpg",
			"address_proof_file": "https://asjdnksadsad.jpg",
		}

15. Update KYC:
	<b>PUT</b>: kyc/data

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Body:

		{
			"id_proof_type_id": 2,
			"id_no": "OLFPS3023P",
			"address": "Lane no. 2, Kwakeithel Thokchom Leikai",
			"landmark": "Kwakeithel UPHC",
			"country_id": 21,
			"state_id": 23,
			"district": "Imphal West",
			"pin_code": 795001
		}

	Response:

		{
			"success": true,
			"message": "Successfully updated"
		}

16. Update KYC id-proof file:
	<b>PUT</b>: kyc/id-proof

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Body <b>(Form data)</b>:

		"id_proof_file": ** MULTIPART FILE **

	Response:

		{
			"success": true,
			"message": "ID proof document successfully updated"
		}

17. Update KYC address proof file:
	<b>PUT</b>: kyc/address-proof

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Body <b>(Form data)</b>:

		"address_proof_file": ** MULTIPART FILE **

	Response:

		{
			"success": true,
			"message": "Address proof document successfully updated"
		}

18. Get transferable amount
	<b>GET</b>: transfers/available

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Response:

		{
			"transferable_amount": 200
		}


19. Get member details (for transfer)
	<b>GET</b>: members/{{ member_id }}

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Response:

		{
			"success": true,
			"message": "Member details"
			"member_id": 745215,
			"name": "Khundrakpam Sushil",
			"phone": *******803
		}

		{
			"success": false,
			"message": "Invalid member ID",
			"member_id": null,
			"name": null,
			"phone": null
		}

20. Send OTP to for transfer request (valid for 15 minutes)
	<b>POST</b>: transfers/send-otp

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Body:

		{
			"member_id": 745215,
		}

	Response:

		{
			"success": true,
			"message": "OTP has been sent to the member's mobile number *******803. Valid for 15 minutes"
		}

		{
			"success": false,
			"message": "Invalid member ID"
		}

21. Transfer amount
	<b>POST</b>: transfers

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Body:

		{
			"member_id": 745215,
			"otp": 123456,
			"amount": 50
		}

	Response:

		{
			"success": true,
			"message": "Amount has been successfully transferred to member ID: 745215"
		}

		{
			"success": false,
			"message": "Failed to transfer amount. Reason: Invalid transfer amount/balance"
		}

		{
			"success": false,
			"message": "Failed to transfer amount. Reason: Invalid member ID"
		}

		{
			"success": false,
			"message": "Failed to transfer amount. Reason: Invalid OTP"
		}

		{
			"success": false,
			"message": "Failed to transfer amount. Reason: OTP has expired"
		}

22. Transfers history
	<b>GET</b>: transfers?page=1&limit=10

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Response:

		[{
			"id": 234, "member_id": 745215, "transfer_amount": 50, "transfer_date": "2022-12-25", "member_name": "Khundrakpam Sushil"
		}, {
			"id": 504, "member_id": 745221, "transfer_amount": 50, "transfer_date": "2022-11-10", "member_name": "Mr. Jugindro"
		}]
