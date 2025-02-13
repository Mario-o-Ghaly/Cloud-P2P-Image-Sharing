### Server
- Clone the repo
- Navigate to `src` folder, and inside `main.rs`, manually change the socket addresses of the 3 servers(IP address concatenated with port number). The code has this:  
```
const HEARTBEAT_PORT: u16 = 8085
```

```
// Server settings
let local_addr: SocketAddr = "10.7.19.117:8081".parse().unwrap();
let peer_addresses = vec![
    "10.7.19.117:8085".parse().unwrap(),
    "10.7.19.18:8085".parse().unwrap(),
  ];
```   
>> `HEARTBEAT_PORT` is the port number of the server at hand used for sending and listening to peer servers' heartbeats.  
>> `local_addr` is the IP address of the server at hand concatenated with the port number used for listening to client requests.  
>> `peer_addresses` is the vector of peer IP addresses concatenated with the port number used for heartbeats.  
- Navigate to `src` folder and write `cargo build` then `cargo run`

_Note that >> the **listening port** for all servers should be the **same** since the client sends always to the **same port number**._
