# LABORATORIO REDES DE COMPUTADORAS 1 - Clase 3

## **COMANDOS BÁSICOS PARA CONFIGURACIONES 📚**


**Guía de comandos básicos para uso en distintos dispositivos**

- Para ingresar al modo EXEC privilegiado 

    ```
    enable
    ```

- Ingresar al modo Modo de Configuración Global 

    ```
    configure terminal ó conf t
    ```

- Para mostrar la configuración actual del dispositivo

    ```
    show run ó sh run
    ```

- Para salir de algún modo de configuración 
    ```
    exit
    ```
 
- Desactivar la búsqueda de nombres de dominio (DNS) cuando se ingresan comandos que no son reconocidos como comandos del dispositivo.
    ```
    no ip domain-lookup
    ```

- Comando utilizado para guardar la configuración actual de forma permanente para que la configuración sea persistente después de reiniciar el dispositivo, (Se puede utilizar cualquiera de esos comandos):

    ```
    write memory
    wr o do wr (modo configuración global)
    copy running-config startup-config
    ```

- Comando para establecer una contraseña en el modo EXEC privilegiado:
    ```
    enable secret <contraseña-enable>
    ```
    
 - Para visualizar el protocolo ARP desde una pc
    ```
    arp -a
    ```