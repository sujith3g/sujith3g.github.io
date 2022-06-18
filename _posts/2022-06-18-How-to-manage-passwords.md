---
layout: post
comments: true
title: How to manage passwords
---

In recent times, an individual's usage of multiple online platforms or services has increased exponentially.
More often than not, we end up using the "Forgot Password" feature,
which becomes a tedious process, especially when we have to do it over
and over again. I was looking for a safe and secure way to store and manage
these passwords.

Recently I came across this open source password manager
['pass'](https://www.passwordstore.org/). It is using [GPG](https://en.wikipedia.org/wiki/GNU_Privacy_Guard) encrypted files to store passwords. And pass allows me to connect it with a git repo to keep a track of it and to save it in a central location.

pass can use your existing GPG key for encryption or it can generate one
for you. If you don't have a GPG key, follow
[this](https://www.redhat.com/sysadmin/creating-gpg-keypairs) to create one.

- **Install pass**

    Use your favourite package manager to install pass,

    from MacOS `brew install pass`

    or from Ubuntu/Debian `sudo apt-get install pass`.

- **Use existing GPG key with pass**

    Initialise pass with your GPG key `pass init "<your GPG key ID>"`.

- **Adding your first password to pass**

    Use insert command to add new password.

    `pass insert email/hotmail`

- **Reading password from pass**

    Just use `pass` command to get a list of your passwords.

    and use `pass <path to a specific password>` to see a specific password. You can also
get one password into clipboard using `pass -c email/hotmail`

- **Integrate with a git repo and track your passwords**

    Create a git repo(preferably private) in one of the git repo hosting provider (GitHub/BitBucket/Gitlab), may be the one less exposed to other apps and integrations for security reasons.

    Now use `pass git init` to initialize git repository for pass, and add
the git repo url to pass using `pass git remote add origin <repo URL>`.
Now pass creates a git commit for each change you make to your passwords.


### Next steps

pass is available in mobile devices as well. I use the community
maintained Android app [Android-Password-Store](https://github.com/zeapo/Android-Password-Store#readme).
You can use [Paperkey](https://en.wikipedia.org/wiki/Paper_key) to get your GPG key printed on a paper, and use it
when you have lost access to your computer, to restore it to a new device.


