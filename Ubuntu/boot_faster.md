# Boot Faster

## Systemctl Processes

Check the services that take the most time to start.
In my case lxd service was taking 8.5 seconds.
I can start this service manually whenever I need it. It don't need to start at every boot.

```bash
~> systemd-analyze blame  # Shows services taking the longest time
~> systemctl disable lxd  # Stops the service to start automatically
~> systemd-analyze        # Shows a boot time summary
~> systemd-analyze critical-chain # Shows the critical chain and what is waisting time on
```

## Boot errors

Next step is to check the boot log for errors.

```bash
journalctl -b -p err   # Show errors from last boot
```
See if the any errors are retrying or waiting a long time before quitting.