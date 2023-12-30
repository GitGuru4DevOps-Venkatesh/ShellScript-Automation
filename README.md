# docker-Java-kubernetes-project
Deploying Java Applications with Docker and Kubernetes

Create a shell script to automate these steps. Below is an example of a simple shell script that combines the described steps. Save this script with a `.sh` extension, and make it executable using the `chmod +x script_name.sh` command or use this one also chmod 777 script_name.sh` command. Then, you can run it using `./script_name.sh`.

```bash
#!/bin/bash

# Set your repository URLs
source_repo_url="https://github.com/yourusername/source-repo.git"
new_repo_url="https://github.com/yourusername/new-repo.git"

# Clone source code from GitHub to local
git clone "$source_repo_url"

# Create a new repository on GitHub
# (You may need to replace 'YourAccessToken' with a valid GitHub access token)
curl -u "YourAccessToken:x-oauth-basic" https://api.github.com/user/repos -d '{"name":"new-repo"}'

# Clone the newly created repository
git clone "$new_repo_url"

# Switch to the previously cloned repository
cd source-repo

# Copy source code to the newly created repository
cp -r ./* ../new-repo

# Switch to the new repository
cd ../new-repo

# Commit and push changes
git add .
git commit -m "Copy source code from source-repo"
git push origin main

echo "Script executed successfully!"
```

Note:

Must and should please replace `yourusername`, `source-repo`, `new-repo`, and `YourAccessToken` with your GitHub username, repository names, and a valid GitHub access token.
Make sure to replace `main` with the appropriate branch name if you're using a different branch.

