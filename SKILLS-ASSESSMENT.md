# Skills Assessment — apigee-opdk-setup-qpid-add

> **Skill domain:** Apigee analytics topology modeling — adding a Qpid consumer to an existing analytics group (OPDK). Part of the broader Apigee platform-operations portfolio; see the [`bap_coe` portfolio hub →](https://github.com/carlosfrias/apigee-hybrid-workspace/blob/master/SKILLS-ASSESSMENT.md) for the cloud-native (Hybrid/K8s) counterpart and the full corpus.

---

## Why this role is notable

- **Analytics consumer registration.** Registers the Qpid server with the Management Server, then adds it to the consumer group — the second step in the analytics topology lifecycle after axgroup creation.
- **Composed lifecycle.** This role runs after `apigee-opdk-setup-analytics-group-add` (axgroup + consumer group creation) and before `apigee-opdk-setup-postgres-add` (datastore addition) and `apigee-opdk-setup-scopes-add` (scope binding). The analytics topology is built incrementally, role by role, in dependency order.

---

## Expertise demonstrated

> Ansible is the medium. The engineering evidence lives in the [project README →](README.md). What follows is the skills assessment for the business reader.

- **Apigee analytics topology modeling** — Qpid as a consumer in the `axgroup → consumer-group → {consumers, datastores} + {scopes}` directed object graph. The role is a focused step in the lifecycle.
- **MS REST API choreography** — register the server, then add it to the consumer group. Two sequential POSTs with attribute assertion as a gate.
- **Composable role architecture** — this role is designed to be composed into larger provisioning runbooks via `requirements.yml`, not run in isolation.

---

## How this shows the expertise

This role is the Qpid addition step in the analytics topology lifecycle. It is not notable in isolation — it is notable because it is part of a composable sequence: `analytics-group-add` → `qpid-add` → `postgres-add` → `scopes-add`. Each role is a focused, testable unit that adds one element to the directed object graph. The expertise is in the decomposition: each role owns one API interaction, and the composition builds the topology.

---

## Related expertise

| Skill | Repository | Assessment |
|-------|-----------|-----------|
| Analytics (axgroup) lifecycle | [`apigee-opdk-setup-analytics-group-add`](https://github.com/carlosfrias/apigee-opdk-setup-analytics-group-add) | [SKILLS-ASSESSMENT.md →](https://github.com/carlosfrias/apigee-opdk-setup-analytics-group-add/blob/master/SKILLS-ASSESSMENT.md) ✅ |
| Postgres datastore addition | [`apigee-opdk-setup-postgres-add`](https://github.com/carlosfrias/apigee-opdk-setup-postgres-add) | [SKILLS-ASSESSMENT.md →](https://github.com/carlosfrias/apigee-opdk-setup-postgres-add/blob/master/SKILLS-ASSESSMENT.md) ✅ |
| Scope binding (org/env) | [`apigee-opdk-setup-scopes-add`](https://github.com/carlosfrias/apigee-opdk-setup-scopes-add) | [SKILLS-ASSESSMENT.md →](https://github.com/carlosfrias/apigee-opdk-setup-scopes-add/blob/master/SKILLS-ASSESSMENT.md) ✅ |
| Cloud-native (Hybrid/K8s) counterpart | [`apigee-hybrid-workspace`](https://github.com/carlosfrias/apigee-hybrid-workspace) | [SKILLS-ASSESSMENT.md →](https://github.com/carlosfrias/apigee-hybrid-workspace/blob/master/SKILLS-ASSESSMENT.md) ✅ portfolio hub |

---

## Provenance

Authored and maintained by **Carlos Frias** during his tenure on Apigee Edge Private Cloud. This skills assessment is the companion to the engineering [README →](README.md).

## License

See [LICENSE](./LICENSE).