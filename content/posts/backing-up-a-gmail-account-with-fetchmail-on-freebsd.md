+++
title = "Backing Up a Gmail Account With Fetchmail on FreeBSD"
authors = ["ludo"]
description = ""
tags = []
date = "2011-10-17T10:00:00"
+++

**Gmail is awesome. But I do not want Gmail to be the only location where all my important emails are stored. For this reason I use `fetchmail` to automatically archive any emails sent to my Gmail account on my own FreeBSD server. This guide describes how I currently have this set up.**

## Ingredients

* FreeBSD 8.2
* Fetchmail 6.3.20

## Installing Required Packages

If you haven't already, install the `fetchmail` port with the following commands.

    $ cd /usr/ports/mail/fetchmail
    $ make install clean

We also need to install the `ca_root_nss` port. This port contains all root certificates from certificate authorities included in Mozilla applications (i.e. Firefox and Thunderbird).

    $ cd /usr/ports/security/ca_root_nss
    $ make install clean

## Configuring

First, make sure that you have POP access to your Gmail account enabled. This can be done from the Gmail settings page, under the tab ‘Forwarding and POP/IMAP’.

![](gmail_settings.png)

Next, calculate the MD5 fingerprint for the <tt>pop.gmail.com</tt> certificate. Whenever Google makes a change to the certificate this fingerprint has to be recalculated and updated in the fetchmail configuration.

    $ echo -n |
      openssl s_client -connect pop.gmail.com:995 |
      sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' |
      openssl x509 -noout -fingerprint -md5 |
      cut -d '=' -f 2

Customize the following snippet and place it in `~/.fetchmailrc`.

    poll pop.gmail.com protocol pop3 with interval 3:
      user "<your Gmail address>" pass "<your Gmail password>"
      options keep ssl sslfingerprint "<actual MD5 fingerprint>"
      mda "/usr/bin/procmail -d %T"

## Testing

That should be all, now we can test our configuration.

    $ fetchmail -d0 -v pop.gmail.com

If everything is set up correctly then the output should look something like this:

    fetchmail: 6.3.20 querying pop.gmail.com (protocol POP3) at Sun Oct 16 19:25:01 2011: poll started
    Trying to connect to 209.85.227.109/995...connected.
    fetchmail: Server certificate:
    ...
    fetchmail: POP3> QUIT
    fetchmail: POP3< +OK Farewell.
    fetchmail: 6.3.20 querying pop.gmail.com (protocol POP3) at Sun Oct 16 19:25:02 2011: poll completed