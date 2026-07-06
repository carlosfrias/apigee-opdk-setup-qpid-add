# apigee-opdk-setup-qpid-add — Add a Qpid Server to an Apigee OPDK Analytics Group

> **An Ansible role that registers a Qpid server with the Management Server and adds it to an analytics consumer group** — the Qpid step in the Apigee analytics topology lifecycle: `axgroup → consumer-group → {consumers (qpid), datastores (postgres)}`.

> [!NOTE]
> Engineering portfolio note — this role is part of the analytics-topology lifecycle. See the [skills assessment →](SKILLS-ASSESSMENT.md) for the expertise applied.

This role adds a Qpid (analytics consumer) to an existing axgroup and its consumer group. It is composed after `apigee-opdk-setup-analytics-group-add` (which creates the axgroup and consumer group) and before `apigee-opdk-setup-scopes-add` (which binds org/env scopes). See the [`apigee-edge-opdk`](https://github.com/carlosfrias/apigee-edge-opdk) framework for composition playbooks.

<!-- BEGIN Google Required Disclaimer -->

## Not Google Product Clause

This is not an officially supported Google product.
<!-- END Google Required Disclaimer -->

---

## What the role actually does

`tasks/main.yml`:

1. **Assert required attributes** — `ax_group`, `consumer_group`, `server_type`, `uuid`, `local_mgmt_ip`, credentials.
2. **Register the Qpid server** — `POST /v1/analytics/groups/ax/{ax_group}/servers?uuid={uuid}&type={server_type}`.
3. **Add Qpid to the consumer group** — `POST /v1/analytics/groups/ax/{ax_group}/consumer-groups/{consumer_group}/consumers?uuid={uuid}`.

---

## Role variables (selected)

| Variable | Purpose |
|----------|---------|
| `ax_group` | The analytics group name (created by `apigee-opdk-setup-analytics-group-add`) |
| `consumer_group` | The consumer group name (created by `apigee-opdk-setup-analytics-group-add`) |
| `local_mgmt_ip` | Management Server IP |
| `opdk_user_email` / `opdk_user_pass` | MS API credentials |

---

## Provenance

Authored and maintained by **Carlos Frias** during his tenure on Apigee Edge Private Cloud. One of the analytics-topology roles in the `apigee-opdk-*` corpus.

Contributions welcome — see [CONTRIBUTING.md](./CONTRIBUTING.md).

## License

See [LICENSE](./LICENSE).