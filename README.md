# get_throttled for humans

`vcgencmd get_throttled` is a command on Raspberry Pi operating system, Raspbian, 
to find out whether the processor has been throttled due to overheating or under-voltage, 
and whether this is still the case. 

## Reference to the original documentation
https://www.raspberrypi.com/documentation/computers/os.html#get_throttled

## Validation table
```asci
1111 0000 0000 0000 1111
||||                ||||_ Undervoltage detected
||||                |||_ Arm frequency capped
||||                ||_ Currently throttled
||||                |_ Soft temperature limit active
||||_ Undervoltage has occurred
|||_ Arm frequency capping has occurred
||_ Throttling has occurred
|_ Soft temperature limit has occurred
```

## Example result
Test on Raspberry Pi 4 Model B.
```sh
pi@node01:~ $ vcgencmd get_throttled
throttled=0x0
pi@node01:~ $ bash get_throttled.sh 
Current issues:
No throttling issues detected.

Previously detected issues:
No throttling issues detected.
```
```sh
pi@node02:~/test_cpu $ vcgencmd get_throttled
throttled=0x50000
pi@node02:~/test_cpu $ bash get_throttled.sh 
Current issues:
No throttling issues detected.

Previously detected issues:
~ Under-voltage has occurred
~ Arm frequency capping has occurred
```
