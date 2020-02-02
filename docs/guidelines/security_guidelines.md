# Guidelines for Security in Applications

## Introduction
This is a security consideration in an application.

## Security Model

Define your product security model:

- Security area
They are logical area, we will mark users and places with one of these area.

  - Trust Area
  The area where data can not be accessed by an unauthorized user.

  - Public Area
  The area where data would be accessed by an unauthorized user.

- Users

Users who would access your data;

- Places

Places where your data would be stored
Places where your data would be transmitted
Places where your data would be cached

Mark each place with an area.

For example:
Place | Area
----- | -----
Database | Trust Area
Internet | Public area
Log files | Public area
Cookies | Public area

## Development Guidelines

- Support security protocols, e.g. https, sftp etc.

- Protect passwords
Passwords must be encrypted.
Do not allow passwords in clear text format be written in any files.
Do not allow passwords be transmitted to clients ( or via Internet).
Do not allow passwords be cached.

- Encryption and Hash methods
We have to use the encryption and hash methods matched criteria (or with highest intensity).
E.g. MD5 is not allowed, instead we should use SHA with highest intensity.

List all encryption methods and hash methods in the release management document.

- Credential Information : do not leak credential information in public.

- Prevent SQL injection

- Prevent Script Attack

- Do not trust client requests
Always check permissions, always validate data.
Avoid malicious users use elaborately edited URL or post/put data to access protected data.
