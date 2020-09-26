Our Identity and Access Management system gives you full control over who or what can access specific resources on the
CBWS platform.

Most resources have an IAM policy that describes which principals (users, groups or service accounts)
can access the particular resource and what can be done with it.

You can for example give developers read-only access to your production projects, give administrators owner rights
and auditors access to view logs. This can even be controlled on individual resources like a specific virtual machine,
service account, or something else.

To assign permissions we define a policy on a resource, this policy has one or more bindings. Each binding uses a
predefined role (owner, virtual machine admin, something else), has a description you can define for future reference
and a list of members (principals like users, groups and service accounts) to which this binding applies.

The CBWS platform provides a number of predefined roles per service as well as more generic roles like owner, editor
and viewer.

The IAM service also provides service accounts which allow services, scripts, background jobs etc to access our APIs,
the service accounts are full on principals that can be given access to specific resources via IAM policies.
