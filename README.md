# Dashboard Webmap para Nmap

Compartiendo con unos colegas del grupo **Read Team UTP** al cual pertenezco, hemos estado desarrollando una investigación sobre herramientas que podamos automatizar para la hora de realizar un pentesting, para ello hemos encontrado la herramienta Webmap, un dashboard que toma los resultados de Nmap y los gráfica, además que nos muestra un panel de administración. Esta herramienta no es recomendada en producción debido a que no cuenta con autenticación, sin embargo se pueden implementar medidas complementarias para permitir el acceso como una autenticación básica. 

##### Requerimientos

* [VPS](https://www.vultr.com/?ref=8403796-6G "Vultr.com") o host con nmap 
* docker y docker-compose instalado
* Equipo objetivo en nuestro caso será una máquina de [Hack The Box](https://www.hackthebox.eu/ "HTB") llamada Cascade con ip 10.10.10.182



1. Escaneamos el objetivo con Nmap 

```shell
nmap -sC -sV -T4 -vvvv -p- chamilo.ambientevirtualuea.org -oX /root/webmap-report/backtrack4.xml
```



```shell
docker run -d --name webmap -h webmap -p 8000:8000 -v /root/webmap-report:/opt/xml secureforest/webmap
```



```shell
 docker exec -ti webmap /root/token
```



