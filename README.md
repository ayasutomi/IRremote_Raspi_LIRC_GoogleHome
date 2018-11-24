# IR remote with Raspberry pi and Google Home

## Install LIRD

## Test IR LED

    $ cd /etc/lirc/lircd.conf.d/
    $ sudo wget -O test.conf https://sourceforge.net/p/lirc-remotes/code/ci/master/tree/remotes/samsung/00056A.lircd.conf?format=raw

    $ sudo systemctl stop lircd
    $ sudo systemctl start lircd

    $ irsend SEND_ONCE Samsung_00056A KEY_POWER

## TEST Receiver

    $ sudo mode2 -d /dev/lirc0
Then press a TV remote control. It will print the date as below)
    space 8979
    pulse 4451
    space 588
    pulse 93409
    space 8981
    pulse 4444
    space 584
    pulse 93412

## Record TV Remote Control

Return to root

    $ cd

stop lircd if it was running

    $ sudo kill $(pidof lircd)

Start recording without namespace

    $ sudo irrecord --disable-namespace

Follow instructions on screen

Copy file to '/etc/lirc/lircd.conf.d/'.

    $ sudo cp Sharp_GB077WJSA.lircd.conf /etc/lirc/lircd.conf.d/

## Record Air Conditioner Remote Control

Air conditioner remote controls do not send signals related to just one button as on TV remotes.
Instead, it send a signal with the whole air conditioner configuration including temperature, airflow, air direction, etc.
Thus the message is very long, so the irrecord command does not work properly.

To record the A/C IR signal then, the command the following command to read the IR signals is used.

    $ mode2 -m -d /dev/lirc0

The signals obtained will be in the following form:

    4989552

        4369     4418      525     1640      579     1587
        527     1639      526     1648      520      554
        526      557      526     1640      527      555
        526      555      534      548      532      551
        533      550      525     1642      525     1639
        531      552      525     1641      527      555
        528      557      523      555      527      554
        527      557      526      556      525     1649
        518     1641      525     1641      528     1639
        580     1586      527     1639      527     1641
        527     1638      582      501      525      557
        526      554      528      555      527      555
        526      555      526      557      534      547
        528      552      528     1640      527     1639
        527      556      581      501      526      555
        526      557      526      554      527      556
        526      556      525      557      526      555
        527      555      526      556      527      555
        526      559      523      555      582     1585
        526      557      525      553      530      557
        524      555      527      562      574      502
        579      501      528      555      529     1638
        579      502      527      556      525      556
        526      556      526      555      527      556
        527      555      526     5338     4381     4409
        609     1559      579     1588      580     1585
        527     1637      530      554      526      556
        527     1638      538      543      528      555
        528      560      522      555      526      554
        529     1639      581     1586      527      563
        524     1634      527      555      529      551
        537      547      526      555      527      563
        517      558      526     1646      521     1639
        528     1641      525     1640      586     1580
        527     1640      525     1641      525     1643
        525      562      517      558      527      553
        584      500      528      555      525      556
        527      554      527      555      527      554
        526     1640      583     1583      529      555
        527      555      526      556      525      556
        525      557      526      556      526      556
        527      555      526      563      572      502
        527      556      580      501      527      555
        526      555      527     1640      527      554
        582      501      526      555      527      555
        527      557      525      555      580      501
        580      503      527     1639      582      500
        583      500      526      555      526      556
        582      500      527      555      526      556
        526

## Create node.js server



## Link Google Home to Raspberry Pi using Webhooks



## Open port to internet (Port Forwading)

Forward a port from the internet to your home network. 

This has to be done in your router configuration normally accessed by typing the ip address of the router (usually 192.168.1.1 or 192.168.11.1).

The ip address used in the port forward is the local ip address of the raspi, and the port is 3003 (as configured in the .js file of the server)


## References:
https://craftzdog.hateblo.jp/entry/control-an-air-conditioner-with-voice-from-google-home-via-raspberry-pi

https://portforward.com/buffalo/whr-g300n/

https://pimylifeup.com/raspberry-pi-port-forwarding/

https://www.instructables.com/id/Google-Home-Raspberry-Pi-Power-Strip/

https://www.instructables.com/id/Raspberry-Pi-Zero-Universal-Remote/

https://www.raspberrypi.org/forums/viewtopic.php?t=159035

https://www.raspberrypi.org/forums/viewtopic.php?t=90731

https://github.com/mtraver/rpi-ir-remote






