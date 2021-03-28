# Microservicios-SpringBoot - Reservas viajes
Aplicación para realizar reserva de viajes, con opción de elegir hotel y vuelo.

Tecnología utilizada: Arquitectura distribuida con microservicios. Lenguaje programación: JAVA 8 Frameworks: Spring Boot, Spring Cloud BBDD SQL Workbench: MySql Servidor: Tomcat 9

NSTRUCCIONES DE USO: 
 1. Importar la Base de Datos MySql con el fichero "viajes.sql".
 2. Arrancar el servicio de Eureka Server para poder descubrir el resto de servicios.
 3. Una vez desplegado, arrancar el resto de servicios (Hoteles, Vuelos, Reservas).
 4. Abrir "reservas.html" para ir a la página de reservas hechas o "nuevareserva.html" para ir a la página de creación.

MICROSERVICIO SERVIDOR EUREKA http://localhost:8761/ Eureka Server, Servidor que registra los servicios y permite acceder a ellos sin conocer su ubicación real y puerto.

MICROSERVICIO HOTELES http://localhost:8000/hoteles Servicios disponibles: 1. GET -> Devuelve un listado de todos los hoteles disponibles.

MICROSERVICIO VUELOS http://localhost:9000/vuelos/ Servicios disponibles: 1. GET -> {plazas} -> Pasar por parámetro el número de plazas que se deseen. Devuelve un listado con los vuelos que tengan plazas disponibles. 2. PUT -> {idvuelo}/{plazas} -> Pasar por parámetro el 'idvuelo' y el número de plazas a reservar. Actualiza el atributo 'plazas' del vuelo seleccionado, restando las plazas.

MICROSERVICIO RESERVAS http://localhost:10000/reservas Servicios disponibles: 1. GET -> Devuelve un listado de todos las reservas realizadas. 2. POST -> reserva/{personas} -> Pasar por parámetro el número de personas por reserva.

MICROSERVICIO SERVIDOR ZUUL Servidor Zuul, Servidor que proporciona al cliente front un punto de acceso único a todos los servicios comunicándose con el servidor Eureka http://localhost:7000/ 1. svuelos/vuelos/1 -> Devuelve un listado con los vuelos que tengan plazas disponibles. 2. shoteles/hoteles -> Devuelve un listado de todos los hoteles disponibles. 3. sreservas/reserva/1 -> Devuelve un listado de todos las reservas realizadas.
