# conjur-policies
@CyberArk @ConjurInc policies for my lab

## Policy Load Order

1. `conjur policy load root users.yml`
2. `conjur policy load root groups.yml`
3. `conjur policy load root grants/grants_user.yml`
4. `conjur policy load root root.yml`
5. `conjur policy load cd cd/ansible/ansible.yml`
6. `conjur policy load cd/ansible cd/ansible/ops-team-1.yml`
7. `conjur policy load cd/ansible cd/ansible/ops-team-2.yml`
8. `conjur policy load root grants/grants_cd.yml`
9. `conjur policy load ci ci/jenkins/jenkins.yml`
10. `conjur policy load ci/jenkins ci/jenkins/dev-team-1.yml`
11. `conjur policy load ci/jenkins ci/jenkins/dev-team-2.yml`
12. `conjur policy load ci/jenkins ci/jenkins/projects.yml`
13. `conjur policy load ci ci/github/github.yml`
14. `conjur policy load ci/github ci/github/actions.yml`
15. `conjur policy load ci ci/refactr/refactr.yml`
16. `conjur policy load ci/refactr ci/refactr/onboarding.yml`
17. `conjur policy load root grants/grants_ci.yml`
18. `conjur policy load cloud cloud/aws/aws.yml`
19. `conjur policy load cloud/aws cloud/aws/ec2.yml`
20. `conjur policy load cloud/aws cloud/aws/lambda.yml`
21. `conjur policy load cloud cloud/gcp/gcp.yml`
22. `conjur policy load cloud/gcp cloud/gcp/compute.yml`
23. `conjur policy load cloud/gcp cloud/gcp/function.yml`
24. `conjur policy load cloud cloud/thales/thales.yml`
25. `conjur policy load web web/conjur-oidc-demo.yml`
26. `conjur policy load root authn/authn-gcp.yml`
27. `conjur policy load root authn/authn-iam-prod.yml`
28. `conjur policy load root authn/authn-jwt-jenkins.yml`
29. `conjur policy load root authn/authn-k8s.yml`
30. `conjur policy load root authn/authn-oidc-webapp.yml`
31. `conjur policy load root authn/seed-generation.yml`
32. `conjur policy load root grants/grants_authn.yml`
33. `conjur policy load root grants/grants_vcs.yml`
34. `conjur policy load root grants/grants_host.yml`

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