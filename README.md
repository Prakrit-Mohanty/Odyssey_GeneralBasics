# Odyssey_GeneralBasics

# SOLID Principles

Code can become messy and hard to maintain when we add new features, many people are working on it, new implementations are needed etc.

SOLID principles are a collection of 5 principles used to create and maintain easy to implement, easy to extend, simple and consistent code.

## Single Responsibility Principle (SRP)

It says that each class should only have one responsible or should be responsible for only thing. Other responsibilities should be given to other classes.

## Open/Closed Principle (OCP)

We should be able to add features to classes without breaking of pre-existing code. Goal is to not disturb or change code in order to add new things, if we have to change pre-existing code it will become tedious to add new features.

## Liskov Substitution Principle (LSP)

States that the child class should be able to be replaceable with the parent class. When functions are called for the child class, these functions should not throw exceptions at the parent class functions.

## Interface Segregation Principle (ISP)

Larger interfaces should be split into smaller interfaces. This way we can ensure no class is implementing methods it does not need or rely on.

## Dependency Inversion Principle (DIP)

Larger modules should not depend on smaller modules. Lets say we have UPI connected to payment class, and we want to change it to razorpay, we should’t have to change the entire class in order to add or replace a payment method.

---

# Microservices & its Purpose

In Mircroservices all the processes are not tightly coupled into one huge system ran as a single service, rather they are all treated as their own service. In monolith everything is combined into one system making it harder to add extra features as the codebase grows, makes It difficult to point out errors.

Larger systems are broken down into smaller systems to make it easier to scale, deploy, correct for errors, etc. These services in Microservices communicate with each other through fast and light API’s.

When it comes to scaling in monolith, if one certain feature needs to be scaled due to more concentrated traffic, the entire single service will have to be scaled along with it. In micro services we can scale each feature on its own whenever they need to be scaled.

This is the same for deployment, as micro services enable CI/CD, making it easy to try new ideas and roll back if something doesn’t work. There is no one size fits all approach, we can use different tech stacks and tools to solve problems in each service.

Since all services are independent of each other, they have the freedom to work and exist on their own. Each service can also get its own personalised team making It easier for them to understand their context and their domain to be able to fix their problem as soon as possible.

---

# Database Normalization

The process of organising and standardising data to eliminate redundancy, prevent errors and improve performance.

**Redundancy = duplicate data; this can cause messy tables and issues with adding and deleting data.**

## 1NF

Each row cannot have multiple types of information.

- Each column should have only one type of data.
- Storing related types of data in multiple columns is not allowed.

## 2NF

All candidate keys should not partially depend on the primary key, but should fully depend on it.

## 3NF

Transitive dependencies are not allowed, non key columns cannot depend on other non key columns, they must depend on the primary keys.

---

# Database Pooling

A database connection allows the software applications to connect with the database. It is not resource efficient or smart to let connections be made as soon as you want to send a request and let it terminate every time that request ends. Database pooling allows us to reuse these connections which in turn reduces overhead, use of resources and makes connections with the database more efficient.

When it comes to database pooling, the connection isn’t made with the database directly but made with the connection pooler instead, the pooler acts as the database for the client. PGBouncer is a well known lightweight connection pooler user for Postgre SQL. Putting the pooler in the client software allows for the connection between the two to use lighter weight mechanism than TCP, which in turn reduces latency.

There are three types of connection pooling:

- Transaction
- Session
- Statement

---

# CORS

Cross origin recourse sharing is a browser security mechanism that controls whether a web page running on an origin is allowed to make requests to a server on a different origin.

Browsers usually follow same origin policy by default. This exists because your browser automatically send cookies and session credentials with requests. This can be harmful if a malicious website fires requests to your bank or email provider.

Without proper CORS config, a frontend hosted on another origin will have its requests blocked by the browser, you will get a message saying something like:

> "no access-control-allow-origin"

Preflight requests and requests made before the actual requests to see if Cors is allowed or not. Basically to see if the custom requests will be allowed or not.

`Access-Control-Allow-Origin` tells the browser which origin(s) are allowed to read the response.

---

# API (Application Programming Interface)

Mechanisms that enable two software components to communicate with each other.

