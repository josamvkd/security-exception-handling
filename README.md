🔐 Spring Security – JWT Exception Handling Scenarios

This project demonstrates how different authentication and authorization failures are handled using Spring Security with JWT.

You can replicate the following scenarios using Postman.

📌 Prerequisites

Before testing the scenarios:

Create two users in the system:

ADMIN role

USER role

Generate a valid JWT token using the authentication endpoint.

🚀 Test Scenarios (Using Postman)
✅ Scenario 1 – Invalid Credentials

Endpoint:

POST /products/authenticate


Request Body:

{
  "username": "test",
  "password": "wrong password"
}


Expected Result:

HTTP Status: 401 Unauthorized

Error: BadCredentialsException

Message: Authentication failed

Description:
Occurs when incorrect username or password is provided.

✅ Scenario 2 – Access Denied (Insufficient Role)

Condition:

Authenticate successfully as a USER

Try accessing an endpoint restricted to ADMIN

Example Endpoint:

GET /products/2


Expected Result:

HTTP Status: 403 Forbidden

Error: AccessDeniedException

Message: Access Denied

Description:
Occurs when a user does not have sufficient privileges to access a protected resource.

✅ Scenario 3 – Invalid JWT Signature

Condition:

Generate a valid JWT token

Manually modify the token (e.g., remove or change a character)

Expected Result:

HTTP Status: 403 Forbidden

Error: SignatureException

Message: Invalid JWT signature

Description:
Occurs when the JWT token signature is tampered with or corrupted.

✅ Scenario 4 – Expired JWT Token

Condition:

Generate a valid JWT token

Wait until the token expires

Attempt to access a secured endpoint

Expected Result:

HTTP Status: 403 Forbidden

Error: ExpiredJwtException

Message: JWT token has expired

Description:
Occurs when the token's expiration time has passed.
