
Flow control in TCP ensures that the sender does not overwhelm the receiver with more data than it can handle. This is achieved using a mechanism called the **Sliding Window Protocol**.

1. **Sliding Window**:
    - Each TCP connection has a **window size**, which represents the amount of data (in bytes) that the sender is allowed to transmit before waiting for an acknowledgment (ACK) from the receiver.
    - The window size is determined by the receiver and communicated to the sender through the **TCP header's window field**. This is known as the **receiver's advertised window**.
    
2. **Dynamic Adjustment**:
    - The window size can change dynamically during the session based on the receiver’s buffer capacity and network conditions.
    - When the receiver’s buffer starts to fill up, it reduces the advertised window size, signaling the sender to slow down the transmission. If the buffer is full, the window size may become zero, effectively pausing data transmission until space is available again.
      
3. **ACK and Data Flow**:
    - The sender can continue sending data until it fills the window. Once data is sent, it waits for ACKs from the receiver. As ACKs are received, the window "slides" forward, allowing the sender to transmit additional data.
    - If ACKs are delayed or lost, the sender may pause transmission until it receives confirmation that previous segments were received correctly.
      
4. **Prevention of Overflows**:
    - Flow control prevents buffer overflows at the receiver by pacing the data flow based on the receiver's ability to process the incoming data.
    - This mechanism avoids overwhelming slower receivers with data, ensuring that all data is processed without loss.