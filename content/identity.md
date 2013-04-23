# Identity Management, Authentication and Authorization



## Identity Management

Identity management is about adding, updating or removing users from our application.


## What is a User #1

A user is a person who aim at using our software.


## What is a User #2

A user is the representation of a person in our software


## What is a User #3

A user is the representation of a person in our directory. He has :

* credentials
* a first name
* a last name
* an email address


## What is a User #3

A user is the representation of a person in our directory **and he belongs to some groups**



## Authentication

Authentication is about saying :
> This user is Alexandre Zapolsky, you can trust me, I've checked it


## How to authenticate

There's plenty of authentication scheme :

* login/password
* physical token authentication
* OpenId
* SAML
* CAS
* ... probably a lot more ...


## Does it matter to an application writer ?

The short answer is : **NO**


## Does it matter to an application writer ?

It's not an application matter, it's an integration one. A PaaS must provide a lot of authentication scheme but should not take decision about this.


## Does it matter to an application writer ?

It's not an application matter until we realize we should make OpenPaaS instance communication possible by defining a collaboration protocol around authentication


## Does it matter to an application writer ?

Inter-instance trust is SAML aim, we should come with an integrated SAML workflow to connect instance with simple click



## Authorization

Authorization is about saying :
> Alexandre Zapolsky can raise Matthieu Baechler's salary

or

> Matthieu Baechler can't raise its own salary


## Authorization

Is about making decisions based on the user profile


## Authorization

Must be described at the application level, probably as close to the code as possible


## Authorization

Public APIs should look like :

    @RequiresPermissions(“account:create”)‏
    public void openAccount( Account acct ) {
     //create the account
    }

Or

    @RequiresRoles( “teller” )
    public void openAccount( Account acct ) {
     //do something in here that only a teller
     //should do
    }

Code stolen from [Shiro documentation](http://shiro.apache.org/java-authorization-guide.html)



## Putting everything in a single picture

    +-------------------------------------------------------------+
    |            Authentication          Identity Management      |
    |                                                             |
    |                +-----+           +----------------------+   |
    |                |     |           |                      |   |
    |                | L   | Provides  |  RSE                 |   |
    |                | E   +-----------+                      |   |
    |                | M   | Headers   |                      |   |
    |                | O   |           +----------------------+   |
    |                | N   |                                      |
    |                | L   |           +----------------------+   |
    |                | D   |           |                      |   |
    |                | A   |           |  LinID               |   |
    |                | P   |           |                      |   |
    |                | :   |           +-------+--------------+   |
    |                | :   |                   | Manage           |
    |                | N   |           +-------+------+           |
    |                | G   |  Query    |              |           |
    |                |     +-----------+  LDAP        |           |
    |                |     |           |              |           |
    |                +-----+           +--------------+           |
    |                                                             |
    +-------------------------------------------------------------+


## Putting everything in a single picture

In the short term :

* LemonLDAP::NG authenticates the user against an LDAP directory and provides the application some HTTP headers containing details on the logged user and its identity
* LinID provides an LDAP management tool to create, update and remove users from the application, including group attribution
* LDAP provides us a user directory
* and the application have to use some framework like Apache Shiro to do some Role Base Access Control


## Putting everything in a single picture

In the future :

* We could ask LinID team to help us integrate user management features right into the RSE for a better User Experience
* We can add application informations on top of the LDAP user and make automatic synchronization from LDAP to our application
* We can use LemonLDAP::NG to do inter-instance SAML authentication



## Roadmap

1. By end of may, we should create a prototype of the Big Picture
2. Then, we should be able to implement groups and roles found in the specification into LinID
3. Then, we should be able to implement RBAC in the application REST services


## Questions ?



## The technical side of my slides

* Powered by [Reveal.js](http://lab.hakim.se/reveal-js)
* Written using [Markdown](http://daringfireball.net/projects/markdown/)
 * but waiting for a Asciidoc plugin
* Hosted by [Github](https://github.com)