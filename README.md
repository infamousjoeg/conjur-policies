# conjur-policies
@CyberArk @ConjurInc policies for my lab

## Policy Load Order

1. `conjur policy load root users.yml`
2. `conjur policy load root groups.yml`
3. `conjur policy load root hosts.yml`
4. `conjur policy load root grants.yml`
5. `conjur policy load root root.yml`
6. `conjur policy load pki other/pki.yml`
7. `conjur policy load tower cd/tower.yml`
8. `conjur policy load secretless-demo other/secretless-demo.yml`
9. `conjur policy load jenkins ci/jenkins.yml`

## Directories

* /
  * `root` policy files split by resource type
* authn
  * Authenticator web service policies
* cd
  * Continuous delivery policies
* ci
  * Continuous improvement policies
* cloud
  * Cloud provider policies
* delete
  * Delete records policy templates
* other
  * Miscellaneous policies for demonstrations

## License

[MIT](LICENSE)