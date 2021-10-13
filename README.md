# lighttpd-external-munin-proxy

lighttpd external.conf for Munin webserver proxy

Simple [lighttpd](https://www.lighttpd.net/) external configuration file a [Munin](https://munin-monitoring.org/) webserver proxy. Works out of the box with the [Pi-hole](https://pi-hole.net/) web client.

# Related projects
* [lighttpd](https://github.com/lighttpd/lighttpd1.4)

lighttpd1.4 on github for easier collaboration - main repo still on lighttpd.net

* [Munin](https://github.com/munin-monitoring/munin)

Main repository for munin master / node / plugins

* [MuninPiholePlugins](https://github.com/Rauks/MuninPiholePlugins)

Munin plugins monitoring [Pi-Hole](https://pi-hole.net)

* [Pi-hole](https://github.com/pi-hole/pi-hole)

A black hole for Internet advertisements

## Usage
* Install Munin
```
sudo apt install munin munin-node
```

* Switch to the lighttpd directory
```
cd /etc/lighttpd/
```

* Download the config file
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/lighttpd-external-munin-proxy/master/etc/lighttpd/external.conf
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
