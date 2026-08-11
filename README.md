# Read and display pinball DMD data

This project allows to read the contents of a pinball DMD using the Raspberry Pi Pico. Both the RP2040 and RP2350 are supported.

## Hardware

The Pico is directly connected to the DMD data lines. Communication between the Pico and the consumer is implemented via SPI with an additional IRQ line.
On this IRQ line, the Pico signals that new data is available and consumer must start the data transfer whenever possible.
Since most consumers (especially the Raspberry Pi) are not real-time, this method is used. 
Because of this, the consumer has full flexibility of setting an SPI CLK frequency. The Pico in this case is real-time, and will be able to keep up easily.

## Officially supported and tested hardware systems

* WPC95 & WPC -> 128x32
* Data East -> 128x32 & 128x16
* Sega -> 128x32 & 192x64
* Stern Whitestar -> 128x32
* Stern SAM -> 128x32
* Stern SPIKE 1 -> 128x32
* Capcom -> 128x32 & 256x64
* Gottlieb/Premier -> 128x32
* Alvin G. & Co -> 128x32
* Homepin -> 128x32
* Spinball -> 128x32
* Sleic/Petaco -> 128x32
* Dotmation -> 192x64

## Reading data

When reading data, we assume the data is sent correctly.
DMDreader sends complete frames only, containing a predefined amount of bits per pixel.

The process is as follows:
 - Wait for a frame to start (DMD frame detect PIO program)
 - Read frame (DMD dotloop PIO program)
 - Construct frame based on captured data (dmd_dma_handler IRQ)

## License

This project was once forked from https://github.com/pinballpower/code_dmd, but has undergone many changes and additions.
Since the original project changed its license from MIT to GPL v3 on 2022-05-02, the license of this fork is now also GPL v3.