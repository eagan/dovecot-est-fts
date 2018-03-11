# dovecot-est-fts
Full-Text-Search for [Dovecot](https://www.dovecot.org/) mailbox with [Hyper Estraier](http://fallabs.com/hyperestraier/)

## Building index
### dovecot-est-gatherer
`dovecot-est-gatherer /path/to/casket /path/to/dovecot-uidlist ...`

Shell script dovecot-est-gatherer doesn't scan directories by itself,
but reads [dovecot-uidlist](https://wiki2.dovecot.org/MailboxFormat/Maildir)
to get IMAP UID / filename mapping.
Current version may fail to get some of mailfiles,
because suffixes of file names, they stand for flags,
are reflected to dovecot-uidlist asynchronously.

Core part to build index is done by `estcmd gather -fm`.
IMAP UIDs are embeded into the index as the field `imap-uid`.
