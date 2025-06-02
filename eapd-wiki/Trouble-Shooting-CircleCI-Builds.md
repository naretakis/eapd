One of the easiest ways to troubleshoot a failed build is to SSH the CircleCI container. CircleCI uses the same SSH key that GitHub uses.

## Generate Key in GitHub
1. Go into your personal settings 
2. Choose SSH and GPG Keys
3. Click New SSH Key
4. Add the Title and the [Key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

## Add Key to CircleCI
1. Go to CircleCI and change from All Projects to eAPD
2. Click Project Settings in the top right corner of CircleCI
3. Click SSH Keys
4. Under "Additional SSH Keys" click "Add SSH Key"
5. Leave Hostname blank
6. Paste your Private Key into the box and click "Add SSH Key"

## Enable SSH in CircleCI Build
1. If/When your build fails, click on the failed job
2. Find the Rerun drop down and select "Rerun Job with SSH"
3. It'll restart the build with SSH enabled

## SSHing into CircleCI Container
1. Once the Enable SSH job has finished, expand it and it'll give you SSH instructions
```
You can now SSH into this box if your SSH public key is added:
    $ ssh -p 12345 1.2.3.4
```
2. Copy that command and paste it on the command line, add -i ~/.ssh/yoursshkey
```
    $ ssh -p 12345 1.2.3.4 -i ~/.ssh/yoursshkey
```
You should now be SSHed into the container.  
From the container you can run Linux commands. The container will have the variables already imported. 