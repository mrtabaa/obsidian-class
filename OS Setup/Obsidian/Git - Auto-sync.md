1. Install `Git` plugin [obsidian://show-plugin?id=obsidian-git](obsidian://show-plugin?id=obsidian-git)
# Obsidian Git – SSH Setup (Linux Mint)

2. **Generate SSH key (with passphrase)**
        ```
    ssh-keygen -t ed25519 -C "mrtabaa@gmail.com"
    ```
    
    Press Enter to accept `~/.ssh/id_ed25519`, then set a passphrase.
    
3. **Start agent & add the key**
    
    ```
    eval "$(ssh-agent -s)"
    ssh-add ~/.ssh/id_ed25519
    ```
    
4. **Add the public key to GitHub**
    
    ```
    cat ~/.ssh/id_ed25519.pub
    ```
    
    Copy the output → GitHub **Settings → SSH and GPG keys → New SSH key** → paste → Save.
    
5. **Test SSH to GitHub**
    
    ```
    ssh -T git@github.com
    ```
    
    Type `yes` on first connect; expect a greeting with your username.
    
6. **Point your vault repo to SSH**
    
    ```
    cd /path/to/your/obsidian/vault
    git remote set-url origin git@github.com:YOUR_USER/YOUR_REPO.git
    git remote -v
    ```
    
7. **Use in Obsidian**  
    Open vault → **Obsidian Git** → Pull / Commit / Push.  
    (You may unlock the key once per login session.)
    

---

### Optional: SSH config & permissions

```bash
mkdir -p ~/.ssh && chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_ed25519
```

Create or edit `~/.ssh/config`:

```
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519
  AddKeysToAgent yes
  IdentitiesOnly yes
```
