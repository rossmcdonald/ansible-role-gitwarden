Gitwarden Agent Ansible Role
=====================

This role installs and configures
the [GitWarden agent](https://github.com/gitwarden/gitwarden-agent) for
the [GitWarden](https://gitwarden.com) service.

Requirements
------------

This role is only supported on RedHat-based and Debian-based systems, which
includes all modern versions of the following:

* Debian (squeeze, jessie)
* Ubuntu (precise, trusty, wheezy, xenial, yakkety, zesty)
* RedHat Enterprise Linux (6, 7)
* CentOS (6, 7)
* Amazon Linux (2017.03, 2016.09, 2016.03, 2015.09, 2015.03)

There are no other requirements for running this role.

Role Variables
--------------

The variables for running this role are:

* `gitwarden_api_key_id` (string) - is the GitWarden API key ID for your Github
  organization. This can be obtained through
  the [GitWarden dashboard](https://gitwarden.com) once your organization is
  added.

* `gitwarden_api_key_secret` (string) - is the GitWarden API key secret for the
  corresponding API ID above.

* `gitwarden_teams` (list of strings) - is a list of Github teams to create user
  accounts for on the bootstrapped instance. The included team names should
  match the display name of the Github team (or what you see when viewing the
  team in Github).

* `gitwarden_admin_teams` (list of strings) - is a list of Github teams to
  create _administrative_ accounts for on the bootstrapped instance. Any team
  included in this listing will have super-user access on the instance. The
  included team names should match the display name of the Github team (or what
  you see when viewing the team in Github).

No other variables are required.

Dependencies
------------

There are no dependencies for this role.

Example Playbook
----------------

Here is a small example of how to use the role:

```yaml
    - hosts: servers
      roles:
         - gitwarden.gitwarden-agent
           gitwarden_api_key_id: MYAPIKEYID
           gitwarden_api_key_secret: MYAPIKEYSECRET
           gitwarden_teams:
             - Employees
             - Contractors
           gitwarden_admin_teams:
             - System Administrators
             - DevOps
         ...
```

License
-------

Apache2

Author
------

Created by Ross @ [GitWarden](https://gitwarden.com).
