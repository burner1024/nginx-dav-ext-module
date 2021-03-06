## NGINX WebDAV missing commands support (PROPFIND & OPTIONS)

For full WebDAV support in NGINX you need to turn on standard NGINX
WebDAV module (providing partial WebDAV implementation) as well as
this module for missing methods:
```
./configure --with-http_dav_module --add-module=<path-to-this-module>
```

### Build requirements: libexpat-dev (aka expat-devel)

### Example config
```
location / {
  dav_methods PUT DELETE MKCOL COPY MOVE;
  dav_ext_methods PROPFIND OPTIONS;
  root /var/root/;
}
```

### Centos 7 (x64) yum repo
```
cd /etc/yum.repos.d
sed -i '/\[epel\]/a exclude=nginx' epel.repo
wget http://yum.devopsx.com/devopsx.repo
yum install nginx
```
