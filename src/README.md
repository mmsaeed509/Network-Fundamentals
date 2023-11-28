### UDP Client (`udpBaseClient_2`)

```java
package UDP;

import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.InetAddress;
import java.util.Scanner;

public class udpBaseClient_2 {
    public static void main(String args[]) throws IOException {
        Scanner sc = new Scanner(System.in);

        // Step 1: Create the socket object for carrying the data.
        DatagramSocket ds = new DatagramSocket();

        InetAddress ip = InetAddress.getLocalHost();
        byte buf[] = null;

        // Loop until the user enters "bye"
        while (true) {
            // Step 2: Get user input
            String inp = sc.nextLine();

            // Convert the String input into the byte array.
            buf = inp.getBytes();

            // Step 3: Create the datagramPacket for sending the data.
            DatagramPacket DpSend = new DatagramPacket(buf, buf.length, ip, 1234);

            // Step 4: Invoke the send call to actually send the data.
            ds.send(DpSend);

            // Break the loop if the user enters "bye"
            if (inp.equals("bye"))
                break;
        }
    }
}
```

- **Imports**: The necessary Java libraries are imported, including those for working with UDP (e.g., `DatagramSocket`, `DatagramPacket`), input/output (`IOException`), and handling IP addresses (`InetAddress`).

- **Main Method**: The `main` method is the entry point of the program.

    - **Socket Creation**: `DatagramSocket` is created for sending data.

    - **InetAddress**: The IP address (`InetAddress`) is set to the local host.

    - **Input Loop**: The program enters a loop to continually take user input.

    - **Data Conversion**: User input is converted into a byte array.

    - **DatagramPacket Creation**: A `DatagramPacket` is created with the byte array, length, destination IP (localhost), and port number (`1234`).

    - **Data Sending**: The `DatagramSocket` sends the packet.

    - **Exit Condition**: If the user enters "bye," the loop is exited.

### UDP Server (`udpBaseServer_2`)

```java
package UDP;

import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.InetAddress;

public class udpBaseServer_2 {
    public static void main(String[] args) throws IOException {
        // Step 1: Create a socket to listen at port 1234
        DatagramSocket ds = new DatagramSocket(1234);
        byte[] receive = new byte[65535];

        DatagramPacket DpReceive = null;
        while (true) {
            // Step 2: Create a DatagramPacket to receive the data.
            DpReceive = new DatagramPacket(receive, receive.length);

            // Step 3: Receive the data in a byte buffer.
            ds.receive(DpReceive);

            // Step 4: Print the received data
            System.out.println("Client: " + data(receive));

            // Step 5: Exit the server if the client sends "bye"
            if (data(receive).toString().equals("bye")) {
                System.out.println("Client sent bye... EXITING");
                break;
            }

            // Step 6: Clear the buffer after every message.
            receive = new byte[65535];
        }
    }

    // A utility method to convert the byte array data into a string representation.
    public static StringBuilder data(byte[] a) {
        if (a == null)
            return null;
        StringBuilder ret = new StringBuilder();
        int i = 0;
        while (a[i] != 0) {
            ret.append((char) a[i]);
            i++;
        }
        return ret;
    }
}
```

- **Imports**: Similar to the client, the server imports necessary Java libraries.

- **Main Method**: The `main` method is the entry point for the server.

    - **Socket Creation**: A `DatagramSocket` is created to listen on port `1234`.

    - **Data Reception Loop**: The server enters a loop to continuously receive data.

    - **DatagramPacket for Receiving**: A `DatagramPacket` is created for receiving data.

    - **Data Reception**: The server waits to receive data.

    - **Print Received Data**: The received data is printed on the server's console.

    - **Exit Condition**: If the received data is "bye," the server prints a message and exits the loop.

    - **Buffer Clearing**: The receive buffer is cleared after each message.

- **Utility Method (`data`)**: This method converts a byte array into a `StringBuilder` representation until a null character (`0`) is encountered.

### Summary

This code implements a basic UDP client-server communication. The client sends user input to the server, and the server receives and prints the data. The communication continues until the user enters "bye," signaling the termination of the connection.
