An md5 hash is used on each request after a succesful handshake.

* The hash is built with all the strings values inside the message, plus sequence and **key** in the middle.
* The key is dynamically provided by a message in response to a successfull login and it's always followed by **leroy**.
* The initial key for the login hash is just ``leroy``.

Rest queries such the one for set drone coordinates replace sequence with method (i.e 'GET')


