# OAuth2 Scopes [](id=oauth2-scopes)

In OAuth 2.0, applications are granted access to limited subsets of user data.
These are called *scopes* (not to be confused with Liferay scopes). They are
created in two ways: 

1.  By administrators, by creating a Service Access Policy for the scope

2.  By developers, by creating a JAX-RS endpoint. By default, scopes are 
    generated based on the HTTP verbs supported by the JAX-RS endpoint.
    A special annotation override this behavior and register specific scopes. 

## Creating a Scope for a JSONWS Service [](id=creating-a-scope-for-a-jsonws-service)

The most common way to create a scope is to create a 
[Service Access Policy](/discover/deployment/-/knowledge_base/7-1/service-access-policies)
prefixed with the name `OAUTH2_`. This naming convention causes the policy to appear
in the OAuth application configuration screen as a scope. 

For example, say the application needs access to a user's profile information to
retrieve the email address. To grant the application access to this, go to
*Control Panel* &rarr; *Configuration* &rarr; *Service Access Policy*, and
create the policy pictured below. 

![Figure 1: A Service Access Policy defines a scope for OAuth 2.0 applications.](../../../images/oauth-service-access-policy.png)

Note that the policy is not a default policy, and that it grants access only to
one method in the `UserService`. This is a JSONWS web service generated by
Service Builder. You can view a list of all available services in your
installation at this URL: 

    http://[host]:[port]/api/jsonws/

Once you create a policy and name it with the `OAUTH2_` prefix, it appears in
the *Scopes* tab in OAuth2 Administration. 

![Figure 2: Scopes named with the proper prefix appear in the Scopes tab of your application configuration.](../../../images/oauth-scopes-tab.png)

Now you can select it and save your application. 

## Creating a Scope for a JAX-RS Service [](id=creating-a-scope-for-a-jax-rs-service)

Without any special Liferay OAuth2 annotations or properties, a standard OSGi
JAX-RS application is inspected by the Liferay OAuth2 runtime and scopes are
derived based on the HTTP verbs supported by the application.

When developers want more control, they can register their JAX-RS application 
with the property `oauth2.scopechecker.type=annotations` and annotate endpoint 
resource methods or whole classes like this:

    @RequiresScope("scopeName")

Once deployed, this becomes a scope in the OAuth 2.0 configuration. 

Great! Now that you understand scopes, it's time to make the authorization
process happen in your application. 
