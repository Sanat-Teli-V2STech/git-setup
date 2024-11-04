# Creating SSH key for Github

1. Generate the SSH Key: Open a terminal and enter the following command. Replace `FirstName-LastName-V2STech` with the username associated with your GitHub account:

```bash
ssh-keygen -t ed25519 -C "FirstName-LastName-V2STech"
```
You’ll be prompted to enter a file location to save the key. Set the default location as `~/.ssh/github`.
Next, enter a passphrase for added security (or leave it blank for no passphrase). 

**Note:** It's completely fine to leave it blank to avoid typing the password again and again for every `push` or `pull`.

2. Copy the SSH Key to Your Clipboard: To copy the public key, use the following command: `cat ~/.ssh/github.pub`

3. Add the SSH Key to Your GitHub Account:
    - Go to this link: [Click Here](https://github.com/settings/keys)
    - Click on *New SSH key*
    - Give your ssh key a title, example: `work-laptop-key`
    - Paste your key which we had copied from **step 4**
    - Click on *Add SSH key* to save.

4. Add config for ssh on laptop, you can simply copy and paste this in your laptop in a terminal: 
```bash
cat <<EOF | tee -a ~/.ssh/config
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/github
    IdentitiesOnly yes
    Port 22
EOF
```
5. Run this to make sure your keys are recognize by shell: 
```bash
eval "$(ssh-agent -s)"
```

6. Test your newly added ssh key:
```bash
ssh -T git@github.com
```

7. Done.

