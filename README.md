# lighttpd-external-munin-proxy

lighttpd external.conf for Munin webserver proxy

Simple [lighttpd](https://www.lighttpd.net/) external configuration file a [Munin](https://munin-monitoring.org/) webserver proxy. Works out of the box with the [Pi-hole](https://pi-hole.net/) web client.

## Related projects
* [lighttpd](https://github.com/lighttpd/lighttpd1.4)

lighttpd1.4 on github for easier collaboration - main repo still on lighttpd.net

* [Munin](https://github.com/munin-monitoring/munin)

Main repository for munin master / node / plugins

* [munin-pihole-plugins](https://github.com/saint-lascivious/munin-pihole-plugins)

Munin plugins monitoring [Pi-Hole](https://pi-hole.net)

* [munin-unbound-plugins](https://github.com/saint-lascivious/munin-unbound-plugins)

Munin plugins monitoring [Unbound](https://github.com/NLnetLabs/unbound)

Unbound is a validating, recursive, caching DNS resolver.

## Usage
* Install Munin
```
sudo apt install munin munin-node
```

* Download the lighttpd external.conf file
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/lighttpd-external-munin-proxy/master/etc/lighttpd/external.conf -P /etc/lighttpd
```

* Or edit your existing lighttpd external.conf to include:
```
# Munin
server.modules += ( "mod_alias", "mod_rewrite" )

alias.url += ( "/munin-static" => "/etc/munin/static" )
alias.url += ( "/munin"        => "/var/cache/munin/www/" )

fastcgi.server += ("/munin-cgi/munin-cgi-graph" =>
                   (( "socket"      => "/var/run/lighttpd/munin-cgi-graph.sock",
                      "bin-path"    => "/usr/lib/munin/cgi/munin-cgi-graph",
                      "check-local" => "disable",
                   )),
                  "/munin-cgi/munin-cgi-html" =>
                   (( "socket"      => "/var/run/lighttpd/munin-cgi-html.sock",
                      "bin-path"    => "/usr/lib/munin/cgi/munin-cgi-html",
                      "check-local" => "disable",
                   ))
                 )

url.rewrite-repeat += (
                   "/munin/(.*)" => "/munin-cgi/munin-cgi-html/$1",
                   "/munin-cgi/munin-cgi-html$" => "/munin-cgi/munin-cgi-html/",
                   "/munin-cgi/munin-cgi-html/static/(.*)" => "/munin-static/$1"
                   )
```

* Edit /etc/munin/munin.conf
Ensure your `/etc/munin/munin.conf` file has the following values set:
```
graph_strategy=cgi
html_strategy=cgi
```

* Restart services
```
sudo systemctl restart lighttpd munin
```

## Help! My graphs aren't showing up!

* Be patient

Graphs should be generated at five minute intervals. If you still do not see graphs after this time, try restarting the machine and waiting a further five minutes. If you still can not get any graphs to display, contact me for further support.

## Contact
* Discord
[SaintLascivious](https://discord.gg/NC7taVyn)

* Email
saint@sainternet.xyz

* IRC
[##saint-lascivious](https://webchat.freenode.net/##saint-lascivious)

* Reddit
[saint-lascivious](https://www.reddit.com/user/saint-lascivious)

![alt text][logo]

[logo]:https://vignette.wikia.nocookie.net/pokemon/images/7/76/265Wurmple.png "Using the spikes on its rear end, Wurmple peels the bark off trees and feeds on the sap that oozes out. This Pokémon's feet are tipped with suction pads that allow it to cling to glass without slipping."
