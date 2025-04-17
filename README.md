# backporting-realtek-gige-nic
Backporting re(4) RealTek Gigabit network device driver from FreeBSD 5.5-RELEASE to FreeBSD-4.9-RELEASE. The chipset of this Gigabit NIC is RTL8169SB.

This is an actual hands-on learning the details on how porting works in FreeBSD network device driver from an SMP-supported FreeBSD-5.5 to a single-CPU i386 systems which is FreeBSD-4.9. This driver is compiled into a kernel loadable module using Makefile.

The original license of the source codes from the author were preserved.

Compiling the kernel loadable if_re.ko will display the NIC information.

``soekris# make clean && make && make install``
``soekris# kldload if_re.ko``

``re0: <RealTek 8169SB Single-chip Gigabit Ethernet> port 0xe400-0xe4ff mem 0xa0003000-0xa00030ff irq 11 at device 10.0 on pci0``
``miibus3: <MII bus> on re0``
``ukphy3: <Generic IEEE 802.3u media interface> on miibus3``
``ukphy3:  10baseT, 10baseT-FDX, 100baseTX, 100baseTX-FDX, auto``

``soekris# ifconfig re0``
``re0: flags=8802<BROADCAST,SIMPLEX,MULTICAST> mtu 1500``
        ``ether 18:a6:f7:00:01:d5``
        ``media: Ethernet autoselect (10baseT/UTP)``
        ``status: active``

``soekris# ifconfig re0 up``
``soekris# ifconfig re0``
``re0: flags=8843<UP,BROADCAST,RUNNING,SIMPLEX,MULTICAST>``
        ``inet6 fe80::1aa6:f7ff:fe00:1d5%re0 prefixlen 64 scopeid 0x8``
        ``ether 18:a6:f7:00:01:d5``
        ``media: Ethernet autoselect (100baseTX <full-duplex>)``
        ``status: active``


