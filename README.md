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
			"unit_bought": false,
			"membership_confirmed": false,
			"kyc": false
		}

		{
			"success": false,
			"message": "Invalid member ID or password",
			"unit_bought": false,
			"membership_confirmed": false,
			"kyc": false
		}

		{
			"success": false,
			"message": "This account has been suspended",
			"unit_bought": false,
			"membership_confirmed": false,
			"kyc": false
		}

5. Fetch Neptune unit details:
	<b>POST</b>: neptune/unit

	Response:

		{
			"min": 1000,
			"max": 1000000000,
			"usd": 0.005,
			"inr": 0.034
		}

6. Fetch Neptune bank account details:
	<b>POST</b>: neptune/bankaccount

	Response:

		{
			"bank_name": "SBI",
			"ifsc": "SBIN0007440",
			"bank_branch": "Paona Bazar",
			"account_no": 31254795440,
			"account_holder_name": "NEPTUNE MLM"
		}

7. 
