# Store credentials

### Using cache

{% embed url="https://git-scm.com/docs/git-credential-cache" %}

This command caches credentials **in memory** for use by future Git programs. The stored credentials **never touch the disk**, and are forgotten after a configurable timeout. The cache is accessible over a **Unix domain socket,** **restricted to the current user** by filesystem permissions.

* socket -  an internal endpoint of local [inter-process communication](https://en.wikipedia.org/wiki/Inter-process_communication) \(IPC\) \(not over a network\)
* [Unix domain sockets](https://en.wikipedia.org/wiki/Unix_domain_socket) \(UDS\), for internal inter-process communication.. exchanging data between processes executing on the **same host operating system.**
  * all communication occurs entirely within the operating system [kernel](https://en.wikipedia.org/wiki/Kernel_%28operating_system%29).

Conclusion: 

The credentials are cached in memory \(are not stored on disk\) and are accessible only for processes created by the same user and for the limited period of time \(60sec in our case\)

### On disk 

{% embed url="https://git-scm.com/docs/git-credential-store" %}





