# Linux Practice – Processes and Services

## 1. Process Checks

### View Running Processes

```bash
ps aux
```

**Observation:** Displays all running processes with CPU and memory usage.

### Monitor Processes in Real Time

```bash
top
```

**Observation:** Shows live CPU, memory, and process activity.

---

## 2. Service Checks

### Check Docker Service Status

```bash
systemctl status docker
```

**Observation:** Docker service is active and running.

### View Running Services

```bash
systemctl list-units --type=service
```

**Observation:** Displays all active services managed by systemd.

---

## 3. Log Checks

### View Docker Logs

```bash
journalctl -u docker -n 20
```

**Observation:** Shows the last 20 Docker service log entries.

### View Recent System Logs

```bash
journalctl -xe
```

**Observation:** Displays recent system events and errors.

---

## 4. Mini Troubleshooting Flow

### Scenario: Verify Docker Health

1. Check service status

```bash
systemctl status docker
```

2. Check Docker logs

```bash
journalctl -u docker
```

3. Verify Docker process

```bash
ps aux | grep dockerd
```

4. Restart service if needed

```bash
sudo systemctl restart docker
```

5. Confirm service is running

```bash
systemctl status docker
```

---

## Key Learnings

* `ps` and `top` are used to inspect processes.
* `systemctl` is used to manage services.
* `journalctl` is used to view logs.
* A service can create one or more processes.
* Checking service status → logs → processes is a common troubleshooting workflow.
