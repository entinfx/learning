# Authentication & Authorization

# Authentication vs Authorization
* Authentication - verifying identity (401 Unauthorized)
* Authorization - verifying permissions (403 Forbidden)

# Types of authentication
* Stateful - via sessions using cookies
* Stateless - token based, using JWT or OAuth

## Stateful - Session-based authentication
Sessions flow:
1. User submits credentials (e.g. email, password) to server
2. Server verifies [ideally the hash of] credentials against DB
3. Server creates a temporary user session (state) and sends a cookie to user
4. User includes the cookie with each request to server and the server validates
   the cookie against session store and grants access
5. When user logs out, server destroys session and clears cookie on user's side

Features:
* Sessions on the server are stored in the database, cache (like Redis or
  Memcached) or memory.