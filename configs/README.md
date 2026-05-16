# Configuration Files

Reusable configuration files referenced by the main tutorial.

## Files

| File | Destination on the host | Purpose |
|------|--------------------------|---------|
| [`cyclonedds.xml`](cyclonedds.xml) | `~/.ros/cyclonedds.xml` | CycloneDDS network interfaces and buffer settings |
| [`10-cyclone-max.conf`](10-cyclone-max.conf) | `/etc/sysctl.d/10-cyclone-max.conf` | Kernel UDP buffer tuning (persistent across reboots) |

## Quick install

```bash
# 1. CycloneDDS configuration
mkdir -p ~/.ros
cp configs/cyclonedds.xml ~/.ros/cyclonedds.xml
# Then edit ~/.ros/cyclonedds.xml to replace enp4s0 and wlp3s0
# with your actual interface names (see `ip -br link show`).

# 2. Kernel buffer tuning
sudo cp configs/10-cyclone-max.conf /etc/sysctl.d/10-cyclone-max.conf
sudo sysctl -p /etc/sysctl.d/10-cyclone-max.conf

# 3. Activate CycloneDDS — add to ~/.bashrc:
#    export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp
#    export CYCLONEDDS_URI=file://$HOME/.ros/cyclonedds.xml
```

For the full step-by-step explanation, see the [main README](../README.md).
