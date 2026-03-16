**[Backend engineering concepts]{.underline}**

**[Concepts to be covered:]{.underline}**

\* a high level understanding of the internet.

\* HTTP and it's protocols.

\* Routing.

\* Serialization and deserialization.

\* Authentication and Authorization.

\* Validation and transformation.

\* Middlewares.

\* Request context.

\* Handlers or controllers.

\* CRUD deepdive.

\* Rest best practices.

\* Databases.

\* Business logic layer (BLL).

\* Caching.

\* Transactional Emails.

\* Task queuing and scheduling.

\* Elasticsearch.

\* Error handling.

\* Config management.

\* Logging , monitoring & observability.

\* Graceful shutdown.

\* Security.

\* Scaling and performance.

\* Concurrency and parallelism.

\* Object storage and large files.

\* Realtime backend systems.

\* Testing and code quality.

\* 12 factor app principles.

\* OpenAPI standard.

\* Webhooks.

\* DevOps for backend engineers.

**[Expectations]{.underline}**

1 -- Story & Philosophy of Backend engineering.

2 -- Implementation ( the language and ecosystem we will use for backend
).

3 -- Building Production level Projects.

**[Backend definition:]{.underline}**

Backend in it's traditional definition is a computer (server) listening
for http/https , websockets , grpc ... requests on any port 80/443 that
is accessible over the internet so that clients can send or get data
from or to it based on the request , we call it a server because it
serves some content whether it's static files like images or html , JS
or JSON and accepts data if the client sends something.

**[Why Use Backends ?]{.underline}**

I allows us to store data in a presisitent and secures way.

**[Why Not Use Frontends Instead of Backends ?]{.underline}**

The browsers is what does the treatment instead of our server , wich
means that any code we wrote gets executed loaded by the browser and
executed on that level.

The issues with this:

\* Browser runtimes are sandbox environements wich means they are
isolated from our OS , wich makes the browser access limited amount of
ressources like the DOM , localStorage , cookies and external APIs.

The reason to why we can't use clients to store data is :

\* Security restrictions of browsers.

\* CORS restrictions (Because backends often times need to connect to
external domains).

\* Browsers can not connect or maintain connexions to databases servers.

\* Computing power (the user's client may not have the process power to
process the tasks needed).

**[Benefits of learning backend engineering from first
principles:]{.underline}**

1 -- breaking down the most complex systems into the most basic problems
gives you a massive edge.

2 -- Seeing the big picture (understand the logic , routing , and all
complex and over engineered parts of the system).

3 -- Faster onboarding (you can use and dive to any language or
framework to build systems with it without wasting so much time on it's
syntax or ecosystem because you understood the principles of backend
engineering).

4 -- 10x faster in new projects.

5 -- Syntax fatigue (first principles minimizes the syntax learning
fatigue).

6 -- Always choosing the right tools for the right Job.

7 -- More employable and versatile.

**[HTTP/HTTPS for backend engineering]{.underline}**

Http and Https is the way backend and frontend connect and talk to each
other.

The two ideas that are the heart of http:

\* Statless: it has no memorie of past interactions , and all the data
required should be in that request.

\* Client-server model: is the famous architecture we know.

![](media/image1.png){width="4.414583333333334in" height="1.7875in"}

NOTE: as we know for this communication to happen there must be an
established connection between the client and the server , the
connection is established via TCP so that the paquets or the data isn't
lost in transfer.

**[Request Message in http:]{.underline}**

![](media/image2.png){width="6.329861111111111in" height="3.1125in"}

**[Response Message in http:]{.underline}**

![](media/image3.png){width="6.000694444444444in"
height="3.015972222222222in"}

![](media/image4.png){width="6.6930555555555555in" height="4.86875in"}

**[Http Headers:]{.underline}**

The http headers are key value pairs of different params that are sent
over request or received from response

(also called metadata).

**[Categories of http Headers:]{.underline}**

[1 - Request headers: sent from the client to the server:]{.underline}

\* User agent : what kind of client is that (browser , postman , mobile
app).

\* Authorization : sends diferrent cridentials like tokens to identify
the user.

\* Accept : what kind of content we are sending.

[2 -- General headers:]{.underline}

\* Date : date of the message.

\* Cache control : different caching mecanism.

\* Connection : wether the connection should be kept alive or close it.

[3 -- Representation headers:]{.underline}

presents informations obout the body of the message.

\* Content-Type : what's the type of the content iin the body.

\* Content-Length.

\* Content-Encoding : what type of encoding used for the body.

\* Etag : unique id generaly used for caching

[4 -- Security headers:]{.underline}

used to enhance the security of the request or response by handling
content loading , encryption...

\* Strict-Transport-Security (HSTS)

\* Content-Security-Policy (CSP).

\* X-Frame-Options.

\* X-Content-Type-Options.

\* Set-Cookie.

**[!!! Look Into these concepts More in the future for better
understanding]{.underline}**

**[there are two main caracteristics of http:]{.underline}**

**[Extensibility:]{.underline}** http is very extensible by adding
numerous http headers without altering the underlying protocol.

**[Remote Controll:]{.underline}** http headers act as a remote
controller of the server side , because they influence how the server
responds or process requests.

**[The http methods:]{.underline}**

Get -- Post -- Put -- Patch -- Delete.

Methods/verbs that define the intent of the request.

Idempotent methods (gives the same result) :

Get -- Put -- Delete.

Non-Idempotent methods (different result each time) :

Post.

**Option** method: used in the CORS flow (same origin policy),

we probably won't use it as a developper but it's good to know about it.

\*\*\* So what it does is to fetch the capabilities of the server for a
cross origin request.

This method is also used with preflight requests(look more
into![](media/image5.png){width="6.304166666666666in"
height="3.2888888888888888in"} this).

**[Response codes in http:]{.underline}**

These response codes exist to communicate the result of a request in a
standarized way.

[Information]{.underline}: 1xx (number of the codes is starting with)

[Success]{.underline}: 2xx (200 = OK , 201 = created , 204 = no content)

