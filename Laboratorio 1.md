
## Manuel David Santos y Valentino Russo

1) Las dos instancias creadas:
	
	![foto](/images/foto1.png)
	
2) Ejecución de ip link show
	![foto2](/images/foto2.png)
	
3) Creamos un script para hacer el setup de la red:
```bash
ip link set enp5s0 up
ip address add 172.16.1.12/24 dev enp5s0
echo "Dispositivos de red configurados correctamente"
```
5) El resultado de ip address show:
	
    ![foto3](/images/foto3.png)
6) Verificamos conectividad entre instancias:
	
    ![foto4](/images/foto4.png)
7) Usamos ping con más opciones:
	
    ![foto5](/images/foto5.png)
	
	El máximo/promedio/minimo fue 0,269/0,377/0,710

8) Cuando reiniciamos las VMs la configuración se pierde ya que los comandos ejecutados para realizarla son temporales. Al probar la red entre equipos nos damos cuenta que no hay conectividad.
	
    ![foto6](/images/foto6.png)
	
9) ¿Cómo se denomina la forma de trabajo donde la configuración no queda almacenada en forma persistente? No creo que esto sea así en todos  los sistemas de red, a igual que nosotros deben tener scripts y configuraciones permanentes que se cargan al iniciar el servicio para no tener que rehacer el trabajo manualmente. Traer ejemplos. El router de mi casa?
10) Para hacer que la configuración sea permanente, configuramos ip estática en la máquina virtual usando el servicio systemd-networkd :
```bash 10-static-enp5s0.network
[Match]
Name=enp5s0

[Network]
Address=172.16.1.11/24
#Gateway=
#DNS=
```



enviar paquetes :
	ping -c 10 -s 16 google.com


lxdbr0 puede ser switch, router, etc
