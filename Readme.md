# JWT WebSocket Communication

This project demonstrates secure WebSocket communication between a Spring Boot backend and a FastAPI server using JWT (JSON Web Tokens) for authentication, message passing, and token expiration handling.


## Overview

### Spring Boot Backend

1. Generates JWT tokens containing a message.
2. Establishes a WebSocket connection with a FastAPI server.
3. Sends the JWT token over the WebSocket connection.
4. Handles token expiration by generating a new token after 9 seconds.

### FastAPI Server
1. Runs a WebSocket endpoint that listens for incoming connections.

2. Receives JWT tokens sent by the Spring Boot application.

3. Decodes and verifies the JWT tokens using a shared secret key.

4. Displays the decoded message.

5. Handles expired tokens and processes new tokens generated by Spring Boot.


## JWT Implementation

1. Uses HS256 algorithm for signing tokens.
2. Includes claims such as subject (message content) and expiration time.


## Security
1. Employs JWT for secure message passing between services.
2. Uses a shared secret key for token signing and verification.


## Communication Flow

1. Spring Boot generates a token with a message.

2. The token is sent to FastAPI via WebSocket.

3. FastAPI decodes the token and extracts the message.

4. FastAPI sends a confirmation back to Spring Boot.

5. Token expires after 9 seconds.

6. Spring Boot generates a new token.

7. FastAPI decodes and displays the new message.

8. WebSocket connection is closed.


## Project Structure

    WS_JWT_Exp/
    ├── spring-boot/
    │   ├── src/
    │   │   ├── main/
    │   │   │   ├── java/
    │   │   │   │   └── com/
    │   │   │   │       └── example/
    │   │   │   │           └── jwtwebsocket/
    │   │   │   │               ├── controller/
    │   │   │   │               │   └── MessageController.java
    │   │   │   │               ├── service/
    │   │   │   │               │   └── JwtService.java
    │   │   │   │               ├── model/
    │   │   │   │               │   └── Message.java
    │   │   │   │               └── JwtWebsocketApplication.java
    │   │   └── resources/
    │   │       └── application.properties
    │   └── pom.xml
    └── fastapi/
        ├── main.py
        ├── jwt_service.py
        └── requirements.txt


## File Descriptions

1. **MessageController.java**: Handles incoming requests and sends JWT tokens over WebSocket.

2. **JwtService.java**: Provides JWT token generation and verification services.

3. **Message.java**: Defines the data model for messages exchanged over WebSocket.

4. **JwtWebsocketApplication.java**: Main entry point for the Spring Boot application.

5. **application.properties**: Configuration properties for the Spring Boot application.

6. **pom.xml**: Maven configuration file for managing dependencies and build process.

7. **main.py**: Defines WebSocket endpoint and JWT token decoding logic in FastAPI.

8. **jwt_service.py**: Provides functions for creating and decoding JWT tokens in FastAPI.

9. **requirements.txt**: Lists dependencies for the FastAPI application.


## Prerequisites

Java 11 or higher

Python 3.8 or higher

Maven

pip (Python package installer)


## Overall View

Upon starting, the Spring Boot application will generate a JWT token, establish a WebSocket connection with the FastAPI server, send the token, and print the results of the communication. 

The FastAPI server will handle the received token, decode it, and respond appropriately. After 9 seconds, the token will expire, and the Spring Boot application will generate a new token, which will be processed similarly by the FastAPI server.


## License

This project is licensed under the MIT License.
