# MicroProfile REST API with JWT Auth

This repository shows how to create a REST API with MicroProfile and use JWT for authentication. Please read [Build a REST API Using Java, MicroProfile, and JWT Authentication](https://developer.okta.com/blog/2019/07/10/java-microprofile-jwt-auth) to see how this example was created.

**Prerequisites:** [Java 8](https://adoptopenjdk.net/).

> [Okta](https://developer.okta.com/) has Authentication and User Management APIs that reduce development time with instant-on, scalable user infrastructure. Okta's intuitive API and expert support make it easy for developers to authenticate, manage, and secure users and roles in any application.

* [Getting Started](#getting-started)
* [Links](#links)
* [Help](#help)
* [License](#license)

## Getting Started

To install this example, run the following commands:

```bash
git clone https://github.com/oktadeveloper/okta-microprofile-jwt-auth-example.git
cd okta-microprofile-jwt-auth-example
```

### Create an Application in Okta

Log in to your Okta Developer account (or [sign up](https://developer.okta.com/signup/) if you don’t have an account).

1. From the **Applications** page, choose **Add Application**.
2. On the Create New Application page, select **Web**.
3. Give your app a memorable name, add `https://oidcdebugger.com/debug` as a Login redirect URI, check the box next to **Implicit (Hybrid)**, then click **Done**.

Modify `pom.xml` to use your Okta domain:

```xml
<properties>
  ...
  <oktaDomain>{yourOktaDomain}</oktaDomain>
</properties>
```

**NOTE:** The value of `{yourOktaDomain}` should be something like `dev-123456.okta.com`. Make sure you don't include `-admin` in the value!


Build your app and start the server:

```
mvn install liberty:start-server
```

To generate a JWT access token, go to https://oidcdebugger.com/ and fill out the values for your OIDC application.

In a shell, store the token in a variable. Then use it to hit the API and authentication with JWT:

```
http :8181/DemoAPI/data/protected "Authorization: Bearer $TOKEN"
```

## Links

This example uses the following open source libraries:

* [Eclipse MicroProfile](https://microprofile.io/) 
* [Java JWT](https://github.com/jwtk/jjwt)
* [Open Liberty](https://openliberty.io/)

## Help

Please post any questions as comments on the [blog post](https://developer.okta.com/blog/2019/07/10/java-microprofile-jwt-auth), or on the [Okta Developer Forums](https://devforum.okta.com/).

## License

Apache 2.0, see [LICENSE](LICENSE).
