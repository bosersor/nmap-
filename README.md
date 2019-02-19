# nmap - 
sentencias para nmap credits SecurityByDefault --> www.securityhacklabs.net

Uso: nmap [Tipo(s) de Análisis] [Opciones] {especificación de objetivos} ESPECIFICACIÓN DE OBJETIVO:
Se pueden indicar nombres de sistema, direcciones IP, redes, etc.

Ej: scanme.nmap.org, microsoft.com/24, 192.168.0.1; 10.0.0-255.1-254

-ESPECIFICACIÓN DE OBJETIVO:
-iL <archivo_entrada>: Lee una lista de sistemas/redes del archivo.

-iR <número de sistemas>: Selecciona objetivos al azar

--exclude <sist1[,sist2][,sist3],...>: Excluye ciertos sistemas o redes --excludefile <fichero_exclusión>: Excluye los sistemas indicados en el fichero

DESCUBRIMIENTO DE HOSTS:
-sL: Sondeo de lista - Simplemente lista los objetivos a analizar

-sP: Sondeo Ping - Sólo determina si el objetivo está vivo

-P0: Asume que todos los objetivos están vivos

-PS/PA/PU [listadepuertos]: Análisis TCP SYN, ACK o UDP de los puertos indicados 

-PE/PP/PM: Solicita un análisis ICMP del tipo echo, marca de fecha y máscara de red 

-n/-R: No hacer resolución DNS / Siempre resolver [por omisión: a veces] 

--dns-servers <serv1[,serv2],...>: Especificar servidores DNS específicos 

--system-dns: Utilizar la resolución del sistema operativo


TÉCNICAS DE ANÁLISIS:
-sS/sT/sA/sW/sM: Análisis TCP SYN/Connect()/ACK/Window/Maimon 

-sN/sF/sX: Análisis TCP Null, FIN, y Xmas

--scanflags <indicador>: Personalizar los indicadores TCP a utilizar 
  
-sI <sistema zombi[:puerto_sonda]>: Análisis pasivo («Idle», N. del T.) 

-sO: Análisis de protocolo IP

-b <servidor ftp rebote>: Análisis por rebote FTP


ESPECIFICACIÓN DE PUERTOS Y ORDEN DE ANÁLISIS: 
-p <rango de puertos>: Sólo sondear los puertos indicados Ej: 
  
-p22; -p1-65535; -p U:53,111,137,T:21-25,80,139,8080

-F: Rápido - Analizar sólo los puertos listados en el archivo nmap-services

-r: Analizar los puertos secuencialmente, no al azar. DETECCIÓN DE SERVICIO/VERSIÓN:

-sV: Sondear puertos abiertos, para obtener información de servicio/versión 

--version-intensity <nivel>: Fijar de 0 (ligero) a 9 (probar todas las sondas) 
  
  --version-light: Limitar a las sondas más probables (intensidad 2) 
  
  --version-all: Utilizar todas las sondas (intensidad 9)
  
  --version-trace: Presentar actividad detallada del análisis (para depurar)
  
  
  DETECCIÓN DE SISTEMA OPERATIVO
-O: Activar la detección de sistema operativo (SO)

--osscan-limit: Limitar la detección de SO a objetivos prometedores

--osscan-guess: Adivinar el SO de la forma más agresiva

TEMPORIZADO Y RENDIMIENTO:
-T[0-5]: Seleccionar plantilla de temporizado (los números altos son más rápidos) 

--min-hostgroup/max-hostgroup <tamaño>: Paralelizar los sondeos 

--min-parallelism/max-parallelism <msegs>: Paralelización de sondeos 
  
  --min-rtt-timeout/max-rtt-timeout/initial-rtt-timeout <msegs>: Indica
el tiempo de ida y vuelta de la sonda

--max-retries <reintentos>: Limita el número máximo de retransmisiones de las sondas de análisis de puertos
  
--host-timeout <msegs>: Abandonar un objetivo pasado este tiempo

--scan-delay/--max-scan-delay <msegs>: Ajusta el retraso entre sondas EVASIÓN Y FALSIFICACIÓN PARA CORTAFUEGOS/IDS:

-f; --mtu <valor>: fragmentar paquetes (opc. con el MTU indicado) 
  
  -D <señuelo1,señuelo2[,ME],...>: Disimular el análisis con señuelos
N. del T.: «ME» es «YO» mismo.

-S <Dirección_IP>: Falsificar la dirección IP origen

-e <interfaz>: Utilizar la interfaz indicada

-g/--source-port <numpuerto>: Utilizar el número de puerto dado

--data-length <num>: Agregar datos al azar a los paquetes enviados

--ttl <val>: Fijar el valor del campo time-to-live (TTL) de IP

--spoof-mac <dirección mac/prefijo/nombre de fabricante>: Falsificar la dirección MAC --badsum: Enviar paquetes con una suma de comprobación TCP/UDP falsa

SALIDA:
-oN/-oX/-oS/-oG <file>: Guardar el sondeo en formato normal, XML,
s|<rIpt kIddi3 (n3n3b4n4n4), y Grepeable (para usar con grep(1), N. del T.),
respectivamente, al archivo indicado.

-oA <nombre_base>: Guardar en los tres formatos principales al mismo tiempo

-v: Aumentar el nivel de mensajes detallados (-vv para aumentar el efecto) -d[nivel]: Fijar o incrementar el nivel de depuración (Tiene sentido hasta 9) 

--packet-trace: Mostrar todos los paquetes enviados y recibidos

--iflist: Mostrar interfaces y rutas (para depurar)

--append-output: Agregar, en vez de sobreescribir, a los archivos indicados con -o. 

--resume <archivo>: Retomar un análisis abortado/detenido

--stylesheet <ruta/URL>: Convertir la salida XML a HTML según la hoja de estilo
XSL indicada

--webxml: Referenciar a la hoja de estilo de Insecure.Org para tener un XML más portabl
e

--no_stylesheet: No asociar la salida XML con ninguna hoja de estilos XSL

MISCELÁNEO:
-6: Habilitar análisis IPv6

-A: Habilita la detección de SO y de versión

--datadir <nombreDir>: Indicar la ubicación de los archivos de datos Nmap
personalizados.

--send-eth/--send-ip: Enviar paquetes utilizando tramas Ethernet o paquetes IP
"crudos"

--privileged: Asumir que el usuario tiene todos los privilegios -V: Muestra el número de versión
-h: Muestra esta página resumen de la ayuda.

EJEMPLOS:

nmap -v -A scanme.nmap.org
nmap -v -sP 192.168.0.0/16 10.0.0.0/8 nmap -v -iR 10000 -P0 -p 80
