


### Notes
If you experience connection issues, such as
> svn: E230001: Unable to connect to a repository at URL 'https://projects.coin-or.org/svn/qpOASES/stable/3.2'
> svn: E230001: Server SSL certificate verification failed: issuer is not trusted

```
# query the svn repo to be asked about the certificate
svn list https://projects.coin-or.org/svn/qpOASES/stable/3.2/
# and choose "accept permanently"
```
