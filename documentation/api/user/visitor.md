Docs for `user/visitor`
=======

[&laquo; Back to user module overview](/api/user/index.md)

-----

getIdentity <small>- Added at v0.0.1</small>
-----

Get the user's identity. Contains user information such as credit count.

### Parameters

| Parameter | Type     | Description                                            |
| --------- | -------- | ------------------------------------------------------ |
| callback  | Function | The callback that will be called when creation is done |

### Example
```js
define(['bridge!user/visitor'], function(visitor) {

  visitor.getIdentity(function(error, result) {
    if (error) {
      // Error while fetching user
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
| callback  | Function | The callback that will be called when done |

### Example

```javascript
define(['bridge!user/visitor'], function(visitor) {

  visitor.hasIdentity(function(error, result) {
    if (error) {
      // Error while fetching the identity
    }

    var userLoggedIn = result;
  });
});
```

-----

login <small>- Added at v0.0.1</small>
-----
Login a visitor.

### Parameters

| Parameter | Type          | Description                                            |
| --------- | ------------- | ------------------------------------------------------ |
| username  | String        | The username / email                                   |
| password  | String        | The password                                           |
| callback  | Function      | The callback that will be called when done             |

### Example
```js
define(['bridge!user/visitor'], function(visitor) {

  var username = 'Bob'
    , password = 'keeshond';

  visitor.login(username, password, function(error, result) {
    if (error) {
      // Authentication error
    }

    var user = result;
  });
});
```

-----

loginByHash <small>- Added at v0.0.1</small>
------

Login a visitor by hash.

### Parameters

| Parameter | Type     | Description                                |
| --------- | -------- | ------------------------------------------ |
| email     | String   | The email address                          |
| hash      | String   | The hash                                   |
| callback  | Function | The callback that will be called when done |

### Example

```javascript
define(['bridge!user/visitor'], function(visitor) {

  var email = 'user@example.net'
    , hash  = 'Jpe+MKFtRW7Hs1xfPKjUMQ';

  visitor.loginByHash(email, hash, function(error, result) {
    if (error) {
      // Authentication error
    }

    var user = result;
  });
});
```

-----

register <small>- Added at v0.0.1</small>
------

Register a new visitor

### Parameters

| Parameter | Type     | Description                                                      |
| --------- | -------- | ---------------------------------------------------------------- |
| params    | Object   | Object of params: username, password, email[, wallet][, p][, pi] |
| callback  | Function | The callback that will be called when done                       |

### Example

```javascript
define(['bridge!user/visitor'], function(visitor) {

  var params = {
    username: 'foo',
    password: 'abcd',
    email   : 'my@domain.nl',
    wallet  : 'wallet url',   // The wallet `from_url`. NOTE: Will create wallet account.
    p       : '61',           // Defaults to Object "partnerCode"
    pi      : 'typein'        // Defaults to Object "partnerInfo"
  };

  visitor.register(params, function(error, createdAccount) {
    if (error) {
      // Authentication error
    }

    var user = createdAccount;
  });
});
```

------

getUserId <small>- Added at v0.0.1</small>
-----
Get the user id of the authenticated visitor.

### Parameters

| Parameter | Type          | Description                                            |
| --------- | ------------- | ------------------------------------------------------ |
| callback  | Function      | The callback that will be called when done             |

### Example
```js
define(['bridge!user/visitor'], function(visitor) {

  visitor.getUserId(function(error, result) {
    if (error) {
      // Error while fetching userId
    }

    var userId = result;
  });
});
```

-----

hasUsername <small>- Added at v0.0.1</small>
-----
Check if the visitor has a username.

### Parameters

| Parameter | Type          | Description                                            |
| --------- | ------------- | ------------------------------------------------------ |
| callback  | Function      | The callback that will be called when done             |

### Example
```js
define(['bridge!user/visitor'], function(visitor) {

  visitor.hasUsername(function(error, result) {
    if (error) {
      // Error while fetching username
    }

    var boolean = result;
  });
});
```

-----

setUsername <small>- Added at v0.0.1</small>
-----
Set the username of the authenticated visitor.

### Parameters

| Parameter | Type          | Description                                            |
| --------- | ------------- | ------------------------------------------------------ |
| username  | String        | The username                                           |
| callback  | Function      | The callback that will be called when done             |

### Example
```js
define(['bridge!user/visitor'], function(visitor) {

  var username = 'Bob';

  visitor.setUsername(username, function(error) {
    if (error) {
      // Error while setting username
    }
  });
});
```

-----

getCredits <small>- Added at v0.0.1</small>
-----
Get the amount of credits the authenticated visitor has.

### Parameters

| Parameter | Type     | Description                                            |
| --------- | -------- | ------------------------------------------------------ |
| callback  | Function | The callback that will be called when fetching is done |

### Example
```js
define(['bridge!user/visitor'], function(visitor) {

  visitor.getCredits(function(error, result) {
    if (error) {
      // Error while fetching credits
    }

    var credits = result;
  });
});
```

follow <small>- Added at v0.3.0</small>
------

Follow a performer

### Parameters

| Parameter | Type     | Description                                            |
| --------- | -------- | ------------------------------------------------------ |
| username | String   | The name of the performer                              |
| callback  | Function | The callback that will be called when creation is done |

### Example
```js
define(['bridge!user/visitor'], function(visitor) {

  var performerName = 'kaatje';

  visitor.follow(performerName, function(error) {
    if (error) {
      // Failed following the performer
    }
  });
});
```

---------
isFollowing <small>- Added at v0.3.0</small>
------

See if the user follows a certain performer

### Parameters

| Parameter  | Type     | Description                                            |
| ---------- | -------- | ------------------------------------------------------ |
| username   | String   | The name of the performer                              |
| callback   | Function | The callback that will be called when creation is done |

### Example
```js
define(['bridge!user/visitor'], function(visitor) {

  var performerName = 'kaatje';

  visitor.isFollowing(performerName, function(error, boolean) {
    if (error) {
      // Failed getting the followed performer(s)
    }

    var isFollowing = boolean;
  });
});
```

---------
following <small>- Added at v0.3.0</small>
------

See which performers the user is following

### Parameters

| Parameter  | Type     | Description                                            |
| ---------- | -------- | ------------------------------------------------------ |
| callback   | Function | The callback that will be called when creation is done |

### Example
```js
define(['bridge!user/visitor'], function(visitor) {

  visitor.isFollowing(function(error, result) {
    if (error) {
      // Failed getting the followed performer(s)
    }

    var performers = result;
  });
});
```

---------
unFollow <small>- Added at v0.3.0</small>
------

Unfollow a performer

### Parameters

| Parameter  | Type     | Description                                            |
| ---------- | -------- | ------------------------------------------------------ |
| username   | String   | The name of the performer                              |
| callback   | Function | The callback that will be called when creation is done |

### Example
```js
define(['bridge!user/visitor'], function(visitor) {

  var performerName = 'kaatje';

  visitor.unFollow(performerName, function(error) {
    if (error) {
      // Failed unfollowing the performer
    }
  });
});
```
