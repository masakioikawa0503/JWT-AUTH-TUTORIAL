## What is this repository?

This section describes what we have confirmed through actual hands-on verification of the JWT mechanism.

## What is JWT(Json Web Token)?

- サイト（サービス）にアクセスするための **許可証** みたいなもの。
- Cookie やセッションの考え方に近い

### Reference URL

- [RFC 7519: JSON Web Token (JWT)](https://www.rfc-editor.org/rfc/rfc7519)
- [JSON Web Tokens - jwt.io](https://jwt.io/)

## Node.js/NPM Version

```
node -v
v16.13.1

npm -v
8.1.2
```

## Tools to check JWT API execution

### Reference URL

- [Postman API Platform | Sign Up for Free](https://www.postman.com/)

## Demo Programming

- Create a package.json

```
npm init -y
```

- Install a Express(nodemon)
  ソースコードを save するたびにサーバーを自動で再起動してくれるモジュール。

```
npm i express nodemon
```

- Edit a package.json

```json
## Before
"scripts": {
    "start": "node server.js"
  }

## After
"scripts": {
    "start": "nodemon server.js"
  }
```

- Startup nodemon
  ローカルサーバーを起動します。

```
npm start
```

## Flow of New User Registration

### User enters e-mail address and password

To access the site, users enter their e-mail address and password.

### Check the validity of the entered e-mail address and password

For example, it checks if an e-mail address is entered, if a password of at least 7 characters is entered, etc.

### Check to see if a user already exists for the email address and password entered.

Check if a user has already been registered for the e-mail address and password entered from the DB.

### Password Encryption

If a new user is not in the DB, a new password is stored.
At this time, the password to be saved is encrypted (hashed) into a string that is not easily guessed.

### Save to DB

Store the user's e-mail address and encrypted (hashed) password in the DB.

### Publish JWT

JWT is issued to the client (PC, smartphone, etc.).
