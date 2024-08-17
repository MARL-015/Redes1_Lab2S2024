# LABORATORIO REDES DE COMPUTADORAS 1

## **COMANDOS BÁSICOS PARA CONFIGURAR VLAN 📚**

- **Para configurar VLANs en un Switch** 

    ```
    enable
    configure terminal
    hostname SW#
    ```

- creando y definiendo las vlans

    ```
    vlan 10
    name VLAN10
    vlan 20
    name VLAN20
    vlan 99
    name VLAN99
    exit
    ```

- configurando el modo troncal

    ```
    interface f0/#
    switchport mode trunk
    ```

- cambiando la vlan nativa 
    ```
    switchport trunk native vlan #
    ```
 
- restringiendo las vlan que se pasarán en modo troncal
    ```
    switchport trunk allowed vlan 10,20,99,1002-1005
    ```

- configurando el modo acceso

    ```
    interface f0/#
    switchport mode access
    switchport access vlan #
    ```

- guardando la configuracion
    ```
    do write
    end
    ```

- visualizar las vlan creadas
    ```
    show vlan brief 
    sh vlan
    ```