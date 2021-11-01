# lighttpd-external-munin-proxy

lighttpd external.conf for Munin webserver proxy

Simple [lighttpd](https://www.lighttpd.net/) external configuration file a [Munin](https://munin-monitoring.org/) webserver proxy. Works out of the box with the [Pi-hole](https://pi-hole.net/) web client.

# Related projects
* [lighttpd](https://github.com/lighttpd/lighttpd1.4)

lighttpd1.4 on github for easier collaboration - main repo still on lighttpd.net

* [Munin](https://github.com/munin-monitoring/munin)

Main repository for munin master / node / plugins

* [munin-pihole-plugins](https://github.com/saint-lascivious/munin-pihole-plugins)

Munin plugins monitoring [Pi-Hole](https://pi-hole.net)

* [Pi-hole](https://github.com/pi-hole/pi-hole)

A black hole for Internet advertisements

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
alias.url += ( "/munin" => "/var/cache/munin/www/" )

$HTTP["url"] =~ "^/munin" {
    proxy.server = ( "" => ( "host" => "127.0.0.1", "port" => 4948 ) )
}

```

* Restart lighttpd
```
sudo systemctl restart lighttpd
```

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
