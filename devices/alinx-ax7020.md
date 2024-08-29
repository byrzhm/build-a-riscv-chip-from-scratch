# Alinx AX7020

## Part ID: `xc7z020clg400-2`

* `xc7z020` is the part number which identifies a specific device from a Xilinx FPGA family (in this case, it belongs to a Zynq family from the 7-series).
* `clg400` is the package number which defines the number of package IO pins.
* `-2` is the speed grade.

## Documentations

* [Zynq-7000 Product Selection Guide](https://www.xilinx.com/support/documentation/selection-guides/zynq-7000-product-selection-guide.pdf)
* [Technical Reference Manual](https://docs.xilinx.com/viewer/book-attachment/mxcNFn1EFZjLI1eShoEn5w/pnoMLQXFIWQ6Jhoj0BUsTQ)
* [Xilinx 7-series Configurable Logic Block User Guide](http://www.xilinx.com/support/documentation/user\_guides/ug474\_7Series\_CLB.pdf)
* [AX7020 User Guide](https://www.alinx.com/public/upload/file/AX7020\_UG.pdf)

## Specification

* How many LUTs, FFs, Block RAMs (number of 36Kb blocks), and DSP slices are on the xc7z020 FPGA?
  * LUTs: 53,200
  * FFs: 106,400
  * Block RAMs (# 36Kb blocks): 140
  * DSP slices: 220

<figure><img src="../.gitbook/assets/Screenshot 2024-07-07 at 17.27.37.png" alt=""><figcaption><p>From <a href="https://www.xilinx.com/support/documentation/selection-guides/zynq-7000-product-selection-guide.pdf"><em>Zynq-7000 Product Selection Guide</em></a></p></figcaption></figure>

* How many slices are in a single CLB?
  * 2 slices in a single CLB (See. [Chapter 2 of 7 Series FPGAs CLB User Guide](http://www.xilinx.com/support/documentation/user\_guides/ug474\_7Series\_CLB.pdf))
* What is the difference between a SLICEL and a SLICEM?

<figure><img src="../.gitbook/assets/Screenshot 2024-07-07 at 19.36.01.png" alt=""><figcaption><p>From chapter 2 of <a href="http://www.xilinx.com/support/documentation/user_guides/ug474_7Series_CLB.pdf"><em>7 Series FPGAs CLB User Guide</em></a></p></figcaption></figure>

* How many LUTs are in a slice?
  * There are 4 LUTs in a slice. (See figure above)
* How many inputs do each of the LUTs have?
  * Each LUT has 6 inputs.

<figure><img src="../.gitbook/assets/Screenshot 2024-07-07 at 19.47.00.png" alt=""><figcaption><p>From chapter 2 of <a href="http://www.xilinx.com/support/documentation/user_guides/ug474_7Series_CLB.pdf"><em>7 Series FPGAs CLB User Guide</em></a></p></figcaption></figure>

* How many slices do you need to implement a logic function of 8 inputs?
  * Only one slice. See the figure above.
