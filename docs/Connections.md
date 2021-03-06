SSH Connections
===============

A connection is your starting point to all SSH communications. To establish a connection, you first require a
credential object. Your credential object will contain your user/pass or keypair.

    $auth = new PasswordCredential('username', 'password');
    $connection = new Connection('hostname', 22, $auth);

or rather,

    $auth = new KeyCredential('username', '/path/to/key.pem.pub', '/path/to/key.pem', 'keypassword');
    $connection = new Connection('hostname', 22, $auth);

Once you have a connection ready, you can connect, check fingerprints and authenticate:

    $connected = $connection->connect("6F89C2F0A719B30CC38ABDF90755F2E4");   // Fingerprint optional
    $authenticated = $connection->authenticate();

An exception will be raised if the server fingerprint is a mismatch. Once authenticated, you're now able to execute
commands or request an interactive shell.

PSR-3 Logger Support
--------------------
The Connection class implements the PSR-3 LoggerAwareInterface, you may provide a LoggerInterface for the connection
object to log to.


See Also
--------

* [Executing Commands](ExecutionStream.md)
* [Interactive Shell](Shell.md)
