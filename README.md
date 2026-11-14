# Lesson6_Activity
Lesson 6 Activity answers

Q1. Why return a resource instead of the model itself?  
A resource is an explicit API contract. It controls which fields clients receive and prevents accidental exposure of database columns.

Q2. What does whenLoaded() do if the course wasn't eager-loaded?  
It omits the relationship from the response without querying for it. This helps the resource avoid causing N+1 queries.

Q3. Why limit guests by IP but users by ID?  
A guest has no authenticated user ID, so the IP address provides a practical client key. Authenticated requests are counted per user, so people sharing an IP do not share one user's request limit.

Verify the activity

Request GET /api/students with a valid bearer token.
Confirm the response includes data, links, and meta.
Confirm student objects do not include user_id, created_at, or updated_at.
Confirm each loaded course object includes id and name.
Request a student owned by another user and confirm its email key is absent; the owner's token should see the email.
Send six requests to POST /api/tokens/create within one minute and confirm the sixth receives HTTP 429.
