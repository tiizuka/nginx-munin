nginx-munin
===========

Munin plugin for Nginx

#### Graph Fields

* Active connections
* Accepted connections/sec
* Handled connections/sec
* Requests/sec
* Reading connections
* Writing connections
* Waiting connections

#### Graph Type

1. `all`
  * All status values in one graph
2. `request`
  * Only Requests/sec values in one graph
3. `connection`
  * Only Active, Reading, Writing and Waiting connections values in one graph

#### Setting Examples

ex1. All status values in one graph
```
# cp nginx_status /usr/share/munin/plugins/nginx_status
# ln -s /usr/share/munin/plugins/nginx_status /etc/munin/plugins/nginx_status_all
```

ex2. Only Requests/sec values in one graph
```
# cp nginx_status /usr/share/munin/plugins/nginx_status
# ln -s /usr/share/munin/plugins/nginx_status /etc/munin/plugins/nginx_status_request
```

ex3. Only Active, Reading, Writing and Waiting values in one graph
```
# cp nginx_status /usr/share/munin/plugins/nginx_status
# ln -s /usr/share/munin/plugins/nginx_status /etc/munin/plugins/nginx_status_connection
```

#### Remote Nginx Server Setting

Set `nginx_status_url` environment variable to nginx_status page URL.
```
# echo '[nginx_status*]' >> /etc/munin/plugin-conf.d/nginx_status
# echo 'env.nginx_status_url http://remote_server/nginx_status' >> /etc/munin/plugin-conf.d/nginx_status
```
