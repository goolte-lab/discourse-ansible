# Discourse Orchestration (Ansible)

![lint](https://github.com/InformaticsMatters/discourse-ansible/workflows/lint/badge.svg)

![GitHub tag (latest SemVer)](https://img.shields.io/github/v/tag/informaticsmatters/discourse-ansible)

A playbook and Role to deploy [Discourse], suitable for execution by
[AWX].

This project contains one Ansible role:-

*   **discourse**

>   Note: The Role is designed to be executed from within our AWX server
    where credentials for the cluster (Kubernetes) reside. If you're not
    running from AWX (discouraged) then you will need to provide
    values for the variables that would be injected by AWX.

We depend on our [infrastructure] project's Kubernetes
**Certificate Manager** to generate https certificates.

As with all of our playbooks you can find the common user-defined variables
in the role's `defaults/main.yaml` and less common variables in
`vars/main.yaml`.

## Prerequisites
You will need: -

1.  A **PostgreSQL** database (better than v10) with a user
    and database that can be used by Discourse.
2.  A **Redis** database

>   You'll set the database details using variables you'll find in
    the `defaults` directory.

You could create a default Discourse database in PostgreSQL...

    # psql --username postgres --dbname postgres
    
    CREATE USER bn_discourse;
    ALTER USER bn_discourse WITH PASSWORD 'bitnami1';
    CREATE DATABASE bitnami_application;
    GRANT ALL PRIVILEGES ON DATABASE bitnami_application TO bn_discourse;

---

[awx]: https://github.com/ansible/awx
[discourse]: https://www.discourse.org
[infrastructure]: https://github.com/InformaticsMatters/ansible-infrastructure
