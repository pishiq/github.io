---
layout: post
title:  "Running Mathematica Script via SSH with tmux"
date:   2024-05-18 00:19:50 +1000
categories: jekyll update

---

## Why tmux is Recommended

`tmux` is a powerful yet straightforward solution for running long-running processes on a remote workstation. It offers:

1. **Persistence**: `tmux` sessions persist even if the connection drops, allowing you to reconnect and continue where you left off.
2. **Session Management**: `tmux` provides robust session management, allowing multiple windows and panes within a single SSH connection.
3. **Reattaching Sessions**: It's easy to detach and reattach to `tmux` sessions, which is useful for long-running processes like Mathematica scripts.

## Installing tmux

If `tmux` is not already installed on your workstation, you can install it using your package manager. For example:

- **Ubuntu/Debian**:
  
  ```bash
  sudo apt-get install tmux
  ```

- **CentOS/RHEL**:
  
  ```bash
  sudo yum install tmux
  ```

## Using tmux

1. **Start a `tmux` session**:
   
   ```bash
   tmux
   ```

2. **Run your Mathematica script**:

```bash
math -script file.m
```

3. **Detach from the tmux session**:
   Press `Ctrl-B` followed by `D`. This detaches the session, but the script continues to run.

4. **Log out from the SSH session**:
   You can now safely log out without stopping the script.

5. **Reattach to the `tmux` session**:
   When you log back in via SSH, reattach to your `tmux` session with:

```bash
tmux attach-session -t 0
```

If you have multiple `tmux` sessions, list them with:

```bash
tmux ls
```

Then attach to the desired session by its ID:

```bash
tmux attach-session -t [session_id]
```
