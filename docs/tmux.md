## tmux Best Practices for Wip Sessions
- https://tmuxcheatsheet.com/
- https://github.com/tmux/tmux/wiki/Getting-Started

### Named Sessions

```bash
# List all tmux sessions
tmux ls

# Attach to mysession
tmux a -t mysession

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
| `Ctrl+B d` | Detach (session keeps running) |**,**
| `Ctrl+B w` | Window list of all sessions |
| `Ctrl+B &` | kill current window |
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

---
---
## Issue with Mac 
Ah, the triple-layer nesting! Because you are on a Mac, remoted into Windows, and SSH'ing into Linux, macOS is intercepting the Ctrl + Arrow Key combination first because it is a global Mac shortcut used for "Mission Control" (switching virtual desktops).
To fix this, you have two options: either bypass the arrow keys entirely using standard tmux command lines, or use a specific tmux shortcut that changes layout sizes instantly.

Solution 1: Use the Command Line (No Arrow Keys)

This bypasses macOS completely by using text commands.
1. Press Ctrl + b
2. Type : (this opens the tmux command prompt at the bottom of your screen)
3. Type one of the following commands and hit Enter:
	- Resize Up: resize-pane -U 10
	- Resize Down: resize-pane -D 10
	- Resize Left: resize-pane -L 10
	- Resize Right: resize-pane -R 10
(You can change the number 10 to adjust how many rows/columns you want to move it by).

Solution 2: Use Built-in Presets

If you just want tmux to instantly balance your screen out evenly without fighting your keyboard layout, you can use these default layout keys:
- Evenly space columns: Ctrl + b, then Alt + 1
- Evenly space rows: Ctrl + b, then Alt + 2
- Cycle through other default layouts: Ctrl + b, then Spacebar

Solution 3: Disable the Mac Shortcut (Optional)

If you want your normal terminal arrow shortcuts to work, you can turn off the macOS shortcut that is getting in the way:
1. On your Mac, open System Settings > Keyboard > Keyboard Shortcuts.
2. Click Mission Control on the left.
3. Uncheck Move left a space and Move right a space (which use Ctrl + ◀ / ▶).
Are you trying to make a specific pane larger for editing code, or just trying to clear up a cramped screen? I can help you map custom letters (like H, J, K, L) to resize panes instead so you never have to use arrow keys again.

---
---
## Mouse to control pane
You can resize panes in tmux using either keyboard shortcuts or your mouse.

Method 1: The Standard Keyboard Shortcuts

To resize, you press your prefix key (Ctrl + b), release it, and then hold down the Ctrl key while tapping the arrow keys.
- Expand Up: Ctrl + b, then hold Ctrl + ▲
- Expand Down: Ctrl + b, then hold Ctrl + ▼
- Expand Left: Ctrl + b, then hold Ctrl + ◀
- Expand Right: Ctrl + b, then hold Ctrl + ▶
Note: Tapping the arrow key moves it by 1 cell. Keep tapping the arrow key while holding Ctrl to continuously resize.

Method 2: Temporary Full-Screen (Zoom)

If you just need a pane to be bigger temporarily to read a lot of text, you can "zoom" it to fill the entire window, and then shrink it back down when you are done.
- Toggle Zoom In / Out: Ctrl + b, then z

Method 3: Enable the Mouse (Highly Recommended)

If you want to simply click and drag the borders of your panes with your mouse, you can turn on mouse mode.
1. Press Ctrl + b, then type : to open the tmux command line at the bottom of the screen.
2. Type set -g mouse on and hit Enter.
(To make this change permanent so it works every time you open tmux, add set -g mouse on to your ~/.tmux.conf file).
Would you like to know how to create a configuration file so your mouse and custom shortcuts work automatically every time you start tmux?

