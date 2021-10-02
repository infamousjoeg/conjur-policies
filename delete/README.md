# Delete Policies <!-- omit in toc -->

All `!delete` policies should be loaded into the branch where the policy the resource being deleted was loaded.

## What it is

A `!delete` is a definition that lets Conjur's policy engine know that a resource is going to be removed. The resource to remove is declared using the `record:` key.

## How it can be declared

```yaml
- !delete
  record: !user UserName
```

## How to load a delete policy

#### API

PATCH [Update Policy](https://docs.cyberark.com/Product-Doc/OnlineHelp/AAM-DAP/Latest/en/Content/Developer/Conjur_API_Update_Policy.htm?tocpath=Developer%7CREST%C2%A0APIs%7C_____15)

#### cybr-cli

The cybr-cli can be downloaded on GitHub at [https://github.com/infamousjoeg/cybr-cli](https://github.com/infamousjoeg/cybr-cli).

`cybr conjur update-policy -b root -f ./delete-root.yml`

* `-b` is the policy branch to load the policy on
* `-f` is the file path to load

#### Conjur CLI (Ruby)

`conjur policy load --delete root delete-root.yml`

#### Conjur CLI (Python)

`conjur policy update -b root -f ./delete-root.yml`

* `-b` is the policy branch to load the policy on
* `-f` is the file path to load