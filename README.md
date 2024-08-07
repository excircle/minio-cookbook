# MinIO Cookbook
A repository dedicated to MinIO administrative tricks and tips

Table of contents
=================

<!--ts-->
   * [Summary](#summary)
   * [mc admin](#mc-admin)
      * [Finding The MinIO ARN for an Established OIDC Account](##Finding-The-MinIO-ARN-for-an-Established-OIDC-Account)
   * [Tests](#tests)
<!--te-->

# Summary

# `mc admin`

## Finding The MinIO ARN for an Established OIDC Account

When configuring OIDC in MinIO, you will need to assign a pre-existing or custom role to provide successfully authenticated users. When writing code against this established OIDC, you will need to know where to find the unique ARN that is associated with the established OIDC's role.

Consider the following `mc admin` command:

```bash
ubuntu@minio-bastion-host:~$ mc idp openid info $ALIAS $NAME_OF_OIDC_CONFIG
╭────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│      claim_userinfo: off                                                                                   │
│           client_id: 0oahf59ud3CUAiFdP697                                                                  │
│          config_url: https://trial-12345678-admin.okta.com/.well-known/openid-configuration                │
│              enable: on                                                                                    │
│        redirect_uri: http://minio-load-balancer-123456789.us-west-2.elb.amazonaws.com:9001/oauth_callback  │
│redirect_uri_dynamic: on                                                                                    │
│             roleARN: arn:minio:iam:::role/dIUx-BmnIqYevLY6moHYLkD25yg    <<<<<UNIQUE ARN                   │
│         role_policy: readwrite                                                                             │
│              scopes: openid,profile,email                                                                  │
╰────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
```