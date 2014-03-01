# Zooconf

Zooconf keeps your configuration files in sync with [Zookeeper][zookeeper]. It
subscribes to your keys in Zookeeper. When they change, Zookeeper notifies the
Zooconf process which creates a new configuration file from your template and
reloads the process.

This project is inspired by [confd][confd] for [etcd][etcd].

## Configuration

Zooconf is managed by a JSON configuration file:

```json
{
  "prefix": "/etc/zooconf/",
  "nodes": [
    "localhost:2181"
  ]
}
```

## Resources

A resource is defined in `/etc/zooconf/zooconf.d/` (`<prefix>/zooconf.d`).

```json
{
  "src":    "template.conf.templ",
  "dest":   "/etc/nginx/nginx.conf",
  "paths": [
    "/conf/nginx"
  ],
  "reload": "/usr/sbin/service nginx restart"
}
```

[etcd]:  https://github.com/coreos/etcd
[confd]: https://github.com/kelseyhightower/confd
[zookeeper]: http://zookeeper.apache.org
