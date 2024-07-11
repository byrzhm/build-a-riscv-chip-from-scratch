# Serial Interface

## Concepts and Implementations

### RS232 Connector

{% hint style="info" %}
**Baud Rate vs. Bandwidth**

Baud rate always refers to symbol rate, but not always bit rate. But here a
 symbol is really one bit.

See [what is the difference between a baud rate and a bandwidth?](https://www.quora.com/What-is-the-difference-between-a-baud-rate-and-a-bandwidth)
{% endhint %}

### UART

### FIFO

## Application: Berkeley Memory Controller

```sh
sudo screen /dev/ttyUSB0 115200 # usually the fastest you can go
```

{% hint style="warning" %}

Use `ls -l /dev | grep ttyUSB0` to make sure that `/dev/ttyUSB0` exists.

{% endhint %}

## References

* [fpga4fun serial interface](https://www.fpga4fun.com/SerialInterface.html)
* [EECS 151/251A 2024 spring fpga lab5](https://github.com/EECS150/fpga_labs_sp24/tree/main/lab5)
* [EECS 151/251A 2024 spring fpga lab6](https://github.com/EECS150/fpga_labs_sp24/tree/main/lab6)
* [Screen User's Manual: 6.6 Window Types](https://www.gnu.org/software/screen/manual/html_node/Window-Types.html#Window-Types)
* Alinx's [RS232 tutorial](https://www.bilibili.com/video/BV1JJ411u77d?p=11&vd_source=571900c3ae9bbfdc988accacb2feb8be)
