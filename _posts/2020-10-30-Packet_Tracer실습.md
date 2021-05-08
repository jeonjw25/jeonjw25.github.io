---
title: Packet Tracer 라우터 및 허브 실습
categories: [School]
comments: true
---
# 목차  
1) Router 0 (2016030081) 기본설정 

2) Router 1 (2016030082) 기본설정  

3) Ping Test  

4) Telnet 설정 및 접속  

5) Hub 실습  

<br/>
<br/>  

![실습1](https://user-images.githubusercontent.com/54730375/97668047-814ab080-1ac4-11eb-87f9-0676a6b52dab.PNG)  

# Router 0 (2016030081) 기본설정

![router1_1](https://user-images.githubusercontent.com/54730375/97668090-932c5380-1ac4-11eb-90f4-c2aebb0437f8.PNG)  

![router1_2](https://user-images.githubusercontent.com/54730375/97668081-90316300-1ac4-11eb-9d19-574c92e6cf77.PNG)  

```telnet
enable (user모드진입)
conf t (관리자모드진입)
hostname 2016030081 (Hostname설정)
int gi0/0/0 (gigabit ethernet설정)
ip add 10.1.1.1 255.255.255.0 (ip 설정)
no shut (설정완료후 라우터전원이 안꺼지도록 설정)
enable password hufs1 (패스워드설정)
enable secret hufs (시크릿넘버설정)
```  
<br/>
<br/>

# Router 1 (2016030082) 기본설정  
![router2_1](https://user-images.githubusercontent.com/54730375/97668087-91fb2680-1ac4-11eb-899b-53694d607110.PNG)  

![router2_2](https://user-images.githubusercontent.com/54730375/97669221-f9b27100-1ac6-11eb-8554-6186f5cb788b.PNG)  

```telnet
enable (user모드진입)
conf t (관리자모드진입)
hostname 2016030082 (Hostname설정)
int gi0/0/0 (gigabit ethernet설정)
ip add 10.1.1.2 255.255.255.0 (ip 설정)
no shut (설정완료후 라우터전원이 안꺼지도록 설정)
enable password hufs2 (패스워드설정)
enable secret hufs (시크릿넘버설정)
```
<br/>
<br/>  

# Ping Test

![router1_ping](https://user-images.githubusercontent.com/54730375/97668084-91629000-1ac4-11eb-9550-c2089767c691.PNG)  

![router2_ping](https://user-images.githubusercontent.com/54730375/97668088-9293bd00-1ac4-11eb-91e5-d30e492430b6.PNG)  

```telnet
CTRL + Z (유저모드진입)
ping 10.1.1.2 (상대 호스트 이름)
```
5개 중 5개 수신.  

<br/>
<br/> 

# Telnet 설정 및 접속  
![router1_telnet](https://user-images.githubusercontent.com/54730375/97668086-91629000-1ac4-11eb-97df-ae1f9194456a.PNG)  

![router2_telnet](https://user-images.githubusercontent.com/54730375/97668089-9293bd00-1ac4-11eb-883b-74aac26e31da.PNG)  

```telnet
conf t (관리자모드진입)
line vty 0 2 (동시접속가능호스트 0~2)
password hufs (텔넷 비밀번호설정)
CTRL + Z (유저모드진입)
telnet 10.1.1.2 (상대호스트 IP)
```

# Hub 실습  
![Hub_ready](https://user-images.githubusercontent.com/54730375/97671575-d6d68b80-1acb-11eb-9bf5-04aeb361ef5f.PNG)  
PC4 -> PC7로 ping보낼 시 초기모습  
  
- When PC4 pings PC7, what type of packet is sent to the hub initially? Can you prove it?  

    : ARP  
    ![Hub_step1](https://user-images.githubusercontent.com/54730375/97671576-d6d68b80-1acb-11eb-90de-c28fc7deddc8.PNG)  

- Who receives the packet? 

    : PC5, PC6, PC7  

    ![Hub_step2](https://user-images.githubusercontent.com/54730375/97671568-d4743180-1acb-11eb-9c63-8b7d26398c78.PNG)  

-  Who recieves the return traffic from PC7 to PC4?  

    : PC4, PC5, PC6  

    ![hub_add](https://user-images.githubusercontent.com/54730375/98643064-c9de5580-2371-11eb-96a8-dd352ba8df0c.PNG) 

- When ping traffic is sent from PC4 to PC7, who recieves the traffic?  

    : PC5, PC6, PC7  

    ![Hub_step5](https://user-images.githubusercontent.com/54730375/97672691-d0e1aa00-1acd-11eb-8af0-dc7dbb5f040e.PNG)  


