# TP teleprocesos-y-redes_2

	
## 1. Definir reemplazo de Router cisco 2961 con OSPf - [X]
	
		La recomendacion en el sitio del vendedor es que vayamos por la serie 4000 de routers asi que elegimos CISCO-4331.
		
	
## 2. Definir distribucion de Redes [X] 
	
			10.7.0.0 y 10.8.0.0 (ambito de direcciones de red)
			50 subredes
			600 estaciones fijas
			400 estaciones moviles [estaciones de trabajo que un dia estan y otro no, pueden ser notebooks celus, etc)
		
## 3.  mascaras, etc. [X] 


		
- Las estaciones fijas pueden estar en cualquier lado
    + asi que calculamos:
        * 600 estaciones fijas / 50 subredes = 12 estaciones fijas por subred  
        
        * 12 estaciones fijas por subred + 400 que pueden estar en cualquier parte de la Organizacion
        
        * Si asumimos que la mitad de las maquinas mobiles pueden estar en cualquier lugar de la red. minimo 212 por subred con un CIDR/24 hay 254 hosts, lo cual es suficiente para permitir el creciemeinto a futuro de la organizacion y soportar maquinas mobiles.   
        
        *  /24 permite crear mas subredes a fututo y mejora mucho la legibilidad ya que las direcciones podrian usarse la forma de Direccion.Direccion.Subnet.HHHHHHHH mucho ya que el segundo octeto de subred no seria necesario (con el primero ya tenemos 256 posiles redes, mas que 50)
        
        *  Necesitamos 50 subredes, es decir log(50)/log(2)~= 8 necesitamos 8 bits, ya estamos cubiertos por el punto anterior
        		
        * Incluye los servers y nodos.
		
        * esas estaciones son el total de la organizaion, y solo una subred pedude acceder al nodo central
		
        * Dejamos la primera subred de 10.7.0.0/24 para el backhoul como convencion


## 4. Asignacion se subredes (ahi hay mucho desperdicio de IPs) [X]
   * Area 0:
			10.7.0.0/24
   * Area 100:
			10.8.0.0/24 - 10.8.0.0/24
   * Area 200:
			10.8.20.0/24 - 10.8.40.0/24
   * Area 300:
			10.8.40.0/24 - 10.8.50.0/24
			
			
## 5. asignar datos al diagrama en el emulador [-]

- Crear routers, switches, servers y terminales [X]
- Como solo va haber limitadas maquinas documentadas en que area y conectada a donde vana  estar las estaciones de cada subred (conexiones, aread, etc)[X]
erdo a nuemros de arrib, no el numero total pero qeu sean varias)  [] 
- Connectar por ospf las areas  []
- Connectar por ospf las areas VLANS [] 
- Agegar routers wireless para estacioens mobiles? []
	
## 6. Agregar ACL [] 
	
	
## 7. Hacer pruebas [] 
	
## 8.  Hacer docuemntacion []


# Biblio
	
	
	- Cisco EoS doc
		https://www.cisco.com/c/en/us/products/collateral/routers/2900-series-integrated-services-routers-isr/eos-eol-notice-c51-737831.html
		Ahi recomiendan usar la serie 4000 de ISR
		-recomendaicon de reemplzao
			https://www.cisco.com/c/en/us/products/routers/4000-series-integrated-services-routers-isr/index.html
		- comparacion de serie 4000
			https://www.cisco.com/c/en_in/products/routers/4000-series-integrated-services-routers-isr/models-comparison.html
