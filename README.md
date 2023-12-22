## netboot.xyz-custom

clone this, change as needed, add

    set github_user <yourgithubuser>

in boot.cfg (as of now, i proposed a change in netboot.xyz) and a new menuitem will appear
or just copy&paste if you're already using your own custom menus

* [Kairos](https://kairos.io) installation

## Boot using iPXE

### NIC with Embedded iPXE

If you've already compiled your own iPXE, you can load up the netboot.xyz menu easily by entering CTRL-B when prompted, setting DHCP and then chainloading iPXE:

```bash
dhcp
chain --autofree https://boot.netboot.xyz
```

If you don't have DHCP on your network, you can manually set your network information:

```bash
set net0/ip <ip>
set net0/netmask <netmask>
set net0/gateway <gateway>
set dns <nameserver>
ifopen net0
chain --autofree https://boot.netboot.xyz
```

Some iPXE builds do not support HTTPS connections. If you get an "Operation not supported" error message, run this instead:

```bash
chain --autofree http://boot.netboot.xyz
```

### KVM

On VPSes that use KVM, you can usually connect to the VPS via VNC, reboot it, press escape while rebooting to get a boot menu, then select the iPXE option. Once iPXE has started, press Ctrl-B and follow the instructions above.
