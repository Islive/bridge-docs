Docs for `user/identity`
=======

[&laquo; Back to user module overview](/api/user/index.md)

---------

login <small>- Added at v0.0.1</small>
------

Login a user.

### Parameters

| Parameter | Type     | Description                                |
| --------- | -------- | ------------------------------------------ |
| role      | String   | The role authenticating for                |
| username  | String   | The username / email                       |
| password  | String   | The password                               |
| callback  | Function | The callback that will be called when done |

### Example

```javascript
define(['bridge!user/identity'], function(identity) {

  var username = 'Bob'
    , password = 'keeshond';

  identity.login('visitor', username, password, function(error, result) {
    if (error) {
      // Authentication error
    }

    var user = result;
  });
});
```

------

loginByHash <small>- Added at v0.0.1</small>
------

Login a user by hash.

### Parameters

| Parameter  | Type              | Description                                |
| ---------- | ----------------- | ------------------------------------------ |
| role       | String            | The role authenticating for                |
| email      | String            | The email address                          |
| hash       | String            | The hash                                   |
| [username] | String / Function | The username, or callback                  |
| callback   | Function          | Callback if username was supplied          |

### Example

```javascript
define(['bridge!user/identity'], function(identity) {

  var email = 'user@example.net'
    , hash  = 'Jpe+MKFtRW7Hs1xfPKjUMQ';

  identity.loginByHash('visitor', email, hash, function(error, result) {
    if (error) {
      // Authentication error
    }

    var user = result;
  });
});
```

------

hasIdentity <small>- Added at v0.0.1</small>
------

Check if the current client has an identity.

### Parameters

| Parameter | Type     | Description                                |
| --------- | -------- | ------------------------------------------ |
| role      | String   | The role checking the identity for         |
| callback  | Function | The callback that will be called when done |

### Example

```javascript
define(['bridge!user/identity'], function(identity) {

  var role = 'performer';

  identity.hasIdentity(role, function(error, result) {
    if (error) {
      // Error while fetching the identity
    }

    var userLoggedIn = result;
  });
});
```

------

usernameAvailable <small>- Added at v0.0.1</small>
------

Check if a specific username is available.

### Parameters

| Parameter | Type     | Description                                |
| --------- | -------- | ------------------------------------------ |
| username  | String   | The username                               |
| callback  | Function | The callback that will be called when done |

### Example

```javascript
define(['bridge!user/identity'], function(identity) {

  var username = 'spongebob';

  identity.usernameAvailable(username, function(error, available) {
    if (error) {
      // Handle error
    }

    var usernameAvailable = available;
  });
});
```

------

logout <small>- Added at v0.0.1</small>
------

Destroy the client's identity.

### Parameters

| Parameter | Type     | Description                                |
| --------- | -------- | ------------------------------------------ |
| callback  | Function | The callback that will be called when done |

### Example

```javascript
define(['bridge!user/identity'], function(identity) {

  identity.logout(function(result) {
    // Logged out.
  });
});
```

------

getUsername <small>- Added at v0.0.1</small>
------

Get the username from a user ID.

### Parameters

| Parameter | Type     | Description                                |
| --------- | -------- | ------------------------------------------ |
| userId    | String   | The user ID                                |
| callback  | Function | The callback that will be called when done |

### Example

```javascript
define(['bridge!user/identity'], function(identity) {

  identity.getUsername('53b69e2d187c317122e0ddc7', function(error, result) {
    if (error) {
      // Error while fetching the username
    }

    var username = result;
  });
});
```

------

getUserId <small>- Added at v0.0.1</small>
------

Get the user ID from the authenticated user.

### Parameters

| Parameter | Type     | Description                                |
| --------- | -------- | ------------------------------------------ |
| callback  | Function | The callback that will be called when done |

### Example

```javascript
define(['bridge!user/identity'], function(identity) {

  identity.getUserId(function(error, result) {
    if (error) {
      // Error while fetching the userId
    }

    var userId = result;
  });
});
```

------

getIdentity <small>- Added at v0.0.1</small>
------

Get the user's identity. Contains user information and role.

### Parameters

| Parameter | Type     | Description                                |
| --------- | -------- | ------------------------------------------ |
| role      | String   | The role [visitor, performer]              |
| callback  | Function | The callback that will be called when done |
| force     | Boolean  | force update (don't use cached identity)   |

### Example

```javascript
define(['bridge!user/identity'], function(identity) {

  identity.getIdentity('visitor', function(error, result) {
    if (error) {
      // Error while fetching the identity
    }

    var userIndentity = result;
  });
});
```

------

getPartnerInfo <small>- Added at v0.0.1</small>
------

Get the partnerInfo for `identity` based on conditions.

### Parameters
| Parameter | Type     | Description                                |
| --------- | -------- | ------------------------------------------ |
| callback  | Function | The callback that will be called when done |
| offline   | Boolean  | Check identity for partnerInfo or not.     |

### Example

```javascript
define(['bridge!user/identity'], function (identity) {
  identity.getPartnerInfo(function (error, info) {
    // Info holds "partnerCode" and "partnerInfo" properties.
  }, true); // Won't try to get info from identified user.
});
```

-----

update <small>- Added at v0.1.0</small>
-----
Update the given properties for the authenticated user.

### Parameters

| Parameter    | Type             | Description                                |
| ------------ | ---------------- | ------------------------------------------ |
| updateValues | Object           | The properties you want to update          |
| callback     | Function         | The callback that will be called when done |

### Example

```js
define(['bridge!user/identity'], function(identity) {

  var updateValues = {notificationEmail : 'bob@keeshond.com'};

  identity.update(updateValues, function(error, response) {
    if (error) {
      // Error while setting the new data
    }

    var userIdentity = response;
  });
});
```

-----
