# serial-port-Linux-windows10-
port serie sous linux sous windows10
Example

On a Windows 10 machine where board is connected on COM15 connect using the following steps:

    sudo chmod 666 /dev/ttyS15 - This is required since cu changes it's uid which drops capabilities even when running as root. Not all serial programs have the same behavior.
    stty -F /dev/ttyS15 -a . Optionally check your current serial settings before updating.
    Set your serial settings, depending on your application this usually will be raw or sane. Either one seems to work fine with cu:
        stty -F /dev/ttyS15 sane 9600
        stty -F /dev/ttyS15 raw 9600 -echo -echoe -echok -echoctl -echoke -iexten -onlcr cs8 crtscts
    cu -l /dev/ttyS15 -s 9600
    Hit enter to refresh the cu console