[Redirection]{.underline}: 3xx (301 = url/route moved permanently to a
new url ,

302 = temporary located to a new url,

304 = the resource isn't modified).

[Client Error]{.underline}: 4xx (400 = bad request,

401 = not authorized,

403 = forbidden,

404 = not found,

405 = method not allowed,

409 = conflict,

429 = too many requests (rate limiting)

[Server Error]{.underline}: 5xx (500 = internal server error,

501 = not implemented,

502 = bad getaway (returned by proxies),

503 = anavailable

504 = getaway timeout.

**[Http Caching:]{.underline}**

Is a technique used to store copies of responses for reuse

reducing the number of repeted requests to the server , this improves
load time , reduces bandwith and decreases server load , because the
client doesn't need to download a lot of data and the server doesn't
need to send a lot of data.

!! You can look more into this type of caching but for development
something like react querry removes the headache.

**[Content Negotiation:]{.underline}**

The client specifies wish type of content it is comfortable with and the
server returns the response in that format (JSON , XML , HTML...) , if
not compatible the server returns the response in a fallback format.

![](media/image6.png){width="6.009722222222222in"
height="3.220833333333333in"}

**[Handling large requests and responses:]{.underline}**

In this part we will see how the client can send large files or large
requests to the server , and how the server can send large responses to
the client.

1 -- Multi-Part requests : used for sending large files form client to
the server in a multi -- part way ( binary is sent in chuncks).

2 -- Streaming responses from the server (Real-Time Updates): is the way
where the server streams responses meaning it sends it in chuncks and
client gets the response in real time.

**[SSL , TLS , HTTPS:]{.underline}**

SSL : the original protocol to secure connection between client and
server by encrypting data.

TLS : Replacement of SSL , modern and more secure than SSL.

HTTPS : HTTP + SSL/TLS.

**[What is Routing in backend ?]{.underline}**

How the requests find their way home (or to the exact route) ?

Example : GET/api/users (mapping a url mapping to a server side logic).

**[Types of routing:]{.underline}**

**[Static Routing:]{.underline}**

routes that don't have any variable parameters inside the URL.

EX : POST/api/books

**[Dynamic Routing:]{.underline}**

routes that have variable parameters inside the URL.

EX : GET/api/books/12

**[Querry params Routing:]{.underline}**

routes that contain a querry variable , for example in searching using a
string , helps us sending some values through the get request by sending
a querry

EX : GET/api/search?query=some+value

**[Nested Routing:]{.underline}**

Generally used when we have relationships between resources in our
server logic , and we want to access some nested or semantic data.

EX : GET/api/users/123/posts/453

**[Route versioning and deprecation:]{.underline}**

a very common practice in rest APIs , basically giving versions to our
APIs , let's say for example we currently our endpoint is return
responses in a specific format , but in the future we want to return a
different format of the same endpoint (if we start building a mobile
app) , this is where versioning comes to play.

EX : GET/api/v1/users

Get/api/v2/users

**[Catch all route:]{.underline}**

a route that will do a catch all handling , basically when a user hits
an api that doesn't exit and displaying a friendly message.

EX : GET/api/v3/products

returns "Route not found"

**[Serialization and deserialization]{.underline}**

How can client and server can make sense of data that is being sent or
received.

Serialization and deserialization is converting from and to a standard
data format so that the client and the server can be able to work with
that data.

**[Serialization Standars:]{.underline}**

There is a lot of standards of serialization standards but the most
common one in rest APIs is JSON serialization.

[Other standards :]{.underline} YAML , XML (+ JSON) and are text based
serialization and other formats like Binary format (Protobuf)

![](media/image7.png){width="6.6930555555555555in"
height="3.011111111111111in"}

**[Authentication and Authorization]{.underline}**

[Authentication:]{.underline} is to answer who are you.

[Authorization:]{.underline} is answer in a particular context or
application.

In 21 st century , new technologies arised , wish required more secure
authentication , EX : Oauth , JWT...

Some concepts we are going to talk about:

Sessions , JWTs , cookies

**[Sessions :]{.underline}** is a concept that came into play when
websites evolved from static websites to dynamic ones , and knowing that
http is stateless and we want to keep track of the user state of login
sessions were created.

A **session** is a way for a server to remember a user **across multiple
HTTP requests**. Since HTTP is stateless (each request is independent),
sessions give you "memory".

### [How sessions work (step-by-step):]{.underline}

1.  **User logs in** (username + password)

2.  **Server verifies credentials**

3.  **Server creates a session**

    -   Stores session data server-side (e.g. userId, roles, expiry)

    -   Generates a **session ID**

4.  **Session ID is sent to the client**

    -   Usually via a **cookie** (e.g. JSESSIONID, session_id)

5.  **Client sends the cookie on every request**

6.  **Server looks up the session**

    -   If valid → user is authenticated

    -   If expired/invalid → user is logged out

![](media/image8.png){width="5.521527777777778in"
height="2.761111111111111in"}

**[JWTs]{.underline}** : the emergance of JWTs was caused by the growing
size of software and appearance of distributed systems , wich caused
managing millions of users sessions not efficient and costing in memory.

A **JWT (JSON Web Token)** is a **self-contained token** that proves a
user is authenticated.\
Instead of the server "remembering" you, **the token carries the
proof**.

## [How JWT authentication works (step-by-step)]{.underline}

1.  **User logs in** (credentials)

2.  **Server verifies credentials**

3.  **Server creates a JWT**

    -   Includes user info (e.g. userId, roles)

    -   Signs it with a secret or private key

4.  **JWT is sent to the client**

    -   Usually in the response body

5.  **Client stores the JWT**

    -   localStorage, sessionStorage, or cookie

6.  **Client sends JWT on every request**

    -   Typically in the Authorization header

        Authorization: Bearer \<token\>

7.  **Server verifies the signature**

    -   If valid & not expired → authenticated

## [What's inside a JWT?]{.underline}

A JWT has **3 parts**:

header.payload.signature

-   **Header** → algorithm + token type

-   **Payload** → claims (userId, roles, exp)

-   **Signature** → prevents tampering

⚠️ Payload is **Base64 encoded, not encrypted** (anyone can read it).

## [Why JWTs are used in authentication]{.underline}

-   **Stateless** → no server-side storage

-   Scales well (microservices, APIs)

-   Works across domains & platforms

-   Perfect for mobile apps & SPAs

## [Where data is stored]{.underline}

**Client-side**

-   JWT (contains identity + claims)

**Server-side**

-   Nothing (except signing key)

### ✅ Advantages

-   Stateless → no server-side storage

-   Scales very well (APIs, microservices)

-   Works across domains & platforms

-   Fast verification (signature check only)

### ❌ Inconveniences

-   Hard to revoke before expiration

-   Logout is not immediate

-   Payload is readable (not encrypted)

-   Security risks if stored poorly (XSS)

-   ![](media/image9.png){width="7.097916666666666in"
    > height="3.6645833333333333in"}Token size bigger than session IDs

When learning we can implement these different types of authentications
, but in production systems we should use an auth provider to reduce the
headache and ensure security.

**[Cookies:]{.underline}**

A **cookie** is a **small piece of data** stored by the browser and
**automatically sent with every request** to the same domain.

## How cookies are used in authentication

1.  **User logs in**

2.  **Server authenticates the user**

3.  **Server sets a cookie**

    -   Usually contains a **session ID** or a **JWT**

4.  **Browser stores the cookie**

5.  **Browser automatically sends the cookie** on every request

6.  **Server validates the cookie**

    -   Valid → user authenticated

    -   Invalid/expired → user logged out

## What's inside an auth cookie?

-   Session ID **(most common)**

-   OR JWT

-   Never raw passwords

## Why cookies are useful for auth

-   Automatic sending (no manual headers)

-   Works naturally with browsers

-   Can be secured with flags:

    -   HttpOnly

    -   Secure

    -   SameSite

### **[Authentication Types:]{.underline}**

**[1 -- Statefull Authentication:]{.underline}**

![](media/image10.png){width="6.404861111111111in" height="2.5375in"}

**[The server stores authentication state (a session) for each
user.]{.underline}**

### How it works

-   User logs in

-   Server creates a **session**

-   Client stores a **session ID** (usually in a cookie)

-   Server checks the session on every request

### When it's used

-   Traditional web apps

-   Server-rendered apps

-   Admin dashboards

### ✅ Pros

-   Easy logout (invalidate session)

-   Strong server control

-   Simple to implement

### ❌ Cons

-   Harder to scale

-   Requires shared session storage

-   Server memory usage

**[2 -- Stateless Authentication:]{.underline}**

![](media/image11.png){width="6.6930555555555555in"
height="8.405555555555555in"}

**[The server does not store auth state. The client sends proof every
request (usually a JWT).]{.underline}**

### How it works

-   User logs in

-   Server issues a **token**

-   Client sends token with each request

-   Server verifies token signature

### When it's used

-   REST APIs

-   Microservices

-   Mobile & SPA apps

### ✅ Pros

-   Highly scalable

-   No server-side storage

-   Works across services

### ❌ Cons

-   Hard to revoke tokens

-   Logout is not immediate

-   Token security is critical

**[3 -- API key authentication:]{.underline}**

![](media/image12.png){width="6.386805555555555in"
height="2.4138888888888888in"}

**[Clients authenticate using a static key assigned to
them.]{.underline}**

### How it works

-   Server generates an API key

-   Client sends it in headers or query params

-   Server validates the key

### When it's used

-   Public APIs

-   Server-to-server communication

-   Rate-limited services

### ✅ Pros

-   Very simple

-   Easy to implement

-   Good for identifying clients

### ❌ Cons

-   No user identity

-   Keys can be leaked

-   Weak security alone

![](media/image13.png){width="6.763194444444444in"
height="3.798611111111111in"}**[4 -- Oauth 2.0:]{.underline}**

**[A delegated authorization framework that allows apps to access user
data without passwords.]{.underline}**

### How it works (simplified)

-   User logs in via a provider (Google, GitHub)

-   App receives an **access token**

-   Token is used to call APIs

### When it's used

-   Login with Google/GitHub

-   Third-party API access

-   Enterprise systems

### ✅ Pros

-   Very secure

-   No password sharing

-   Industry standard

### ❌ Cons

-   Complex to implement

-   Many flows & concepts

-   Easy to misconfigure

**[comeback later and explore more of Oauth(from 1.0 to
2.0)]{.underline}**

**[and also learn about OIDC]{.underline}**

**[The question is when to use wich type of authentication
?]{.underline}**

## 

## 

## 

## **[When to use Stateful (Sessions)]{.underline}**

**Use it when:**

-   You have a **classic web app**

-   Backend and frontend share the same domain

-   You want **easy logout & control**

-   Scaling is not extreme

**Typical examples:**

-   Admin dashboards

-   Server-rendered apps (Spring MVC, Django, Rails)

👉 **Choose sessions if:** *browser-based app + simplicity + control*

##  {#section-3 .unnumbered}

## When to use **Stateless (JWT)** {#when-to-use-stateless-jwt .unnumbered}

**Use it when:**

-   You're building a **REST API**

-   You have **multiple clients** (web + mobile)

-   You expect **high scale**

-   Microservices architecture

**Typical examples:**

-   Next.js + React Native + Spring Boot API

-   Mobile apps

-   Distributed systems

👉 **Choose JWT if:** *API + multiple clients + scalability*

##  {#section-4 .unnumbered}

##  {#section-5 .unnumbered}

## When to use **API Keys** {#when-to-use-api-keys .unnumbered}

**Use it when:**

-   No real "users"

-   You want to **identify an application**

-   Server-to-server communication

-   Rate limiting or usage tracking

**Typical examples:**

-   Weather APIs

-   Payment gateways

-   Internal services

👉 **Choose API keys if:** *machine → machine*

##  {#section-6 .unnumbered}

## When to use **OAuth 2.0** {#when-to-use-oauth-2.0 .unnumbered}

**Use it when:**

-   You don't want to manage passwords

-   Users log in with **Google / GitHub / Apple**

-   Your app accesses **another service's data**

-   Enterprise or third-party integrations

**Typical examples:**

-   "Login with Google"

-   GitHub apps

-   SaaS integrations

👉 **Choose OAuth if:** *third-party login or delegated access*

##  {#section-7 .unnumbered}

##  {#section-8 .unnumbered}

## 🧠 Simple rule of thumb {#simple-rule-of-thumb .unnumbered}

  -----------------------------------------------------------------------
  Situation                  Best choice
  -------------------------- --------------------------------------------
  Web app only               Sessions

  API + web + mobile         JWT

  Service → service          API Key

  Login with Google          OAuth 2.0
  -----------------------------------------------------------------------

**[Authorization:]{.underline}**

as we said authorization is what are you allowed to do in a system , or
providing specific permissions to specific users on a platform or
application.

To implement authorization in our apps we follow a principle called
RBAC(role based access control).

**Authorization** answers the question:\
👉 **"What is this authenticated user allowed to do?"**

-   **Authentication** = who you are

-   **Authorization** = what you can access

## How authorization is used (high level)

1.  User **authenticates** (session, JWT, OAuth, etc.)

2.  Server **identifies the user**

3.  Server **checks permissions**

4.  Request is **allowed or denied**

Example:

> You are logged in ✅ but you can't delete this resource ❌

## Common authorization models

### 1️⃣ Role-Based Access Control (RBAC)

**Idea:** Users have roles, roles have permissions.

**Example roles**

-   USER

-   ADMIN

-   MODERATOR

**How it's used**

-   Endpoints protected by roles

-   Example: only ADMIN can delete users

**Pros**

-   Simple

-   Easy to understand

**Cons**

-   Becomes rigid at scale

### 

### 2️⃣ Permission-Based Authorization

**Idea:** Users have **explicit permissions**, not just roles.

**Example permissions**

-   resource:read

-   resource:write

-   user:delete

**Pros**

-   Very flexible

-   Fine-grained control

**Cons**

-   More complex to manage

### 

### 3️⃣ Ownership-Based Authorization

**Idea:** Users can only access **their own data**.

**Example**

-   User can update **their own profile**

-   Cannot access others' resources

**Pros**

-   Very secure

-   Natural for user data

**Cons**

-   Needs extra checks per request

### 

### 4️⃣ Policy-Based Authorization (Advanced)

**Idea:** Rules (policies) decide access dynamically.

**Example**

-   Time-based access

-   Location-based access

-   Attribute-based rules

**Pros**

-   Very powerful

**Cons**

-   Harder to implement & debug

## How authorization is implemented (practically)

### Step 1: Identify the user

-   From **session**

-   From **JWT claims**

-   From OAuth token

### Step 2: Load permissions

-   From DB

-   From token claims

-   From roles

### Step 3: Check access

-   Before controller logic

-   Or inside service layer

### Step 4: Enforce decision

-   Allow → proceed

-   Deny → 403 Forbidden

**[Error messaging:]{.underline}**

when a user is trying to authenticate , and he uses some invalid email ,
you should not display informative errors like (invalid email) or
(invalid password) , instead you should send general errors like
(invalid credentials).

**[Timing attacks:]{.underline}**

when a server locks a users account for a time , due to multiple failed
auth requests , an attacker might try use response delays to try to
break auth

**[Validation and Transformation]{.underline}**

This topic is mainly reserved for the security and integrity of the
application , and keeping a set of rules when desiging our api's.

The validation and transformation also insures that our systems don't
fall into unckown states and stops working.

## **[What is Validation?]{.underline}**

**Validation** is the process of **checking if input data is
acceptable** before you use or store it.

In short:\
👉 *"Is this data valid according to my rules?"*

Examples:

-   Is the email empty?

-   Is the password at least 8 characters?

-   Is the age ≥ 18?

-   Is this UUID actually a UUID?

If validation fails → you **reject the request**.

##  {#section-12 .unnumbered}

## [What is **Transformation**?]{.underline} {#what-is-transformation .unnumbered}

**Transformation** is about **changing data into the format you want**
after (or while) validating it.

In short:\
👉 *"Convert the data into the shape my app expects."*

Examples:

-   \" simo \" → \"simo\" (trim spaces)

-   \"EMAIL@GMAIL.COM\" → \"email@gmail.com\"

-   \"42\" (string) → 42 (number)

-   JSON → Java object / DTO

👉 Validation checks correctness\
👉 Transformation prepares the data for usage

## 

## [Validation Types]{.underline}

### **[Syntactic Validation]{.underline}** {#syntactic-validation .unnumbered}

**Checks the structure / format** of the data.

It does **NOT** care about meaning --- only shape.

Examples:

-   Email matches pattern something@something.com

-   Password length ≥ 8

-   UUID format is correct

-   JSON is well-formed

❌ Invalid:

email = \"not-an-email\"

✅ Valid:

email = \"user@mail.com\"

📌 Common tools:

-   Regex

-   Length checks

-   \@NotBlank, \@Size, \@Pattern (Spring)

###  {#section-14 .unnumbered}

### **[Semantic Validation]{.underline}** {#semantic-validation .unnumbered}

**Checks if the data makes sense in the real world or business rules**.

It cares about **meaning**, not format.

Examples:

-   Age ≥ 18

-   Start date \< End date

-   Username is not already taken

-   User owns this resource

-   Parent collection exists in DB

❌ Invalid:

age = 5 (for adult signup)

📌 Usually requires:

-   Database queries

-   Business logic

-   External services

###  {#section-15 .unnumbered}

###  {#section-16 .unnumbered}

### **[Type Validation]{.underline}** {#type-validation .unnumbered}

**Checks that the data is of the correct type**.

Examples:

-   \"25\" → should be a number

-   \"true\" → boolean

-   \"2025-01-01\" → date

-   UUID string → UUID object

❌ Invalid:

{ \"age\": \"twenty\" }

📌 Often happens:

-   During deserialization (JSON → DTO)

-   Automatically by frameworks (Spring, Jackson)

## 

## [How They Work Together (Real Example)]{.underline}

Incoming request:

{

\"email\": \" SIMO@MAIL.COM \",

\"age\": \"20\"

}

### [Step 1: **Type Validation**]{.underline} {#step-1-type-validation .unnumbered}

-   \"age\" → convert string → integer

### [Step 2: **Syntactic Validation**]{.underline} {#step-2-syntactic-validation .unnumbered}

-   Email format valid?

-   Age is a number?

### [Step 3: **Semantic Validation**]{.underline} {#step-3-semantic-validation .unnumbered}

-   Age ≥ 18?

-   Email not already registered?

### [Step 4: **Transformation**]{.underline} {#step-4-transformation .unnumbered}

-   Trim email

-   Lowercase email

Final result:

{

\"email\": \"simo@mail.com\",

\"age\": 20

}

## 

## [One-Line Summary (easy to remember)]{.underline}

-   **Validation** → *Is the data correct?*

-   **Transformation** → *Put data in the right shape*

Validation types:

-   **Syntactic** → Format & structure

-   **Semantic** → Meaning & business rules

-   **Type** → Correct data type

**[Controllers , Services , repositories]{.underline}**

**[and Middlewares]{.underline}**

Basically these topics are the request's life cycle inside the server.

# [Controllers]{.underline}

### [What is a Controller?]{.underline} 

A **Controller** handles HTTP requests.

It's the entry point of your backend.\
It receives:

-   The request (GET, POST, PUT, DELETE)

-   The parameters or body

-   And returns a response

It does NOT contain business logic. It delegates that to services.

### [What is it responsible for?]{.underline}

-   Receiving requests

-   Validating input (sometimes)

-   sometimes serialization and transformation

-   Calling the service layer

-   Returning formatted responses (JSON, status codes)

[The controller:]{.underline}

-   Does not save to database

-   Does not hash passwords

-   Does not contain business rules

It delegates everything to the service.

# [Services]{.underline}

### [What is a Service?]{.underline}

A **Service** contains the business logic of your application.

This is where the real work happens.

### 

### [What is business logic?]{.underline}

Examples:

-   Hashing a password

-   Checking if email already exists

-   Calculating totals

-   Applying discounts

-   Validating rules

[Here the service:]{.underline}

-   Checks if email exists

-   Hashes password

-   Calls repository

-   Applies business rules

This is the brain of your application.

# [Repositories]{.underline}

### [What is a Repository?]{.underline}

A **Repository** handles database operations.

It is responsible for:

-   Saving

-   Deleting

-   Finding

-   Updating data

Nothing more.

The repository:

-   Talks directly to the database

-   Executes queries

-   Maps objects to tables

It does NOT:

-   Apply business logic

-   Handle HTTP

-   Do validations

# [Full Flow Example]{.underline}

Let's say someone sends:

POST /users

What happens?

1.  Controller receives request

2.  Controller calls Service

3.  Service applies business logic

4.  Service calls Repository

5.  Repository talks to database

6.  Service returns result

7.  Controller returns HTTP response

This separation is called **layered architecture**.

# [Middlewares]{.underline}

IN our structure where we have routing , controllers , services ,
repositories , middlewares could come in between these levels , for
example a middleware could come before a controller to intersept the
request and do some execution or some checks on it and then send it the
controller to process it and so on.

! it comes in the middle between layers.

Its like a handler (takes request , response object as parameter) but
with an additional parameter called next ( a function that passes the
execution from one middleware to the next context wether its a
middleware , controller , service ..).

**Why do we use middlewares ?**

The simple answer is that so we can write the logic in a function and
reuse it in different places , if we don't have middlewares we have to
reuse the same lines of code that we need on each layer of our
application wish is not convinient.

[Places where we use middlewares:]{.underline}

-   Authentication

-   Authorization

-   Logging and monitoring

-   CORS

-   Rate limiting

-   Request validation

-   Checking JWT tokens

-   Compresion

-   Data Parsing

-   Global error handling

# 

# **[Request Context]{.underline}**

The **request context** is all the data related to a single HTTP request
that flows through your application.

It lives only during that request.

**[It usually contains:]{.underline}**

-   The authenticated user

-   Request ID

-   Headers

-   Locale / language

-   Permissions

-   IP address

-   Correlation ID (for logging)

-   Database transaction (sometimes)

Think of it as a **container of request-scoped information**.

We need a request context to have a context of the request that will be
passed between our middleware , handlers and different layers of our
application.

# **[Why Do We Need It?]{.underline}**

**[Imagine this flow:]{.underline}**

1.  Request comes in

2.  Middleware verifies JWT

3.  Middleware extracts user ID

4.  Controller needs the authenticated user

5.  Service needs user role for authorization

6.  Logger needs request ID

Where do we store that shared data?

**[We don't want to:]{.underline}**

-   Pass 10 parameters everywhere

-   Re-parse the token in every layer

-   Use global variables (very bad idea)

👉 That's what request context solves.

# **[API Design (REST)]{.underline}**

Representational State transfer = REST.

**[Why is it called in this way ?]{.underline}**

\- **[Representational]{.underline}** = resources on the web are
represented on specific formats (json , xml , html ...)

\- **[State]{.underline}** = refers to the current condition or
attributes of a given resource , meaning that each resource has a state
that can be transferred between a server and a client.

\- Transfer = indicates the movement of resources between client and
server using a common http method.

**[What is Idempotency in REST APIs?]{.underline}**

An operation is idempotent if calling it multiple times has the same
effect as calling it once.

It doesn't mean the response is identical every time --- it means the
state of the server remains the same after the first successful request,
no matter how many times you repeat it.

**[Why Idempotency Matters ?]{.underline}**

Idempotency is very important for:

\- Network failures (client retries a request)

\- Mobile apps with unstable connections

\- Preventing duplicate operations (like duplicate payments)

\- Building reliable distributed systems

If a request is idempotent, the client can safely retry it.

**[Idempotency and HTTP Methods]{.underline}**

REST APIs are built on HTTP, and HTTP defines which methods should be
idempotent.

Method Idempotent? Why

GET ✅ Yes Only retrieves data

PUT ✅ Yes Replaces resource with same data

DELETE ✅ Yes Deleting multiple times = same result

POST ❌ No (by default) Usually creates new resource

PATCH ⚠️ Usually not Depends on implementation.

**[Important Distinction:]{.underline}**

Idempotent ≠ Safe

**Safe** = Does not modify server state (GET)

**Idempotent** = May modify state, but multiple identical requests have
same final effect (PUT, DELETE)

Idempotency ensures that repeating the same request does not change the
result beyond the first successful execution.

**[Some Best Practices:]{.underline}**

\- Document your APIs. (EX: Swagger api)

\- Make it intuitive and consistent.

\- Provide defaults in the server side.

\- Avoid abbreviations.

# **[Mastering Databases]{.underline}**

# **[What is a Database?]{.underline}**

A **database** is an organized collection of data.

Think of it like a super-powered digital notebook where data is stored
in a structured way so it can be easily:

-   Saved

-   Retrieved

-   Updated

-   Deleted

### [Example]{.underline}

If you\'re building your app with:

-   users

-   collections

-   resources

All this information is stored inside a **database**.

# [What is a DBMS?]{.underline}

A **DBMS (Database Management System)** is the software that manages the
database.

It is the program that allows you to:

-   Create databases

-   Create tables

-   Insert data

-   Query data

-   Update data

-   Delete data

-   Handle security

-   Handle performance

-   Prevent data corruption

### 

### [Examples of DBMS]{.underline}

-   MySQL

-   PostgreSQL

-   MongoDB

-   SQLite

When you connect Laravel to PostgreSQL, Laravel is talking to the
**DBMS**, not directly to the raw data files.

# [Simple Analogy]{.underline}

-   **Database** = The actual stored data (like files in a cabinet)

-   **DBMS** = The librarian who organizes, protects, and retrieves
    > those files

Without a DBMS, managing data safely would be very difficult.

# [Why Do We Use Databases?]{.underline}

We use databases because:

### 1 - To Store Data Permanently

Without a database, your data disappears when the app stops running.

### 2️ - To Organize Data

Instead of random JSON or txt files everywhere, databases structure data
into:

-   Tables

-   Rows

-   Columns

-   Relationships

Example:

-   One user has many collections

-   One collection has many resources

Databases handle these relationships properly.

### 

### 3 - To Query Data Efficiently

You can ask things like:

-   \"Give me all collections for user 5\"

-   \"Find resources created today\"

-   \"Count how many users signed up this month\"

This is done using **SQL** (Structured Query Language).

### 4 - To Handle Large Scale

Databases can handle:

-   Thousands

-   Millions

-   Even billions of records

Efficiently and safely.

### 5 - Security

DBMS systems allow:

-   User authentication

-   Permissions

-   Data encryption

-   Backup systems

### 

### 6 - Concurrency (Very Important)

If 1,000 users use your app at the same time:

-   The DBMS prevents data conflicts

-   Prevents corruption

-   Manages transactions safely

# [Difference between relational and non-relational Dbs]{.underline}

# [Relational Databases (SQL Databases)]{.underline}

A **relational database** stores data in **tables**.

Each table has:

-   Rows (records)

-   Columns (fields)

-   Relationships between tables

### [Example Structure]{.underline}

**Users Table**

  -----------------------------------------------------------------------
  id             name                          email
  -------------- ----------------------------- --------------------------

  -----------------------------------------------------------------------

**Collections Table**

  ------------------------------------------------------------------------
  id             user_id                       title
  -------------- ----------------------------- ---------------------------

  ------------------------------------------------------------------------

Here:

-   user_id connects collections to users.

-   This is called a **relationship** (Foreign Key).

### [Examples of Relational DBMS]{.underline}

-   PostgreSQL

-   MySQL

-   SQLite

-   Oracle Database

### [Characteristics of Relational Databases]{.underline}

-   Use **SQL** (Structured Query Language)

-   Strict schema (you must define structure first)

-   Strong relationships (foreign keys)

-   ACID transactions (very reliable)

-   Great for structured data

# 

# [Non-Relational Databases (NoSQL)]{.underline}

Non-relational databases do **not require tables or fixed schemas**.

They can store data as:

-   Documents (JSON-like)

-   Key-value pairs

-   Graphs

-   Wide-column structures

### [Example (Document Database)]{.underline}

Instead of separate tables, a user and their collections might be stored
like this:

{

\"name\": \"Simo\",

\"email\": \"simo@email.com\",

\"collections\": \[

{ \"title\": \"AI Resources\" },

{ \"title\": \"Laravel Tutorials\" }

\]

}

Everything can be inside one document.

### [Examples of Non-Relational DBMS]{.underline}

-   MongoDB

-   Redis

-   Cassandra

-   Neo4j

# [Main Differences]{.underline}

  ----------------------------------------------------------------------------
  Feature         Relational (SQL)              Non-Relational (NoSQL)
  --------------- ----------------------------- ------------------------------
  Structure       Tables                        Documents / Key-Value / Graph

  Schema          Fixed (strict)                Flexible

  Relationships   Built-in (Foreign Keys)       Usually manual

  Scaling         Vertical scaling              Easier horizontal scaling

  Best For        Structured data, banking,     Big data, real-time apps,
                  ERP, SaaS apps                flexible structures
  ----------------------------------------------------------------------------

**Database migrations** are a way to **manage and version-control
changes to your database structure (schema)** using code.

Instead of manually changing the database (for example using SQL in a
database GUI), you write **migration files** that describe the changes.
These files can then be executed to update the database automatically.

## [1. What a Migration Is]{.underline}

A **migration** is basically a script that describes how to modify the
database schema.

Examples of changes migrations handle:

-   Creating tables

-   Adding columns

-   Removing columns

-   Creating indexes

-   Creating foreign keys

-   Renaming tables

[Example migration (conceptually):]{.underline}

CREATE TABLE users (

id BIGINT PRIMARY KEY,

name VARCHAR(255),

email VARCHAR(255),

created_at TIMESTAMP

);

[In frameworks like **Laravel**, the same thing is written as
code:]{.underline}

Schema::create(\'users\', function (Blueprint \$table) {

\$table-\>id();

\$table-\>string(\'name\');

\$table-\>string(\'email\');

\$table-\>timestamps();

});

# 

# [2. Why Developers Use Migrations]{.underline}

## [Version Control for the Database]{.underline}

Your database structure becomes part of your **Git repository**.

[Example:]{.underline}

database/migrations/

2026_03_01_create_users_table.php

2026_03_02_add_avatar_to_users.php

[Anyone cloning the project can run:]{.underline}

php artisan migrate

and get the **exact same database structure**.

## [Easy Collaboration]{.underline}

Without migrations:

Developer A manually adds a column.

Developer B pulls the project and the code breaks because their database
**doesn\'t have that column**.

With migrations:

Developer B runs:

php artisan migrate

and the database updates automatically.

## [Database Evolution Over Time]{.underline}

Apps constantly change.

Example timeline:

**v1**

users

\- id

\- name

\- email

**v2**

users

\- id

\- name

\- email

\- avatar

**v3**

users

\- id

\- name

\- email

\- avatar

\- bio

Migrations track these steps.

## [Rollbacks (Undo Changes)]{.underline}

Good migration systems allow **rolling back** changes.

Example in **Laravel**:

php artisan migrate

php artisan migrate:rollback

Rollback might remove a column you just added.

Example migration structure:

public function up()

{

Schema::table(\'users\', function (Blueprint \$table) {

\$table-\>string(\'avatar\');

});

}

public function down()

{

Schema::table(\'users\', function (Blueprint \$table) {

\$table-\>dropColumn(\'avatar\');

});

}

-   **up()** → apply change

-   **down()** → undo change

## [Environment Consistency]{.underline}

You may have different environments:

-   local development

-   staging

-   production

Migrations ensure all environments have the **same schema**.

# [3. Migrations vs Manually Editing the Database]{.underline}

### [Manual DB editing]{.underline}

Example:

Open **phpMyAdmin** → add column manually.

Problems:

-   not reproducible

-   teammates don\'t know what changed

-   hard to track history

### [Using migrations]{.underline}

Everything is:

-   tracked in **Git**

-   automated

-   reproducible

-   reversible

[**Database triggers**]{.underline}

are pieces of code that automatically run when a specific event happens
in a database table.

Think of them like **automatic reactions** inside the database.

Example idea:

-   If a new user is inserted into the users table

-   The database **automatically runs some logic**

You **don't call a trigger manually**. The database runs it
**automatically** when something happens.

# [1. When do triggers run?]{.underline}

Triggers run when certain database events happen:

### Common events

-   **INSERT** → when a new row is added

-   **UPDATE** → when a row is modified

-   **DELETE** → when a row is removed

Example:

INSERT INTO users (name, email)

VALUES (\'Ali\', \'ali@email.com\');

This could automatically trigger some code.

# [2. Simple example]{.underline}

Imagine you have two tables:

users

\-\-\-\--

id

name

email

user_logs

\-\-\-\-\-\-\-\--

id

user_id

action

created_at

You want to **log every time a user is created**.

Instead of doing this in backend code, you create a **trigger**.

Example concept:

AFTER INSERT ON users

INSERT INTO user_logs (user_id, action)

VALUES (NEW.id, \'USER_CREATED\');

Now every time a user is inserted:

users table → new row

trigger runs → log inserted

Automatically.

# [3. BEFORE vs AFTER triggers]{.underline}

### BEFORE trigger

Runs **before** the data is saved.

Example uses:

-   validate data

-   modify data

Example:

BEFORE INSERT

You could automatically lowercase emails.

### AFTER trigger

Runs **after** the data is saved.

Example uses:

-   logging

-   analytics

-   notifications

Example:

AFTER INSERT

# [4. Real uses in backend systems]{.underline}

Triggers are used for things like:

### [1️ - Logging / auditing]{.underline}

Track changes to data.

Example:

user updated email

→ save change in audit table

### 

### [2️ - Automatic timestamps]{.underline}

Example:

updated_at automatically updated

### 

### [3️ - Data consistency]{.underline}

Example:

delete order

→ automatically delete order_items

(This is often done with **foreign key cascades**, though.)

### [4️ - Analytics / counters]{.underline}

Example:

new post created

→ increase user_posts_count

# [5. Why many backend developers avoid triggers]{.underline}

In modern backend systems (Laravel, Spring Boot, Node, etc.), triggers
are **often avoided** because:

### [Hidden logic]{.underline}

Logic exists in the database instead of backend code.

Example problem:

UserService.createUser()

You think it only inserts a user, but the DB trigger also:

-   inserts logs

-   modifies data

-   creates analytics

Harder to debug.

### [Harder to maintain]{.underline}

Code is split between:

-   backend code

-   database triggers

### [Harder to version control]{.underline}

Backend code uses **Git**, but triggers live in the DB unless managed
via **migrations**.

# [6. Modern alternative]{.underline}

Instead of triggers, backend systems usually use:

### Application logic

Example in **Laravel**:

User::created(function (\$user) {

Log::create(\[

\'user_id\' =\> \$user-\>id,

\'action\' =\> \'USER_CREATED\'

\]);

});

Or inside services.

# 

# [7. When triggers are still useful]{.underline}

Triggers are still great for:

-   **audit logs**

-   **database-level security**

-   **guaranteeing integrity**

-   **legacy systems**

-   **data warehouses**

**[Database Indexes]{.underline}**

A database index is a data structure that makes searching rows in a
table much faster.

Think of it like the **index at the back of a book** .

Instead of scanning the whole book to find a topic, you look at the
index and jump directly to the right page.

Databases do the same thing.

# [1. The problem indexes solve]{.underline}

Imagine a table:

users

\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--

id \| name \| email

And it contains **1 million users**.

If you run a query:

SELECT \* FROM users WHERE email = <'simo@email.com>\';

Without an index, the database must:

check row 1

check row 2

check row 3

\...

check row 1,000,000

This is called a **full table scan**.

Very slow for big datasets.

# [2. What an index does]{.underline}

When you add an index:

CREATE INDEX idx_users_email ON users(email);

The database creates a **sorted structure** (usually a **B-tree**, a
type of tree data structure).

Now the search becomes something like:

look in index

jump directly to the row

Instead of scanning everything.

This makes queries **much faster**.

# [3. Visual example]{.underline}

Table:

users

\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--

id \| email

1 \| a@mail.com

2 \| b@mail.com

3 \| c@mail.com

Index:

email index

\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--

a@mail.com -\> row 1

b@mail.com -\> row 2

c@mail.com -\> row 3

Now the database can jump directly to the row.

# [4. Common columns to index]{.underline}

In backend systems, indexes are typically added on:

### Primary keys

Example:

users.id

Usually indexed automatically.

### Foreign keys

Example:

posts.user_id

orders.customer_id

These are used frequently in **joins**.

Example:

SELECT \*

FROM posts

JOIN users ON posts.user_id = users.id;

### 

### Frequently searched columns

Example:

email

username

slug

Example query:

SELECT \* FROM users WHERE email = ?

### 

### Sorting columns

Example:

SELECT \* FROM posts ORDER BY created_at DESC;

Index:

posts.created_at

# [5. Example in backend systems]{.underline}

Imagine a **login system**.

Query:

SELECT \* FROM users WHERE email = ?;

Without index:

slow login for large systems

With index:

instant lookup

Most production apps index:

users.email

users.username

# 

# [6. Indexes in ORMs / migrations]{.underline}

In frameworks like **Laravel**, you define indexes in migrations.

Example:

\$table→string(\'email\')→unique();

This creates a **unique index**.

Or:

\$table→index(\'user_id\');

# [7. Types of indexes]{.underline}

### Primary index

Created automatically:

PRIMARY KEY (id)

### 

### Unique index

Prevents duplicates.

Example:

UNIQUE(email)

### 

### Composite index

Index on multiple columns.

Example:

CREATE INDEX idx_user_posts

ON posts(user_id, created_at);

Used for queries like:

SELECT \* FROM posts

WHERE user_id = 5

ORDER BY created_at;

# 

# [8. Downsides of indexes]{.underline}

Indexes are powerful but not free.

### More storage

Indexes take extra disk space.

### Slower writes

Every time you:

INSERT

UPDATE

DELETE

The index must also update.

Example:

insert user

update email index

update username index

# [9. Real rule backend engineers follow]{.underline}

Good rule:

Index columns that you:

\- search

\- filter

\- join

\- sort

Avoid indexing columns that:

\- rarely used

\- change frequently

# [10. Real production example]{.underline}

A **posts table** in a social app might have:

posts

\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--

id (PK index)

user_id (index)

created_at (index)

Queries like:

get posts by user

sort posts by time

will be very fast.

# **[Caching : the secret behind it all]{.underline}**

![](media/image14.png){width="6.4631944444444445in"
height="3.134027777777778in"}

# **[1. What is Caching]{.underline}**

**Caching** is the process of **storing frequently accessed data in a
faster storage location** so it can be retrieved quickly without
recomputing or refetching it.

Instead of repeatedly requesting data from a **slow source** (database,
server, disk), the system first checks a **cache**, which is a temporary
high-speed storage.

### [Example]{.underline}

When visiting a website:

-   First visit → data comes from the server

-   Next visits → images, scripts, or data may load from **cache**

This reduces loading time and server work.

# [2. Importance of Caching]{.underline}

Caching is critical for system performance.

### 1. Faster Response Time

Data from cache is **much faster** than fetching from the original
source.

Example:

-   Database query → 50 ms

-   Cache lookup → 1 ms

### 2. Reduced Server Load

Many users requesting the same data can be served from cache instead of
hitting the database.

### 3. Improved Scalability

Systems can support **more users** without increasing infrastructure.

### 4. Reduced Network Traffic

Less communication between services or servers.

### 5. Better User Experience

Pages load faster and applications feel smoother.

# [3. Levels of Caching]{.underline}

Caching happens at **multiple layers in computer systems**:

1.  Network level

2.  Hardware level

3.  Software level

# [4. Network Caching]{.underline}

Network caching stores data closer to users in the **network
infrastructure**.

## 

## 

## [CDN (Content Delivery Network)]{.underline}

![](media/image15.png){width="6.6930555555555555in"
height="3.732638888888889in"}

A **CDN** is a network of servers distributed around the world that
store cached versions of web content.

Examples:

-   HTML pages

-   images

-   videos

-   CSS

-   JavaScript

### How CDN works

1.  User requests a website

2.  Request goes to the **nearest CDN server**

3.  If the file is cached → served instantly

4.  If not → fetched from origin server and cached

### Benefits

-   Faster loading

-   Lower latency

-   Reduced load on the origin server

Example providers:

-   Cloudflare

-   Akamai

-   AWS CloudFront

## [DNS Caching (Domain Name System)]{.underline}

DNS converts a **domain name → IP address**.

Example:

google.com → 142.250.190.78

Without caching, every request would query DNS servers.

### DNS caching stores this mapping temporarily.

Locations where DNS caching occurs:

1.  Browser

2.  Operating system

3.  ISP DNS server

4.  Recursive DNS server

### [Example]{.underline}

First request:

google.com → DNS lookup → IP returned

Next requests:

google.com → IP found in DNS cache

Result → faster connection.

# [5. Hardware Level Caching]{.underline}

![](media/image16.png){width="4.133333333333334in"
height="3.9618055555555554in"}

Hardware caching improves **CPU and memory performance**.

The memory hierarchy from fastest to slowest:

CPU Registers

L1 Cache

L2 Cache

L3 Cache

RAM

Hard Disk / SSD

## L1 Cache

-   Smallest

-   Fastest

-   Located inside CPU core

Typical size:

32KB -- 128KB

Used for **most frequently used instructions and data**.

## L2 Cache

-   Larger than L1

-   Slightly slower

Typical size:

256KB -- 1MB

Acts as backup when data is not found in L1.

## L3 Cache

-   Shared between CPU cores

-   Larger but slower

Typical size:

4MB -- 64MB

Stores data used by multiple cores.

## RAM

Random Access Memory is **main memory** used by programs.

Much slower than CPU cache but faster than disk.

## Hard Disk / SSD

Permanent storage.

Slowest level but largest.

# [6. Software-Based Caching]{.underline}

![](media/image17.png){width="6.6930555555555555in"
height="3.7645833333333334in"}

Software caching stores data in **high-speed memory systems**.

Often used by applications or databases.

Most common tools:

-   Redis

-   Memcached

## [In-Memory Key-Value Stores]{.underline}

These systems store data in the form:

key → value

Example:

\"user:123\" → {name: \"Simo\", age: 21}

Since everything is stored **in memory (RAM)**, retrieval is extremely
fast.

Typical uses:

-   Session storage

-   API response caching

-   database query caching

-   leaderboard systems

-   rate limiting

## Redis

Features:

-   in-memory database

-   persistence support

-   data structures (lists, sets, hashes)

-   pub/sub messaging

Common in **large-scale applications**.

## Memcached

Simpler than Redis.

Features:

-   pure key-value store

-   extremely fast

-   used mainly for caching database queries.

# [7. Caching Strategies]{.underline}

Strategies determine **how data is written and read from cache**.

Two common ones:

1.  Lazy caching (Cache Aside)

2.  Write Through

## 

## 

## [Lazy Caching (Cache Aside)]{.underline}

This is the **most commonly used strategy**.

### Process

1.  Application checks cache

2.  If data exists → return it

3.  If not → fetch from database

4.  Store result in cache

5.  Return result

### Advantages

-   Cache only stores data that is actually used

-   Saves memory

### Disadvantage

First request is slow.

## [Write Through]{.underline}

In this strategy, data is **written to both cache and database at the
same time**.

### Process

Write → Cache

→ Database

### Advantages

-   Cache always has fresh data

-   No cache miss for recent writes

### Disadvantages

-   Slower writes

-   More resource usage

# 

# [8. Eviction Policies]{.underline}

Cache storage is limited, so old items must sometimes be removed.

Eviction policies decide **which data to remove**.

## [No Eviction]{.underline}

Cache never removes items automatically.

If full:

-   new data cannot be stored

Rarely used.

## 

## [LRU (Least Recently Used)]{.underline}

Removes the item **that hasn\'t been used for the longest time**.

Example:

Access order:

A B C D

If cache full and new item E comes:

Remove A

Used in many systems like Redis.

## [LFU (Least Frequently Used)]{.underline}

Removes the item used **the fewest number of times**.

Example:

A accessed 20 times

B accessed 5 times

C accessed 1 time

When full:

Remove C

Good for long-term popularity patterns.

## 

## 

## [TTL (Time To Live)]{.underline}

Each cached item has an **expiration time**.

Example:

Cache user data for 10 minutes

After 10 minutes:

Item automatically removed

Useful for:

-   API responses

-   session data

-   temporary information

# **[Task queues and Background jobs]{.underline}**

Task queues and background jobs are a **core backend engineering
concept**. They help you move heavy or slow operations **outside the
main request-response cycle** so your app stays fast.

# [1. Introduction to Background Jobs / Tasks]{.underline}

A **background job (or task)** is a piece of work executed **outside the
main application flow**.

Instead of running during a user request, it runs **later in the
background**.

### Example

User signs up:

1.  Save user in DB

2.  Send welcome email

Without background jobs:

User request

\|

Save user

\|

Send email (slow)

\|

Response to user

With background jobs:

User request

\|

Save user

\|

Add \"send email\" task to queue

\|

Response immediately

The email is processed **later by a worker**.

# 

# [2. Why Background Jobs Are Needed (Email Example)]{.underline}

Sending email can take:

-   network latency

-   SMTP delays

-   failures/retries

If you send it during the request:

User waits 2--5 seconds

That makes your API **slow**.

Instead:

POST /register

\|

Save user

\|

Queue email task

\|

Return response instantly

Worker handles:

Send email

This improves:

-   performance

-   user experience

-   scalability

# 

# 

# [3. How Background Jobs Work (Async Workflow)]{.underline}

Typical architecture:

Application Server

\|

\| 1. Add task

v

Task Queue (Redis, RabbitMQ, SQS)

\|

\| 2. Worker pulls task

v

Worker

\|

\| 3. Execute job

### Step-by-step

1️⃣ User makes request\
2️⃣ App pushes job to queue\
3️⃣ Worker reads job\
4️⃣ Worker executes it

Example:

send_welcome_email(user_id)

# [4. Handling Task Failures and Retries]{.underline}

Tasks **can fail** because of:

-   network errors

-   API failures

-   database issues

Example:

send_email -\> SMTP server down

Task queues usually support **automatic retries**.

Example retry strategy:

Retry 1 → after 10 seconds

Retry 2 → after 30 seconds

Retry 3 → after 2 minutes

If it keeps failing → move to **dead letter queue**.

# [5. Advantages of Background Tasks]{.underline}

### [Faster APIs]{.underline}

User doesn\'t wait for slow tasks.

### [Better scalability]{.underline}

Workers can scale independently.

Example:

10 API servers

50 workers

### [Fault tolerance]{.underline}

Tasks can retry automatically.

### [Load smoothing]{.underline}

Queues handle spikes in traffic.

# [6. Common Use Cases]{.underline}

### Sending Emails

send_email(user_id)

Example:

-   password reset

-   order confirmation

-   newsletters

### Processing Images or Videos

Example after upload:

generate_thumbnail

compress_image

transcode_video

These are **CPU-heavy tasks**.

### 

### Generating Reports

Example:

generate_monthly_sales_report

Could take:

10--60 seconds

Better as a background job.

### Sending Push Notifications

Example:

send_push_notification(user_ids)

May involve **thousands of devices**.

# [7. What is a Task Queue]{.underline}

A **task queue** is a system that stores tasks until workers execute
them.

Architecture:

Producer → Queue → Worker

### Producer

Your app that **creates tasks**.

Example:

queue.add(send_email)

### Queue

Stores tasks temporarily.

Examples:

-   Redis

-   RabbitMQ

-   Amazon SQS

### Worker

Program that processes tasks.

# [8. Technical Deep Dive into Task Queues]{.underline}

A queue usually stores tasks like this:

Task:

{

id: 123

type: send_email

payload: { user_id: 5 }

}

Workers:

while true:

task = queue.get()

execute(task)

Important features:

-   acknowledgement

-   retries

-   visibility timeout

![](media/image18.png){width="7.059722222222222in"
height="4.6715277777777775in"}

# ![](media/image19.png){width="7.121527777777778in" height="3.6104166666666666in"}

# [9. Visibility Timeout]{.underline}

Very important concept.

When a worker **picks a task**, the queue hides it temporarily.

Example:

Worker A picks task

Queue marks task as **invisible** for:

visibility_timeout = 30 seconds

If the worker **crashes**, after 30 seconds:

Task becomes visible again

Another worker can retry it.

This prevents **task loss**.

# 

# [10. Types of tasks]{.underline}

# One-off Tasks

Tasks executed **only once**.

Example:

send_welcome_email

generate_report

resize_image

Typical queue job.

# Recurring Tasks

Tasks that run **on a schedule**.

Example:

every day → send analytics report

every hour → cleanup expired sessions

every minute → sync external API

Tools for this:

-   Celery Beat

-   Cron

-   BullMQ scheduler

# Chain Tasks

Chain tasks execute **in sequence**.

Example:

Task 1 → Task 2 → Task 3

Example workflow:

process_video

↓

generate_thumbnail

↓

send_notification

Each task starts after the previous finishes.

# 

# Batch Tasks

Batch = **many tasks grouped together**.

Example:

Send email to 100,000 users

Instead of one huge job:

1000 tasks

each sends 100 emails

Benefits:

-   parallel execution

-   faster processing

-   failure isolation

# [11. Idempotency]{.underline}

**Critical concept in distributed systems.**

A task should be **safe to run multiple times**.

Example:

Bad:

charge_credit_card()

If retried → customer charged twice.

Good:

charge_credit_card(order_id)

System checks:

if order already charged → skip

This ensures **no duplicate side effects**.

# [12. Error Handling]{.underline}

Good task systems handle:

### Transient errors

Retry automatically.

Example:

network timeout

temporary API error

### Permanent errors

Stop retrying.

Example:

invalid email address

These tasks may move to:

Dead Letter Queue (DLQ)

# [13. Monitoring]{.underline}

You must monitor:

-   task failures

-   queue size

-   worker health

-   processing time

Tools:

-   Celery Flower

-   BullMQ dashboard

-   Prometheus + Grafana

Monitoring helps detect:

queue backlog

worker crashes

high failure rates

# [14. Scalability]{.underline}

Task queues scale horizontally.

Example:

Queue receives 10,000 tasks

Instead of:

1 worker

You run:

50 workers

Processing happens **in parallel**.

This is why task queues are used by **large systems**.

# [15. Ordering]{.underline}

Some queues guarantee **task order**.

Example:

Task A

Task B

Task C

But with many workers:

Worker1 → Task A

Worker2 → Task B

Worker3 → Task C

Order may break.

Sometimes ordering matters (e.g., financial operations).

Solutions:

-   FIFO queues

-   partitioned queues

# [16. Rate Limiting]{.underline}

Prevents tasks from executing **too fast**.

Example:

External API allows:

100 requests / minute

Queue system enforces:

rate_limit = 100/min

Without this you could:

get API banned

# [17. Best Practice]{.underline}

\- keep tasks small and focused.

\- Avoid long running tasks.

\- Use proper error handling and logging.

\- Monitor queue length and worker health.

# 

**[Blazingly fast search with Elastic search]{.underline}**

**[What is Elasticsearch?]{.underline}**

At its core, Elasticsearch is a **distributed, RESTful search and
analytics engine** built on top of Apache Lucene. It stores data in a
JSON document format, and you can interact with it via a simple REST API
(using HTTP requests). It\'s designed to handle massive amounts of data,
scale horizontally across many servers, and provide near real-time
search capabilities.

Think of it as a highly specialized database that\'s optimized
for **search** rather than just simple lookups. It\'s the \"E\" in the
popular **ELK Stack** (now called Elastic Stack), where it often teams
up with Logstash (for data ingestion) and Kibana (for visualization).

## **[Why do we use Elasticsearch?]{.underline}**

Here are the main reasons developers and organizations choose
Elasticsearch:

-   **Blazing-fast full-text search** -- It\'s not just about exact
    matches; it understands language, handles typos, ranks results by
    relevance, and searches across many fields. That\'s thanks to
    Lucene\'s inverted index.

-   **Scalability** -- You can start with a single node and grow to
    hundreds by adding more machines (horizontal scaling). Elasticsearch
    automatically splits your data into shards and distributes them
    across the cluster.

-   **Near real-time** -- Data is searchable within about one second of
    being indexed, making it great for time-sensitive applications.

-   **Rich analytics** -- Beyond search, you can run complex
    aggregations to compute statistics, build histograms, or find trends
    in your data.

-   **Schema‑flexible** -- You can index JSON documents without
    predefining a rigid schema. Elasticsearch will try to detect field
    types, but you can also define explicit mappings for more control.

-   **RESTful API** -- You communicate with it over HTTP using simple
    JSON commands, so it\'s easy to use from any programming language.

-   **High availability** -- Data is automatically replicated across
    nodes, so if a server fails, your data is still safe and searchable.

## **[When should you use Elasticsearch?]{.underline}**

Elasticsearch is a perfect fit for many modern use cases. Here are some
of the most common:

### **[1. Search‑driven applications]{.underline}**

-   **E‑commerce sites** -- Product search with filters, faceting (e.g.,
    by category, price range), and \"did you mean\" suggestions.

-   **Document management** -- Searching through PDFs, emails, or
    internal wikis.

-   **Media libraries** -- Finding images, videos, or articles by tags,
    descriptions, or content.

### **[2. Logging and log analysis]{.underline}**

Collect, parse, and search logs from servers, applications, or network
devices. This is the classic ELK use case: index logs, search for
errors, create dashboards in Kibana.

### **[3. Application performance monitoring (APM) and observability]{.underline}**

-   Store and analyze metrics, traces, and events to monitor system
    health, detect anomalies, and debug performance issues.

### **[4. Security analytics]{.underline}**

-   Ingest security events (like firewall logs or authentication
    attempts) and search for suspicious patterns or threats in real
    time.

### **[5. Geospatial search]{.underline}**

-   Combine location data with search queries -- for example, finding
    all restaurants within a 5‑mile radius that are currently open and
    have a 4‑star rating.

### **[6. Auto‑complete and instant search]{.underline}**

Power search‑as‑you‑type features, with suggestions and corrections,
thanks to its support for edge‑n‑grams, suggesters, and completion
suggester.

### **[7. Business intelligence and analytics]{.underline}**

Run aggregations on large datasets to generate reports, sales
dashboards, or user behaviour analytics.

## 

## **[When should you avoid Elasticsearch?]{.underline}**

Elasticsearch is not a one‑size‑fits-all solution. You might want to
look elsewhere if:

-   You need strict **ACID transactions** or complex joins across
    multiple entities -- a relational database like PostgreSQL is better
    suited.

-   Your data is highly relational and requires frequent updates to many
    small rows.

-   You need a primary data store for mission‑critical transactional
    data -- it\'s safer to use a dedicated database and replicate a copy
    to Elasticsearch for search.

## **[A quick example]{.underline}**

Imagine you run an online bookstore. With Elasticsearch, you could:

-   Index each book\'s title, author, description, price, and
    publication date.

-   Let customers search for \"mystery novels by Agatha Christie\" and
    get relevant results in milliseconds.

-   Add filters for price, publication year, or rating.

-   Show suggestions as they type: \"agatha\" → \"Agatha Christie\",
    \"mystery\" → \"Mystery, Thriller\".

-   Generate a dashboard showing the most popular authors in the last
    month.

All of this is possible because Elasticsearch is built to handle search
and analytics at scale.
