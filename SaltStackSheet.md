# SaltStack Quick Reference

## Salt Master

### View all Keys

    salt-key --list-all

### Accept Specific Key

    salt-key --accept=<key>

### Accept all Keys

    salt-key --accept-all

### Send a Command

    salt '*' test.ping

### Run an SSH Command

    salt '*' cmd.run "ln -l"

### Apply a State

    salt '*' state.apply vim

## Salt Minion

### 