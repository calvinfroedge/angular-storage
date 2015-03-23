# angular-storage

A Storage done right for AngularJS.

## Key Features

* Uses **`localStorage` by default but if it's not available, it uses `ngCookies`**.
* Lets you **save JS Objects**
* If **you save a `Number`, you get a `Number`**, not a String
* Uses a **caching system** so that if you already have a value, it won't get it from the store again.

## Installing it

You have several options:

````bash
bower install a0-angular-storage
````

````bash
npm install angular-storage
````

````html
<script type="text/javascript" src="https://cdn.rawgit.com/auth0/angular-storage/master/dist/angular-storage.js"></script>
````

## Using it

````js
angular.module('app', ['angular-storage'])
.controller('Controller', function(aiStorage) {
  var myObj = {
    name: 'mgonto'
  };

  aiStorage.set('obj', myObj);

  var myNewObject = aiStorage.get('obj');

  angular.equals(myNewObject, myObj); // return true

  aiStorage.remove('obj');

  aiStorage.set('number', 2);

  typeof(aiStorage.get('number')) === 'number'
});
````

## Namespaced Storages

You can also create namespaced storages if you want

````js
angular.module('app', ['angular-storage'])
.factory('Auth0Store', function(aiStorage) {
  return aiStorage.getNamespacedStore('auth0');
})
.controller('Controller', function(Auth0Store) {

  var myObj = {
    name: 'mgonto'
  };
  
  // This will be saved in localStorage as auth0.obj
  Auth0Store.set('obj', myObj);

  // This will look for auth0.obj
  var myNewObject = Auth0Store.get('obj');

  angular.equals(myNewObject, myObj); // return true
});
````

## API

### aiStorage.set(name, value)

Sets a new `value` to the storage with the key `name`. It can be any object.

### aiStorage.get(name)

Returns the saved `value` with they key `name`. If you saved an object, you get an object.

### aiStorage.remove(name)

Deletes the saved `value` with the key `name`

### aiStorage.getNamespacedStore(namespace, delimiter)

Returns a new `aiStorage` service that will use the `namespace` and `delimiter` when saving and getting values like the following `namespace[delimiter]key`. For example `auth0.object` considering `auth0` as `namespace` and `.` as a `delimiter`

## Usages

This library is used in [auth0-angular](https://github.com/auth0/auth0-angular)

## Contributing

Just clone the repo, run `npm install`, `bower install` and then `gulp` to work :).

## Issue Reporting

If you have found a bug or if you have a feature request, please report them at this repository issues section. Please do not report security vulnerabilities on the public GitHub issue tracker. The [Responsible Disclosure Program](https://auth0.com/whitehat) details the procedure for disclosing security issues.

## License

MIT

## What is Auth0?

Auth0 helps you to:

* Add authentication with [multiple authentication sources](https://docs.auth0.com/identityproviders), either social like **Google, Facebook, Microsoft Account, LinkedIn, GitHub, Twitter, Box, Salesforce, amont others**, or enterprise identity systems like **Windows Azure AD, Google Apps, Active Directory, ADFS or any SAML Identity Provider**.
* Add authentication through more traditional **[username/password databases](https://docs.auth0.com/mysql-connection-tutorial)**.
* Add support for **[linking different user accounts](https://docs.auth0.com/link-accounts)** with the same user.
* Support for generating signed [Json Web Tokens](https://docs.auth0.com/jwt) to call your APIs and **flow the user identity** securely.
* Analytics of how, when and where users are logging in.
* Pull data from other sources and add it to the user profile, through [JavaScript rules](https://docs.auth0.com/rules).

## Create a free account in Auth0

1. Go to [Auth0](https://auth0.com) and click Sign Up.
2. Use Google, GitHub or Microsoft Account to login.




