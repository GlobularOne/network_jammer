# network_jammer

network_jammer is a tool to jam a network, disallowing access for everyone or ensuring exclusive access for some. It does so with sending de-authentication packets to discovered clients.

## Features

* Automatic client discovery

* Allowing exclusions from jamming

* Lightweight

* Can target several APs

## Installation

Clone the repository:

```sh
git clone https://github.com/GlobularOne/network_jammer.git
```

Ensure you have a wireless adapter that supports monitor mode, install `aircrack-ng`.

## Usage

First of all, ensure you have a good signal strength as it will help in discovering clients of the target AP. Get ESSID, BSSID and channel information from output of `airodump-ng` (channel is CH in airodump's output). Also if you want to exclude certain devices, get their MAC addresses too. And run the program with root permissions, an example could be:

```sh
sudo ./jam_network wlp2s0 --bssid "XX:XX:XX:XX:XX:XX" --essid "My network" --channel 3
```

If for whatever reason you would want to avoid de-authenticating broadcast, add `--no-broadcast-deauth`. Note that using `--essid` is not required.

You can target several APs:

```sh
sudo ./jam_network wlp2s0 wlp2s1 --bssid "XX:XX:XX:XX:XX:XX" "XX:XX:XX:XX:XX:XX" --essid "My network" "My network 2" --channel 3 12
```

You can work on 5Ghz networks as well:

```sh
sudo ./jam_network wlp2s0 --bssid "XX:XX:XX:XX:XX:XX" "XX:XX:XX:XX:XX:XX" --essid "My network" "My network 2" --channel 3 12 --enable_5ghz
```

If we were to exclude a device, we would use `--exclude`:

```sh
sudo ./jam_network wlp2s0 --bssid "XX:XX:XX:XX:XX:XX" --essid "My network" --channel 3 --exclude "XX:XX:XX:XX:XX:XX"
```

You can also exclude several MAC addresses:

```sh
sudo ./jam_network wlp2s0 --bssid "XX:XX:XX:XX:XX:XX" --essid "My network" --channel 3 --exclude "XX:XX:XX:XX:XX:XX" "XX:XX:XX:XX:XX:XX"
```

Note that excluding any device will automatically disable broadcast de-authentication.

## Disclaimer

This security tool is designed for lawful security testing and research purposes only.
The development team unequivocally condemns any illegal activities or unauthorized access to systems or data.
Misuse of this tool for malicious intent is strictly prohibited.
The creators and contributors of this tool shall not be held responsible for any harm,
damage, or legal repercussions resulting from its misuse by malicious actors.
Users are solely responsible for ensuring compliance with all relevant laws and regulations when utilizing this tool.
By using this tool, you agree to employ it responsibly and ethically.

## Contacting the author

You can always send an email to me. I am available as `GlobularOne@proton.me`.

## License

Apache Software License 2.0. See the [LICENSE](https://github.com/GlobularOne/network_jammer/blob/main/LICENSE) file for more information.
