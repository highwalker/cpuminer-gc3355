cpuminer-gc3355
==============

CPUMiner with GridSeed GC3355 support

./configure CFLAGS="-O3"

GC3355-specific options:

--gc3355=DEV0,DEV1,...,DEVn      			enable GC3355 chip mining mode (default: no)
--freq=FREQUENCY  							set GC3355 core frequency in NONE dual mode (default: 600)
--gc3355-freq=DEV0:F0,DEV1:F1,...,DEVn:Fn	individual frequency setting
--gc3355-autotune  							auto overclocking each GC3355 chip (default: no)
--gc3355-chips=N  							# of GC3355 chips (default: 5)

How to use with Blades: add "--gc3355-chips=40" to the command line

Example script with backup pools for *nix:

while true ; do
./minerd --gc3355=/dev/ttyACM0,/dev/ttyACM1,/dev/ttyACM2 --gc3355-freq=/dev/ttyACM0:800 --gc3355-autotune --freq=850 --url=stratum+tcp://pool1:port --userpass=user:pass --retries=1
./minerd --gc3355=/dev/ttyACM0,/dev/ttyACM1,/dev/ttyACM2 --gc3355-freq=/dev/ttyACM0:800 --gc3355-autotune --freq=850 --url=stratum+tcp://pool2:port --userpass=user:pass --retries=1
./minerd --gc3355=/dev/ttyACM0,/dev/ttyACM1,/dev/ttyACM2 --gc3355-freq=/dev/ttyACM0:800 --gc3355-autotune --freq=850 --url=stratum+tcp://pool2:port --userpass=user:pass --retries=1
done

Example script with backup pools for Windows:

:loop
minerd.exe --gc3355=\\.\COM1,\\.\COM2,\\.\COM3 --gc3355-freq=\\.\COM1:800 --gc3355-autotune --freq=850 --url=stratum+tcp://pool1:port --userpass=user:pass --retries=1
minerd.exe --gc3355=\\.\COM1,\\.\COM2,\\.\COM3 --gc3355-freq=\\.\COM1:800 --gc3355-autotune --freq=850 --url=stratum+tcp://pool2:port --userpass=user:pass --retries=1
minerd.exe --gc3355=\\.\COM1,\\.\COM2,\\.\COM3 --gc3355-freq=\\.\COM1:800 --gc3355-autotune --freq=850 --url=stratum+tcp://pool3:port --userpass=user:pass --retries=1
goto loop
pause