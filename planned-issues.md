# Planned Issues (paste each into a new GitHub Issue)

---

### Convert Docker stack to version-controlled docker-compose.yml

**Description**
Currently the Docker stack (Nextcloud, MariaDB, Jellyfin, Pi-hole, Watchtower, Tailscale) is managed manually. Consolidate all services into a single `docker-compose.yml`, committed to this repo, so the entire stack is reproducible from source instead of relying on manual `docker run` history.

**Acceptance criteria**
- [ ] All current services defined in `docker-compose.yml`
- [ ] Environment variables/secrets externalized to `.env` (not committed)
- [ ] Stack can be torn down and rebuilt from the compose file alone
- [ ] README updated to reference the compose file as the source of truth

---

### Write Ansible playbook for base server provisioning

**Description**
Server hardening (UFW rules, Fail2Ban config, SSH key-only setup) was done manually. Write an Ansible playbook that reproduces this configuration from a clean Ubuntu install, so the security posture is defined as code, not tribal knowledge.

**Acceptance criteria**
- [ ] Playbook configures UFW default-deny + required ports
- [ ] Playbook installs and configures Fail2Ban
- [ ] Playbook disables SSH password auth, enforces key-only
- [ ] Tested against a clean VM or spare hardware
- [ ] Documented in `docs/provisioning.md`

---

### Document Sunshine/Moonlight setup and use case

**Description**
Sunshine (host) + Moonlight (client) are running for remote game streaming but aren't documented anywhere in the repo yet. Write it up.

**Acceptance criteria**
- [ ] `docs/sunshine-moonlight.md` covers setup, network requirements, and how it fits alongside Tailscale
- [ ] Linked from the main README

---

### Write up Pi-hole local DNS configuration

**Description**
Pi-hole is handling local DNS resolution in addition to ad-blocking, but the configuration isn't documented. Write up how local DNS entries are configured and why.

**Acceptance criteria**
- [ ] `docs/pihole-local-dns.md` explains local DNS record setup
- [ ] Linked from the main README

---

### Add a monitoring stack (Uptime Kuma or Prometheus + Grafana)

**Description**
There's currently no automated way to know if a service goes down other than noticing manually. Add a lightweight monitoring stack to track uptime/health of each container and the host itself.

**Acceptance criteria**
- [ ] Monitoring service deployed (Uptime Kuma for simplicity, or Prometheus + Grafana for more depth)
- [ ] All current services being monitored
- [ ] Basic alerting configured (even just a Discord/email webhook on downtime)
- [ ] Documented in `docs/monitoring.md`

---

### Add automated backup verification

**Description**
ZFS scrubs catch silent corruption, but there's no tested process for actually restoring from backup. Add a documented, periodically-tested backup/restore procedure.

**Acceptance criteria**
- [ ] Backup process documented end-to-end
- [ ] Restore procedure actually tested at least once, with results recorded
- [ ] Findings written up in `docs/backup-verification.md`

---

### Add resource usage limits to Docker containers

**Description**
Containers currently run without CPU/memory limits, risking one service starving the others under load. Add resource constraints to the compose file.

**Acceptance criteria**
- [ ] CPU/memory limits set per service based on observed usage
- [ ] Documented rationale for chosen limits

---

### Automate DVD/CD ripping metadata tagging

**Description**
DVD/CD ripping via MakeMKV + HandBrake is manual, including metadata tagging for Jellyfin. Look into automating metadata lookup/tagging as part of the pipeline.

**Acceptance criteria**
- [ ] Metadata tagging step automated or semi-automated (e.g. via a script hooked into the existing pipeline)
- [ ] Pipeline doc updated to reflect the new step
