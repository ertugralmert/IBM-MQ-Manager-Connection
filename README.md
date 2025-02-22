# IBM-MQ-Manager-Connection
[Download](https://github.com/ertugralmert/IBM-MQ-Manager-Connection/releases/download/MQ_Manager-v01/MQManager_v01.war)
# IBM MQ Client - User Guide


A web-based client application for managing IBM MQ connections, queues, and messages.

## Overview


IBM MQ Client provides a user-friendly web interface to interact with IBM MQ servers. This application allows you to connect to MQ servers, manage queues, send and receive messages, and monitor server statistics.

## Installation

1. Download the `MQManager_v01.war` file from the releases section of this repository
2. Deploy the WAR file to your servlet container (Tomcat, Jetty, etc.)
	- For Tomcat: Copy the WAR file to the `webapps` directory
	- For standalone operation: Use `java -jar MQManager_v01.war`
3. Access the application in your web browser:
	- If deployed to a servlet container: `http://[server-address]:[port]/ibm-mq-client`
	- If running standalone: `http://localhost:8080`

## Using the Application


### Connecting to IBM MQ Server

1. Fill in the connection details:
	- **Host**: MQ server hostname or IP address
	- **Port**: MQ listener port (default: 1414)
	- **Channel**: MQ server connection channel name
	- **Queue Manager**: Name of the queue manager
	- **Username** and **Password**: Your MQ authentication credentials
2. Click "Bağlantıyı Test Et" (Test Connection) to verify your connection settings

### Using SSL/TLS Secure Connection

1. Check the "SSL Etkinleştir" (Enable SSL) option
2. Fill in the SSL configuration:
	- **SSL Cipher Suite**: Select the appropriate cipher suite (e.g., TLS_RSA_WITH_AES_128_CBC_SHA256)
	- **Trust Store Path**: Full path to your trust store file (.jks)
	- **Trust Store Password**: Password for your trust store
	- **Key Store Path** (optional): Path to your key store for client authentication
	- **Key Store Password** (optional): Password for your key store

### Managing Queues

1. Click "Queue'ları Listele" (List Queues) to see available queues
2. Select a queue from the list to work with it
3. View the message count for the selected queue
4. Click "Mesaj Sayısını Güncelle" (Update Message Count) to refresh the count

### Working with Messages


After selecting a queue, you'll see the "Mesaj İşlemleri" (Message Operations) section with two tabs:

#### Sending Messages

1. Type your message content in the text area
2. Click "Mesaj Gönder" (Send Message)

#### Receiving Messages

1. Click "Mesaj Al" (Receive Message)
2. The received message will appear with its ID and content
3. To delete the message, click "Mesajı Sil" (Delete Message)

### Viewing Logs

1. Click "MQ Loglarını Göster" (Show MQ Logs) to view detailed information about the MQ server
	- Server details
	- Queue Manager information
	- Queue statistics
	- Channel status
	- System information

### Error Tracking

1. If you encounter any errors, click "Hata Kayıtlarını Göster" (Show Error Logs) to view detailed error information

## Example SSL Configuration


If your MQ server requires SSL/TLS connectivity, you'll need these details from your MQ administrator:

```other
Host: ibmmq21.fyre.ibm.com
Port: 1414
Channel: MY.CHANNEL.SSL
Queue Manager: MQMGR
SSL Cipher Suite: TLS_RSA_WITH_AES_128_CBC_SHA256
Trust Store Path: /path/to/clientTrustStore.jks
Trust Store Password: trustpass
```


## Creating a Trust Store


If you need to create your own trust store with the MQ server's certificate:


1. Obtain the MQ server's certificate from your administrator
2. Create a trust store using Java's keytool utility:

    ```other
    keytool -importcert -file mqserver.crt -keystore clientTrustStore.jks -storepass trustpass
    ```

3. Use the path to this JKS file in the Trust Store Path field

## Troubleshooting


### Common Connection Issues

1. **Connection Failed**:
	- Verify hostname/IP and port are correct
	- Check if the MQ server is running and accessible on the network
	- Verify firewall settings allow connection
2. **Authentication Error**:
	- Check username and password
	- Verify that the user has proper permissions
3. **SSL/TLS Errors**:
	- Verify the trust store contains the correct certificate
	- Ensure the cipher suite is supported by the server
	- Check if trust store password is correct
4. **Channel Error**:
	- Verify the channel name is correct
	- Check if the channel is running on the MQ server
5. **Queue Not Found**:
	- Verify the queue exists on the server
	- Check if your user has permissions to access the queue

## Support


For support or questions, please contact your system administrator or open an issue in this repository.

## Author


Designed and developed by Mertugral.
