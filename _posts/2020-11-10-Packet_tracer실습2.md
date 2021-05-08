---
title: Packet Tracer 스위치 실습
categories: [School]
comments: true
---
# 스위치 실습

- When PC0 pings PC3, what type of packet is sent to the switch initially? Can you prove it?  
    : ARP  
![HW4_1](https://user-images.githubusercontent.com/54730375/98641781-ac0ff100-236f-11eb-8f1b-7765b3c21ad1.PNG) 

- Who receives the packet?  
    : PC1, PC2, PC3  
![HW4_2](https://user-images.githubusercontent.com/54730375/98641782-ac0ff100-236f-11eb-8740-02e82f66c1c9.PNG)  
처음에는 ARP 패킷이 모든 경로로 다 전송됨.

- Who receives the return traffic from PC3 to PC0?  
    : PC0   
![HW4_4](https://user-images.githubusercontent.com/54730375/98641777-aa462d80-236f-11eb-849c-9a3618ed7845.PNG)  
스위치는 송신자인 PC0의 MAC address를 저장하고 있으므로 바로 PC0로 패킷을 전송가능.

- When ping traffic sent from PC0 th PC3, who receives the traffic?  
    : PC3  
![HW4_5](https://user-images.githubusercontent.com/54730375/98641779-ab775a80-236f-11eb-9ab1-00dc2ec822cd.PNG)  
스위치는 PC3의 MAC address를 저장하고 있으므로 바로 PC3로 패킷을 전송가능.

- How many broadcast domains are there in network1?  
    : 4 
![Hub_step2](https://user-images.githubusercontent.com/54730375/97671568-d4743180-1acb-11eb-9c63-8b7d26398c78.PNG)  
처음 전송된 ARP 
![hub_add](https://user-images.githubusercontent.com/54730375/98643064-c9de5580-2371-11eb-96a8-dd352ba8df0c.PNG)  
응답 ARP
![Hub_step5](https://user-images.githubusercontent.com/54730375/97672691-d0e1aa00-1acd-11eb-8af0-dc7dbb5f040e.PNG)  
ICMP
- How many broadcast domains are there in network2?  
    : 3  
![HW4_2](https://user-images.githubusercontent.com/54730375/98641782-ac0ff100-236f-11eb-8740-02e82f66c1c9.PNG)
처음 전송된 ARP  

- How many collision domains in network1 and network2?
    : 1  / 0 times  
![hub_collision1](https://user-images.githubusercontent.com/54730375/98646407-aff34180-2376-11eb-875f-fc2b02617e86.PNG)
![hub_collision2](https://user-images.githubusercontent.com/54730375/98646403-aec21480-2376-11eb-914a-636f34080b1d.PNG)
위 그림과 같이 허브에서는 패킷들과의 충돌이 일어난다.  
반면 스위치는 동시에 오는 패킷들을 순서대로 전달하기때문에 충돌이 일어나지 않는다.  

<br/>
<br/>
<br/>

# vlan 실습  
초기 상태  
![vlan_1](https://user-images.githubusercontent.com/54730375/98652404-ecc33680-237e-11eb-84eb-0a28fa29eaed.PNG)  
switch와 fastethernet 연결 후 각 PC에 IP & subnetmask 할당  

![vlan_initial](https://user-images.githubusercontent.com/54730375/98652413-edf46380-237e-11eb-8d04-4f813fce17ff.PNG)  
초기에는 default 값인 vlan 1에 모든 pc가 속해있다.  


다음 명령어를 통해 PC0, PC1, PC2 -> vlan 2에, PC3, PC4, PC5 -> vlan 3에 할당한다.  
```
conf t
int fa0/1 (각 연결의 인터페이스로 진입)
switchport access vlan 2 (할당하고싶은 vlan에 할당)
ctrl + z (관리자 모드로 진입)
show vlan (vlan 설정확인)
```  
![vlan_config](https://user-images.githubusercontent.com/54730375/98652412-edf46380-237e-11eb-893a-fdfb5cb1838c.PNG)  

<br/>
vlan 설정 후 show vlan을 통해 확인해보면 vlan2 와 vlan3에 각각 PC가 3대씩 할당 된 것을 볼 수 있다.  

![vlan_2,3](https://user-images.githubusercontent.com/54730375/98652406-ed5bcd00-237e-11eb-9fdf-19ec15a5ccbe.PNG)  
  
<br/>
vlan이 잘 할당 되었는지 핑을 통해 테스트 해보면 같은 vlan 안에 있는 PC끼리는 ping이 잘 전달 되나 다른 vlan에 있는 PC로 ping을 보내면 timeout이 뜨는 것을 확인 할 수 있다.  

![vlan_ping1](https://user-images.githubusercontent.com/54730375/98652415-ee8cfa00-237e-11eb-8071-f41df1a0b4fd.PNG)
![vlan_ping2](https://user-images.githubusercontent.com/54730375/98652401-ec2aa000-237e-11eb-9f44-5613c340564b.PNG)  

즉 아래와 같은 구조로 vlan설정이 된 것이다.

![vlan_arch](https://user-images.githubusercontent.com/54730375/98652408-ed5bcd00-237e-11eb-9afc-34e337d100c5.PNG)


