Neptune new member registration API flow:

1. Verify sponsor:
	GET sponsors/check?sponsor_no=27617

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
	POST sponsors/verify

	Body:
		{
			"sponsor_id": 27617,
			"code": 123456
		}

	Response:
		{
			"success": true,
			"message": "Sponsor verification successful",
			"token": "uas987asbukdkasjd_asd9823hkksnkadad78"
		}

		{
			"success": false,
			"message": "Invalid verificaiton code",
			"token": null
		}

		{
			"success": false,
			"message": "Verificaiton code has expired",
			"token": null
		}

3. User account registration:
	POST: members

	Body:
		{
			"token": "uas987asbukdkasjd_asd9823hkksnkadad78",
			"name": "Sushil Kh",
			"email": "sushil@globizs.com",
			"phone": 7629865803
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
	POST: members/login

	Body:
		{
			"username": "291029",
			"password": "98u982u938u223423kn"
		}

	Response:
		{
			"success": true,
			"message": "Login successful",
			"membership_confirmed": false,
			"kyc": false
		}

		{
			"success": false,
			"message": "Invalid member ID or password",
			"membership_confirmed": false,
			"kyc": false
		}

		{
			"success": false,
			"message": "This account has been suspended",
			"membership_confirmed": false,
			"kyc": false
		}

5. Fetch Neptune unit details:
	GET: unit

	Response:
		{
			"min": 1000,
			"max": 1000000000,
			"usd": 0.005,
			"inr": 0.034
		}

6. 
