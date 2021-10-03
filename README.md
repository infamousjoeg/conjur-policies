# conjur-policies
@CyberArk @ConjurInc policies for my lab

## Policy Load Order

1. `conjur policy load root users.yml`
2. `conjur policy load root groups.yml`
3. `conjur policy load root grants/grants_user.yml`
4. `conjur policy load root root.yml`
5. `conjur policy load cd cd/ansible/ansible.yml`
6. `conjur policy load ansible cd/ansible/ops-team-1.yml`
7. `conjur policy load ansible cd/ansible/ops-team-2.yml`
8. `conjur policy load root grants/grants_cd.yml`
9. `conjur policy load ci ci/jenkins/jenkins.yml`
10. `conjur policy load jenkins ci/jenkins/dev-team-1.yml`
11. `conjur policy load jenkins ci/jenkins/dev-team-2.yml`
12. `conjur policy load jenkins ci/jenkins/projects.yml`
13. `conjur policy load ci ci/github/github.yml`
14. `conjur policy load github ci/github/actions.yml`
15. `conjur policy load ci ci/refactr/refactr.yml`
16. `conjur policy load refactr ci/refactr/onboarding.yml`
17. `conjur policy load root grants/grants_ci.yml`
18. `conjur policy load cloud cloud/aws/aws.yml`
19. `conjur policy load aws cloud/aws/ec2.yml`
20. `conjur policy load aws cloud/aws/lambda.yml`
21. `conjur policy load cloud cloud/gcp/gcp.yml`
22. `conjur policy load gcp cloud/gcp/compute.yml`
23. `conjur policy load gcp cloud/gcp/function.yml`
24. `conjur policy load root authn/authn-gcp.yml`
25. `conjur policy load root authn/authn-iam-prod.yml`
26. `conjur policy load root authn/authn-jwt-jenkins.yml`
27. `conjur policy load root authn/authn-k8s.yml`
28. `conjur policy load root seed-generation.yml`
29. `conjur policy load root grants/grants_authn.yml`
30. `conjur policy load root grants/grants_vcs.yml`

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
* [delete](delete)
  * Delete records policy templates
* [grants](grants)
  * Grant policies to add members to groups for root branch

## License

[MIT](LICENSE)