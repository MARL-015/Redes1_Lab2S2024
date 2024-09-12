# Configuración de Port-channel PAGP - LACP

## Topología a realizar

[![image.png](https://i.postimg.cc/T2FF9Pwd/image.png)](https://postimg.cc/hh824cT6)

Teniendo la topologia nos damos cuenta que en cada una existen varios enlaces, los cuales de van a agrupar para crear los distintos port-channel.

## Comandos Utilizados

<ol>
<li>Configurar PAgP en el S1 y el S3 </li>
Configurar el s1 y s3 (desirable y auto).

### S1
    S1(config)# interface range f0/3-4
    S1(config-if-range)# channel-group 1 mode desirable
    Creating a port-channel interface Port-channel 1

    S1(config-if-range)# no shutdown

### S3
    S3(config)# interface range f0/3-4
    S3(config-if-range)# channel-group 1 mode auto
    Creating a port-channel interface Port-channel 1
    S3(config-if-range)# no shutdown


<li>Configurar los puertos de enlace troncal.</li>

    S1(config)# interface port-channel 1
    S1(config-if)# switchport mode trunk


    S3(config)# interface port-channel 1
    S3(config-if)# switchport mode trunk



<li>Configurar LACP entre el S1 y el S2.</li>

### S1
    S1(config)# interface range f0/1-2
    S1(config-if-range)# switchport mode trunk
    S1(config-if-range)# channel-group 2 mode active
    Creating a port-channel interface Port-channel 2

    S1(config-if-range)# no shutdown

### S2
    S2(config)# interface range f0/1-2
    S2(config-if-range)# switchport mode trunk
    S2(config-if-range)# channel-group 2 mode passive
    Creating a port-channel interface Port-channel 2

    S2(config-if-range)# no shutdown


<li> Configurar LACP entre el S2 y el S3</li>

### S2
    S2(config)# interface range f0/3-4
    S2(config-if-range)# switchport mode trunk
    S2(config-if-range)# switchport trunk native vlan 99
    S2(config-if-range)# channel-group 3 mode active
    Creating a port-channel interface Port-channel 3

    S2(config-if-range)# no shutdown

### S3
    S3(config)# interface range f0/1-2
    S3(config-if-range)# switchport mode trunk
    S3(config-if-range)# switchport trunk native vlan 99
    S3(config-if-range)# channel-group 3 mode passive
    Creating a port-channel interface Port-channel 3

    S3(config-if-range)# no shutdown

### Verificar port-channel
    show etherchannel summary 

### Verificar interfaces 
    show run interface f0/3

### Verificar enlaces troncales por medio del port-channel  
    show run interface po1

