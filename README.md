# conjur-policies
@CyberArk @ConjurInc policies for my lab

## Policy Load Order

To view the policy load order, please review [load_policies.sh](load_policies.sh).

## Directories

* /
  * `root` policy files split by resource type
* [authn](authn)
  * Authenticator web service policies
* [cd](cd)
  * Continuous delivery policies
* [ci](ci)
  * Continuous improvement policies
* [cloud](cloud)
  * Cloud provider policies
* [web](web)
  * Web application policies
* [delete](delete)
  * Delete records policy templates
* [grants](grants)
  * Grant policies to add members to groups for root branch

## License

[MIT](LICENSE)