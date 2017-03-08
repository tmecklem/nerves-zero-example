# Nerves Zero Example

## Targets
Nerves applications are configured that they can produce images for target
hardware by setting `NERVES_TARGET`. By default, if MIX_TARGET is not set, Nerves
defaults to building a host target. This is useful for executing logic tests,
running utilities, and debugging. For more information about targets:
https://hexdocs.pm/nerves/targets.html#content

## Getting Started    

To start your Nerves app:

```
NERVES_TARGET=rpi0 mix deps.get
NERVES_TARGET=rpi0 mix firmware
#Burn to an SD card with 
NERVES_TARGET=rpi0 mix firmware.burn
```

### Gadget mode serial iex

Plug in the Pi Zero to a host computer using the USB port on the Zero labeled "USB", then connect to the running iex console via a terminal emulator
Example: `screen /dev/tty.usbmodem* 115200`

### WiFi

Once inside the iex session, try out WiFi on a Pi Zero W or Pi Zero with RedBear IoT pHAT:
```
# Replace SSID and PASSWORD with something real, and potentially change key_mgmt if necessary. See https://github.com/nerves-project/nerves_interim_wifi for more information. 
{:ok, pid} = Nerves.InterimWiFi.setup("wlan0", ssid: "[SSID]", key_mgmt: :"WPA-PSK", psk: "[PASSWORD]")
```

If the setup was successful, you will see lots of stuff on the screen, ending with something like: 
    00:00:17.444 [info]  WiFiManager(wlan0, dhcp) got event {:bound, %{domain: "local", ifname: "wlan0", ipv4_address: "...", ipv4_broadcast: "", ipv4_gateway: "...", ipv4_subnet_mask: "...", nameservers: ["...", "..."]}}

## Learn more about Nerves

  * Official docs: https://hexdocs.pm/nerves/getting-started.html
  * Official website: http://www.nerves-project.org/
  * Discussion Slack elixir-lang #nerves ([Invite](https://elixir-slackin.herokuapp.com/))
  * Source: https://github.com/nerves-project/nerves
