# Configuración de protocolo RIP

## Topología a realizar

[![image.png](https://i.postimg.cc/63YjZGx2/image.png)](https://postimg.cc/R6JL5hF4)

El protocolo RIP se configura en los routers a los cuales queremos establecer las conexiones.

## Comandos Utilizados

<ol>
<li>R1 </li>

### Configuración de Interfaces
    enable
    configure terminal

    interface f0/1
    ip address 9.0.0.1 255.255.255.0
    no shutdown

    interface f0/0
    ip address 10.0.0.1 255.255.255.0
    no shutdown


### Empezamos a configurar RIP
    router rip
    version 2

    !definimos las redes conectadas a este router
    network 9.0.0.0
    network 10.0.0.0

### guardamos la configuración
    do write


<li>R2</li>

### Configuración de Interfaces
    enable
    configure terminal

    interface f0/1
    ip address 11.0.0.1 255.255.255.0
    no shutdown

    interface f0/0
    ip address 10.0.0.2 255.255.255.0
    no shutdown


### Empezamos a configurar RIP
    router rip
    version 2

    !definimos las redes conectadas a este router
    network 10.0.0.0
    network 11.0.0.0


# Configuración de protocolo OSPF

El protocolo OSPF es un protocolo de enrutamiento dinámico que se utiliza en los routers a los cuales queremos establecer las conexiones.

## Comandos para configurar OSPF

<ol>
<li>R1 </li>

### Configuración de Interfaces
    enable
    configure terminal

    int g0/1
    ip address 192.168.10.1 255.255.255.0
    no shut

    int gi0/0
    ip address 192.168.1.1 255.255.255.252
    no shut

### Para configurar OSPF
    router ospf 10

    !definimos las redes conectadas a este router
    network 192.168.10.0 0.0.0.255 area 0
    network 192.168.1.0 0.0.0.3 area 0


# Configuración de protocolo EIGRP

## Topología a realizar

[![image.png](https://i.postimg.cc/q72t79Cg/image.png)](https://postimg.cc/Jy476YxW)

El protocolo EIGRP también es un protocolo de enrutamiento dinámico que se utilizamos en los routers a los cuales queremos establecer las conexiones.


## Comandos Utilizados

<ol>
<li>R1 </li>

### Configuración de Interfaces
    enable
    configure terminal

    int gi0/0
    ip address 192.168.10.1 255.255.255.0
    no shut

    !configuramos interfaz serial
    int s0/1/0
    ip address 192.168.30.1 255.255.255.252
    no shut




### Empezamos a configurar EIGRP
    router eigrp 10

    !definimos las redes conectadas a este router
    network 192.168.10.0 0.0.0.255
    network 192.168.30.0 0.0.0.3
    no auto-summary



### guardamos la configuración
    do write


<li>R2</li>

### Configuración de Interfaces
    enable
    configure terminal

    int gi0/0
    ip address 192.168.20.1 255.255.255.0
    no shut


    int s0/1/0
    ip address 192.168.30.2 255.255.255.252
    no shut
    clock rate 64000




### Empezamos a configurar EIGRP
    router eigrp 10

    !definimos las redes conectadas a este router
    network 192.168.20.0 0.0.0.255
    network 192.168.30.0 0.0.0.3
    no auto-summary 

### guardamos la configuración
    do write

<li>Por último, se deben colocar las IPs adecuadas a las VPC y se podrá tener ping a lo largo de la topología.
</li>

<li>Comandos para verificar la configuración</li>

    show ip protocol
    show ip route

</ol>

