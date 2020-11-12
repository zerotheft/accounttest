# accounttest
This repo is here specifically for invited team members to test proper multi-account setup.

## How to Set Up

Info taken from [this gist](https://gist.github.com/Jonalogy/54091c98946cfe4f8cdab2bea79430f9)

### Create a new ssh key for your anonymous account

```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

Save it to a specific rsa file like `id_rsa_anonacct`

### Add the key to your anonymous GitHub account

Go to GitHub and log in as your anonymous account.

Go to account Settings, and choose `SSH and GPG keys`.

Get your anonymous public key into the clipboard:

```
pbcopy < ~/.ssh/id_rsa_anonacct.pub
```

(or `cat ~/.ssh/id_rsa_anonacct.pub` and then highlight and copy)

And then copy it into a new SSH key for your GitHub account and save it.

### Create a new SSH config for the anonymous git account

Edit your ssh config file (typically `~/.ssh/config`) to include a block for your anonymous github account:

```
#github ZT account
Host github.com-anonacct
   HostName github.com
   User git
   IdentityFile ~/.ssh/id_rsa_anonacct
   IdentitiesOnly yes
```

### Clone the repo

Go to GitHub and get the ssh path to clone the repo.  This will give you an url like:

```
git@github.com:zerotheft/accounttest.git
```

This needs to be edited to replace the `github.com` to the anonymous host `github.com-anonact`, and then clone it:

```
git clone git@github.com-anonacct:zerotheft/accounttest.git
```

(If you set up your SSH key properly this will work.  If not fix the SSH key setup in GitHub.)

### Update your local repo's name and email

You need to override the git config for this repo to get the right user name and email.
`cd` into the repo and then run the following (changing user name and email, of course):

```
git config user.name "anonymous name"
git config user.email anonymousacct@example.com
```

### Confirm the config

Test your local repo's config, so in that repo run:

```
git config --list
```

You should see that the repo is set to the anonymous host, and you will see your local username and email.
Note that you will also likely see your global username and email first, as the later (local) ones override these.




## Confirmed accounts

Add your name to the list below to create a chance to commit and push.

- rigellian34
- Bryan was here
- testing from IntelliJ Idea
- testing from Atom IDE
