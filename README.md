BYU-CAS
=======

## Examples

### Retrieving a CAS ticket

```javascript
var cas = require('byu-cas');
var service = 'http://example.com/signin';

cas.getTicket('username', 'password', service)
.then(function(ticket){
  // do something with the ticket
});
```

### Validating a ticket
```javascript
var cas = require('byu-cas');

var ticket = doSomethingToGetTicket();
var service = 'http://example.com/signin';

cas.validate(ticket, service).then(function success(response) {
  console.log("Ticket valid! Hello, " + response.username);
  console.dir(response.attributes);
}).catch(function error(e) {
  console.log("Invalid ticket. Error message was: " + e.message);
});
```

Attributes come back in the following format

```javascript
{ restOfName: 'Peter Oliver',
  activeParttimeNonBYUEmployee: false,
  activeParttimeInstructor: false,
  inactiveFulltimeEmployee: false,
  surname: 'Rabbit',
  activeFulltimeInstructor: false,
  memberOf: [],
  preferredFirstName: 'Peter',
  sortName: 'Rabbit, Peter Oliver',
  activeFulltimeNonBYUEmployee: false,
  inactiveParttimeNonBYUEmployee: false,
  organization: false,
  activeEligibletoRegisterStudent: false,
  name: 'Peter Rabbit',
  preferredSurname: false,
  personId: '611290592',
  inactiveParttimeInstructor: false,
  netId: 'prabbit',
  inactiveFulltimeNonBYUEmployee: false,
  byuId: '872643180',
  restricted: false,
  emailAddress: 'prabbitbyu@sharklasers.com',
  alumni: false,
  inactiveParttimeEmployee: false,
  inactiveFulltimeInstructor: false,
  activeFulltimeEmployee: false,
  fullName: 'Peter Oliver Rabbit IV',
  activeParttimeEmployee: false }
```

## Contributing

We're pretty lax, but

* New features must come with an appropriate test
* New features should have an example in `README.md`
* Pull requests will generally not be merged if they break tests
* Use two spaces per indent
