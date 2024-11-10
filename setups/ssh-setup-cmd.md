# SSH (Command Prompt)
1. Check for existing ssh key:
```
    dir %userprofile%\.ssh
```

2. Generate new SSH key:
```
    ssh-keygen -t ed25519 -C "your_email@example.com"
```
   - Press enter 3x to use defaults
  
3. Start the SSH-agent to manange keys:
```
    start-ssh-agent.cmd
```

4. Copy public key and add to **remote** git personal settings:
```
    type %userprofile%\.ssh\id_ed25519.pub
```

5. Test SSH connection:
```
    ssh -T git@github.com
```