API architecture is explained in terms of client and server.

- The application sending the request is called the **client**.
- The application sending the response is called the **server**.

## Request Response Lifecycle

- Client initiation and transmission
  - Request construction
  - DNS resolution
  - Network transport
- Perimeter & gateway security
- Server middleware & processing
- Business logic and data fetching
- Response formulation & delivery

## HTTP

HTTP is a set of rules to transfer data through the web. It has a request response format.

### Methods

- GET
- POST
- PUT
- PATCH
- DELETE
- QUERY

Header gives us the metadata while body is the actual data.

### Status Codes

- **1xx** - informational
- **2xx** - success
- **3xx** - redirection
- **4xx** - client error
- **5xx** - server error

---

# Linting

Automated checking of your source code for programmatic and stylistic errors. It is done by a lint tool called "Linter". Linting is used to reduce errors and make code quality better.

## Black

Black is not a linter, rather it is a code rewriter. It does not care about errors or complications in code, it just cares about how your code looks.

## Flake8

Flake 8 is a linter. It checks for style violations and actual issues and complications with your code.

## Ruff

Ruff is newer and it is a mix of Black & flake 8 practically. It resolves all your issues and complications + some other features as well as also having its own formatter. It is 10-100x faster.

---

# Parameterised Queries

Ensuring security and reliability of your database queries is very important. Parameterised queries provide an effective solution by separating data from query logic which helps in preventing SQL injection attacks.

Instead of embedding user input or variable directly into the query, we use parameters that will be filled during run time.

In PostgreSQL parameterised queries are made using the `PREPARE` statement and executed using the `EXECUTE` statement.

## SQL Injection

SQL injection happens when the user input gets inserted directly intro the SQL query as raw text, allowing an attacker to change the query structure.

String concatenation is the root cause; the query text and the data are meant to be two separate things, one is code and one is value - but concatenation merges them into a single string.

It has no way to know which quote marks were supposed to be there and which ones are injected.

Parameterised queries are the fix to this, as they clearly split the code and the value.

---

# VENV

Running with system python and libraries limits you to one specific python version. Trying to run all your python applications makes it very likely that version conflicts may take place between your python libraries. It’s also possible that changes to your system python may break other OS features depending on it.

Virtual environments are lightweight, self-contained python instalments, designed to be set up to be minimal, minimum of fuss and just "to work" without requiring extensive configurations or specialised knowledge.

Venv avoids the need to download python packages globally.

When Venv is active, pip will install all the libraries in the environment itself which will not affect the base python installation in any way.

---

# Error Handling & Logging

Error handling and logging are essential aspects of software development, ensuring that applications run smoothly and that any issues are quickly identified and resolved.

Python error handling occurs mainly in 3 steps those being:

- try
- except
- finally

The code you want to check for the error / might have an error goes in try, if the error does exist the except block does execute. The finally block executes no matter what.

## Logging

Logging is the process of keeping record of what a program is doing while it runs, it helps the developers to understand the behaviour of the program and to easily find and fix errors.

The different python logging levels are:

- debug
- info
- warning
- error
- critical

---

# How Library/Model Imports Work in the Code

The import statement finds the module, runs the code once and binds the result to the name.

For example:

```python
import numpy as np
```

It binds the whole module object to `np`. We can access things like:

```python
np.array()
```

If we import `array` directly from numpy, for ex:

```python
from numpy import array
```

We can directly use the `array()` command.

`from` doesn’t avoid loading the whole module, it still runs all of numpy’s code, it just changes what name gets bound to.

---

# Project Folder Structure Best Practices

Src-layout over flat layout. Putting packages under src rather than top level forces you to actually install the package to run it which can help catch import bugs early than flat layout.

We use:

- `core` for domain logic
- `services` for anything that touches the outside world like API’s, DB’s, etc
- `models` for data shapes
- `utils` for generic helpers with no business logic

Configs and secrets stay out of code, we can use `config.py` to load environment variables.

We should never hardcode credentials.

## Example Structure

```text
my_project/
│
├── README.md
├── .gitignore
├── .env
├── requirements.txt
├── src/
├── tests/
├── docs/
├── scripts/
└── notebooks/
```
