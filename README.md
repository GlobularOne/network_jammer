# network_jammer

network_jammer is a tool to jam a network, disallowing access for everyone or ensuring exclusive access for some. It does so with sending deauthentication packets to discovered clients.

## Features

 - Automatic client discovery

 - Allowing exclusions from jamming

 - Lightweight


## Installation

Clone the repository:

```sh
git clone https://github.com/GlobularOne/network_jammer.git
```

Ensure you have a wireless adapter that supports monitor mode, install aircrack-ng.

## Usage

First of all, ensure you have a good signal strength as it will help in discovering clients of the target AP. Get ESSID, BSSID and channel information from output of airodump-ng (channel is CH in airodump's output). Also if you want to exclude certain devices, get their MAC addresses too. And run the program with root permissions, an example could be:

```sh
sudo ./jam_network --bssid "XX:XX:XX:XX:XX:XX" --essid "My network" --channel 3
```

If for whatever reason you would want to avoid deauthenticating broadcast, add `--no-broadcast-deauth`.

If we were to exclude a device, we would use `--exclude`:

```sh
sudo ./jam_network --bssid "XX:XX:XX:XX:XX:XX" --essid "My network" --channel 3 --exclude "XX:XX:XX:XX:XX:XX"
```

Exclude flag can be passed several times to exclude several MAC addresses:

```sh
sudo ./jam_network --bssid "XX:XX:XX:XX:XX:XX" --essid "My network" --channel 3 --exclude "XX:XX:XX:XX:XX:XX" --exclude "XX:XX:XX:XX:XX:XX"
```

Note that excluding any device will automatically disable broadcast deauthentication.

## Disclaimer

This project is a PoC (Proof of Concept). It must only be used where consent is granted to do so. We (the project development team) do not encourage or endorse any illegal activities.

## Contacting the author

You can always send an email to me. I am available as `GlobularOne@proton.me`.

## License

Apache Software License 2.0. See the [LICENSE](https://github.com/GlobularOne/network_jammer/blob/main/LICENSE) file for more information.

