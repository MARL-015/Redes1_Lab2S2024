# Configuración de HSRP


El protocolo HSRP se configura hacia las interfaces que harán la conexión entre los switches.

## Comandos Utilizados

<ol>
<li>R2 </li>

### HSRP activo
    conf t
    int f0/0
    ip add 192.168.1.1 255.255.255.0
    standby 10 ip 192.168.1.254
    standby 10 priority 150
    standby 10 preempt
    no shut

### configuramos el puerto serial de enlace entre routers
    int s0/0
    ip address 10.1.1.2 255.255.255.252
    no shut

<li>R3</li>

### HSRP standby
    conf t
    int fa0/0
    ip address 192.168.1.2 255.255.255.0
    standby 10 ip 192.168.1.254
    no shut

### configuramos el puerto serial de enlace entre routers
    int s0/1
    ip address 10.2.2.2 255.255.255.252
    no shut

<li>R1</li>

### configuramos las IP de cada interfaz serial
    int s0/0
    ip address 10.1.1.1 255.255.255.252
    no shut

    int s0/1
    ip add 10.2.2.1 255.255.255.252
    no shut

<li>Comprobando la configuración.</li>

    sh standby

</ol>