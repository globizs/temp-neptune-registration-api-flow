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
			"unit_bought": false,
			"membership_confirmed": false,
			"kyc": false
		}

		{
			"success": false,
			"message": "Invalid member ID or password",
			"token": null,
			"unit_bought": false,
			"membership_confirmed": false,
			"kyc": false
		}

		{
			"success": false,
			"message": "This account has been suspended",
			"token": null,
			"unit_bought": false,
			"membership_confirmed": false,
			"kyc": false
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
				"id": 1, name: "With cash"
			}, {
				"id": 2, name: "Bank transfer"
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
			"unit_bought": true,
			"membership_confirmed": false,
			"kyc": false,
			"name": "Sushil Kh",
			"member_id": "291029",
			"unit_balance": 0,
			"e_pocket": 0,
			"images": [{
				"url": "https://mlm.neptunetourist.com/images/290nn32842342.jpg"
			}, {
				"url": "https://mlm.neptunetourist.com/images/87yh4sh348943.jpg"
			}, {
				"url": "https://mlm.neptunetourist.com/images/90jkh3675jhbs.jpg"
			}]
		}

9. Neptune rate:
	<b>GET</b>: neptune/rate

	<div><b>Authorization: Bearer </b>akusndauskndasudnas9d8ashd9ash8dad</div>

	Response:

		{
			"usd": 0.005,
			"inr": 0.034
		}
