# Read and display pinball DMD data

This project allows to read the contents of a pinball DMD display using Raspberry Pi Pico (RP2040). 

## Hardware

The Pi Pico is directly connected to the 6 DMD data lines. Communication between the Pi Pico and the consumer is implemented by SPI with an additional IRQ line.
On this IRQ line, the Pico signals that new data is available and consumer must start the data transfer. 
Since not any consumer (especially the Raspverry Pi) can act as an SPI slave this method is used.

## License

This project has been forked from https://github.com/pinballpower/code_dmd after that project changed its license from MIT to GPL v3 on 2022-05-02.
So, the license of this fork is GPL v3. 
