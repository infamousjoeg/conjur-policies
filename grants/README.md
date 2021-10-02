# Grant Policies <!-- omit in toc -->

All `!grant` policies should be loaded into the `root` branch.

- [What it is](#what-it-is)
- [How it can be declared](#how-it-can-be-declared)
    - [Single resource membership](#single-resource-membership)
    - [Multiple resource membership](#multiple-resource-membership)
- [Common Root Branch Membership Grants](#common-root-branch-membership-grants)

## What it is

A `!grant` is the same as adding a member to a security group in Active Directory in Conjur's policy-as-code.

## How it can be declared

#### Single resource membership

```yaml
- !grant
  role: !group GroupName
  member: !user UserName
```

#### Multiple resource membership

```yaml
- !grant
  role: !group GroupName
  members:
    - !user UserName
    - !host HostName
    - !group AnotherGroupName
```

## Common Root Branch Membership Grants

* User groups
  * Admins
  * Auditors
* Vault Conjur Synchronizer consumer groups
* Vault Conjur Synchronizer admin groups
* Authenticator groups
