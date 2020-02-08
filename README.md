# Kerberos

[Kerberos](http://web.mit.edu/kerberos/) is a network authentication protocol. It is designed to provide strong authentication for client/server applications by using secret-key cryptography.

![Kerberos](./img/dog-ring.jpg)

Here we will find two Ansible Roles to setup a simple [Master KDC Server](https://web.mit.edu/kerberos/krb5-devel/doc/admin/install_kdc.html#install-and-configure-the-master-kdc) and clients for testing purposes.

- [Kerberos Server](./ansible/roles/kerberos-server/README.md) - Setup the KDC Server
- [Kerberos Client](./ansible/roles/kerberos-client/README.md) - Setup the clients

Both roles come with testing environment, but the client one will setup both.

They will use the [MIT](https://web.mit.edu/kerberos/krb5-devel/doc/index.html#) distribution.

> We advise to read [this post](https://www.roguelynn.com/words/explain-like-im-5-kerberos/) for more in-depth information regarding Kerberos.
