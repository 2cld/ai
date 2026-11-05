## tmux Best Practices for Wip Sessions

### Named Sessions

```bash
# Create/attach to named session
tmux new-session -A -s wip

# Multiple sessions for different contexts
tmux new-session -A -s wip      # Wip coordination
tmux new-session -A -s dev      # Development work
tmux new-session -A -s ops      # Ops/monitoring
```

### Useful tmux Commands

| Key | Action |
|-----|--------|
| `Ctrl+B d` | Detach (session keeps running) |
| `Ctrl+B c` | New window |
| `Ctrl+B n` | Next window |
| `Ctrl+B p` | Previous window |
| `Ctrl+B "` | Split horizontal |
| `Ctrl+B %` | Split vertical |
| `Ctrl+B [` | Scroll mode (q to exit) |

### Reconnect After Disconnect

```bash
# From any device (phone, laptop, tablet):
ssh nsadmin@10.147.17.176 -t "tmux attach -t wip"

# If session doesn't exist, create it:
ssh nsadmin@10.147.17.176 -t "tmux new-session -A -s wip"
```
