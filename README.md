nginx-munin
===========

Munin plugin for Nginx.

With simple and straight specifications.
I am not interested in instantaneous Requests/sec value measured by only 1 sec,
but I am interested in average Requests/sec value from whole measuring period.

#### Graph Fields

* Requests/sec
* Accepted connections/sec
* Handled connections/sec
* Active connections
* Reading connections
* Writing connections
* Keep-Alive connections

#### Graph Types

1. `default`
  * Only Requests/sec, Accepted connections/sec, Active connections and Keep-Alive connections values in one graph
2. `request`
  * Only Requests/sec values in one graph
3. `connection`
  * Only Active, Reading, Writing and Keep-Alive connections values in one graph
4. `all`
  * All status values in one graph

Graph type is specified by tail of filename. 

#### Setting Examples

ex1. Default status values in one graph.
```
# cp nginx_status /usr/share/munin/plugins/nginx_status
# ln -s /usr/share/munin/plugins/nginx_status /etc/munin/plugins/nginx_status_default
```

ex2. Only Requests/sec values in one graph.
```
# cp nginx_status /usr/share/munin/plugins/nginx_status
# ln -s /usr/share/munin/plugins/nginx_status /etc/munin/plugins/nginx_status_request
```

ex3. Only Active, Reading, Writing and Waiting values in one graph.
```
# cp nginx_status /usr/share/munin/plugins/nginx_status
# ln -s /usr/share/munin/plugins/nginx_status /etc/munin/plugins/nginx_status_connection
```

ex4. All status values in one graph.
```
# cp nginx_status /usr/share/munin/plugins/nginx_status
# ln -s /usr/share/munin/plugins/nginx_status /etc/munin/plugins/nginx_status_all
```

#### Remote Nginx Server Setting

Set `nginx_status_url` environment variable to nginx_status page URL.
```
# echo '[nginx_status*]' >> /etc/munin/plugin-conf.d/nginx_status
# echo 'env.nginx_status_url http://remote_server/nginx_status' >> /etc/munin/plugin-conf.d/nginx_status
```

Default value is `http://localhost/nginx_status`.
