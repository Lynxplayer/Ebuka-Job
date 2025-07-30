```mermaid

 flowchart TD

    A[Start / Power On] --> B[Initialize ESP32
    <br/> Set preset intensity threshold
    <br/> Configure Wi-Fi and email credentials
    <br/> Initialize LCD (I2C 16x2)
    <br/> Set GPIO pins for LEDs
    <br/> Setup ADC for LDR]

    B --> C[Read potentiometer
    <br/> Set laser driver current]

    C --> D[Turn laser ON
    <br/> Transmit light through fiber]

    D --> E[Read LDR via ADC
    <br/> Voltage divider measurement]

    E --> F[Convert ADC value to intensity
