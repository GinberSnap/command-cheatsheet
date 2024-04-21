# Miscellaneous

#### Fix  libcrypto.so.1.1 issue

```
wget http://nz2.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1f-1ubuntu2_amd64.deb
sudo dpkg -i libssl1.1_1.1.1f-1ubuntu2_amd64.deb
```

```
find / -name libssl.so.1.1
```

[OpenSSL download link](https://www.openssl.org/source/)

[Source](https://stackoverflow.com/questions/72133316/libssl-so-1-1-cannot-open-shared-object-file-no-such-file-or-directory)


` 2>/dev/null` to exclude files that have errors or permission denied when using `find` command. 
