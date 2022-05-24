# How to write a shell script

[[Linux]]
In my setup i have a 144hz monitor, I use linux  with bspwm and I can't set 144hz on the system.  So i created script so I don't have to write every time the computer turns on the code that sets 144hz. So finally let's see how to write a shell script

First we create a .sh file.

```shell
touch test.sh
```

Now the first thing we need to write is this

```shell
#!/usr/bin/env bash
```

After that just write the code we want to run

```shell
#!/usr/bin/env bash
xrandr --output HDMI-A-0 --mode 1920x1080 --rate 144
```

The code is done, now we need to run it, but how to do it?
We need to set the script executable permission by running `chmod` command

```shell
chmod +x test.sh
```

Now to run just write

```shell
./test.sh
```
