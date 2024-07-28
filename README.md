# RIP-configuartion-using-3-Router
Configured a network using RIP (Routing Information Protocol) on three routers in Cisco Packet Tracer, ensuring dynamic routing and efficient data packet management. The setup also included three switches and multiple PCs, creating a robust and scalable network topology for seamless communication between all connected devices.

### RIP Configuration on 3 Routers with 3 Switches and PCs in Cisco Packet Tracer

**Objective:** Set up a network using RIP on three routers, each connected to a switch with multiple PCs, ensuring dynamic routing and seamless communication.

**Steps:**

1. **Setup Devices:**
   - Place three routers (Router1, Router2, Router3) on the workspace.
   - Place three switches (Switch1, Switch2, Switch3), each connected to a router.
   - Connect multiple PCs to each switch.

2. **Cable Connections:**
   - Use straight-through cables to connect each router to its respective switch.
   - Connect each PC to its corresponding switch using straight-through cables.
   - Use serial cables to connect the routers to each other (Router1 to Router2, Router2 to Router3, and Router3 to Router1 for a triangular topology).

3. **IP Address Configuration:**
   - Assign IP addresses to each router's interfaces and PCs. Ensure all devices within the same subnet can communicate with each other.

   Example for Router1:
   ```shell
   Router> enable
   Router# configure terminal
   Router(config)# interface gigabitEthernet 0/0
   Router(config-if)# ip address 192.168.1.1 255.255.255.0
   Router(config-if)# no shutdown
   Router(config-if)# exit
   Router(config)# interface serial 0/0/0
   Router(config-if)# ip address 10.0.0.1 255.255.255.252
   Router(config-if)# clock rate 64000
   Router(config-if)# no shutdown
   Router(config-if)# exit
   Router(config)# interface serial 0/0/1
   Router(config-if)# ip address 10.0.0.5 255.255.255.252
   Router(config-if)# clock rate 64000
   Router(config-if)# no shutdown
   Router(config-if)# exit
   Router(config)# exit
   ```

4. **Configure RIP on Routers:**
   - Enable RIP on each router and add the network addresses directly connected to the router.

   Example for Router1:
   ```shell
   Router> enable
   Router# configure terminal
   Router(config)# router rip
   Router(config-router)# version 2
   Router(config-router)# network 192.168.1.0
   Router(config-router)# network 10.0.0.0
   Router(config-router)# exit
   Router(config)# exit
   ```

5. **Repeat Steps for Other Routers:**
   - Configure IP addresses and RIP for Router2 and Router3 similarly, adjusting IP addresses and networks as per the network design.

6. **Verify Configuration:**
   - Use the `show ip route` and `show ip protocols` commands on each router to verify that RIP is correctly configured and routes are being learned dynamically.
   - Example command:
     ```shell
     Router# show ip route
     ```

7. **Testing Connectivity:**
   - Use the `ping` command from the PCs to test connectivity to other PCs in different subnets, ensuring that RIP is facilitating proper routing.

   Example command from a PC:
   ```shell
   PC> ping 192.168.2.2
   ```

### Conclusion

By following these steps, you can set up a RIP-based network configuration in Cisco Packet Tracer, ensuring effective and dynamic routing across multiple routers and switches.
