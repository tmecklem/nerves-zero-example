# Nerves Zero Example

This is a sample Nerves project intended to showcase the USB serial and ethernet "gadget" OTG capabilities of the Pi Zero and WiFi support for the Pi Zero W and RedBear IoT pHAT. It utilizes the `nerves_system_rpi0` system found at https://github.com/nerves-project/nerves_system_rpi0.

## Getting Started

To start your Nerves app:

```
MIX_TARGET=rpi0 mix deps.get
MIX_TARGET=rpi0 mix firmware
#Burn to an SD card with
MIX_TARGET=rpi0 mix firmware.burn
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
>     00:00:17.444 [info]  WiFiManager(wlan0, dhcp) got event {:bound, %{domain: "local", ifname: "wlan0", ipv4_address: "...", ipv4_broadcast: "", ipv4_gateway: "...", ipv4_subnet_mask: "...", nameservers: ["...", "..."]}}

## Learn more about Nerves

  * Official docs: https://hexdocs.pm/nerves/getting-started.html
  * Official website: http://www.nerves-project.org/
  * Discussion Slack elixir-lang #nerves ([Invite](https://elixir-slackin.herokuapp.com/))
  * Source: https://github.com/nerves-project/nerves
