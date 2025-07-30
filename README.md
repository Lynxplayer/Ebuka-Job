```mermaid

flowchart TD
    A[Start / Power On] --> B[Initialize ESP32 and set threshold]
    B --> C[Read potentiometer and set laser driver current]
    C --> D[Turn laser ON and transmit light through fiber]
    D --> E[Read LDR via ADC to measure intensity]
    E --> F{Is intensity >= preset threshold?}
    F -- Yes --> G[Turn GREEN LED ON and RED LED OFF]
    G --> H[Update LCD: LINK OK + value]
    H --> I[Clear alert latch if set]
    I --> J[Wait debounce interval (100-200 ms)]
    J --> E
    F -- No --> K[Turn RED LED ON and GREEN LED OFF]
    K --> L[Update LCD: ALERT DROP + value]
    L --> M{Has alert already been sent?}
    M -- No --> N[Send email alert and log event]
    N --> O[Set alert latch = TRUE]
    M -- Yes --> P[Skip email to avoid spam]
    O --> Q[Optional: log event to memory]
    P --> Q
    Q --> J
