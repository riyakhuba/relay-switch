# relay
#include <lpc214x.h>

#define RELAY_PIN  10  // GPIO pin number connected to the relay

void delay_ms(unsigned int milliseconds) {
    unsigned int i, j;
    for (i = 0; i < milliseconds; i++)
        for (j = 0; j < 10000; j++);
}

int main(void) {
    IO0DIR |= (1 << RELAY_PIN);  // Set the relay pin as output

    while (1) {
        IO0SET = (1 << RELAY_PIN);  // Activate the relay
        delay_ms(1000);             // Wait for 1 second
        IO0CLR = (1 << RELAY_PIN);  // Deactivate the relay
        delay_ms(1000);             // Wait for 1 second
    }
}
