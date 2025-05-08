# Remember Debts Backend

**Aplicación para la gestión y recordatorio de deudas mensuales de negocio.**

---

## Tabla de Contenidos

- [Descripción del Proyecto](#descripción-del-proyecto)
- [Caso de Uso](#caso-de-uso)
- [Arquitectura y Tecnologías](#arquitectura-y-tecnologías)
- [Modelo de Datos](#modelo-de-datos)
- [Principales Funcionalidades](#principales-funcionalidades)
- [Estructura de Carpetas](#estructura-de-carpetas)
- [Instalación y Ejecución](#instalación-y-ejecución)
- [Ejemplo de Uso](#ejemplo-de-uso)
- [Equipo de Desarrollo](#equipo-de-desarrollo)
- [Licencia](#licencia)

---

## Descripción del Proyecto

**Remember Debts** es una API REST desarrollada en Java con Spring Boot que permite a los usuarios registrar, visualizar y gestionar todas las deudas recurrentes de su negocio (créditos a proveedores, impuestos, préstamos, etc.), recibir alertas y llevar control de pagos, evitando así olvidos y moras.

---

## Caso de Uso

_"Soy una persona que tiene que pagar las deudas de su negocio todos los meses como los créditos de compras a mis proveedores, mis impuestos prediales, mis cuotas de préstamos bancarios, etc. y como tengo tantas cosas que hacer, a veces me olvido de pagar. Por eso necesito una aplicación que me muestre las deudas que tengo que pagar cada mes (qué deuda, cuándo y cuánto)."_

---

## Arquitectura y Tecnologías

- **Java 17+**
- **Spring Boot 3**
- **Spring Data JPA**
- **PostgreSQL**
- **JWT para autenticación**
- **Lombok**
- **Swagger/OpenAPI** para documentación
- **Maven** para gestión de dependencias

---

## Modelo de Datos

### Entidades principales

- **User / Usuario**: Usuarios del sistema, con información personal, credenciales y estado.
- **Role**: Roles de usuario (`ADMIN`, `USUARIO`).
- **Deuda**: Representa una deuda (nombre, monto, vencimiento, estado, frecuencia, etc.).
- **CategoriaDeuda**: Categorías para organizar deudas (ej: Proveedores, Impuestos).
- **Pago**: Registro de pagos realizados sobre una deuda.
- **Alerta**: Recordatorios asociados a deudas, con fecha y estado (enviada/no enviada).

### Relaciones destacadas

- Un **User** tiene un **Usuario** (datos personales).
- Un **Usuario** puede tener muchas **Deudas**.
- Una **Deuda** pertenece a una **CategoriaDeuda** y puede tener muchos **Pagos** y **Alertas**.
- Los **Roles** definen permisos de acceso.

---

## Principales Funcionalidades

- Registro y autenticación de usuarios con roles y JWT.
- CRUD de deudas, pagos, alertas y categorías.
- Asociación de deudas a usuarios y categorías.
- Registro y consulta de pagos de cada deuda.
- Creación y consulta de alertas de pago.
- Gestión de estados de usuario (activo, suspendido, eliminado) y bloqueo de acceso según estado.
- Validaciones de unicidad y reglas de negocio.
- Documentación automática de la API con Swagger.

---

## Estructura de Carpetas

src/main/java/com/rememberdebtscode/
├── model/entity/ # Entidades JPA
├── model/enums/ # Enumeraciones de dominio
├── repository/ # Repositorios Spring Data JPA
├── dto/ # Data Transfer Objects (DTOs)
├── security/ # Seguridad y autenticación
├── service/ # Lógica de negocio
├── api/ # Controladores REST

---

## Instalación y Ejecución

1. **Clona el repositorio:**

git clone https://github.com/tu-usuario/remember-debts-backend.git
cd remember-debts-backend

2. **Configura la base de datos PostgreSQL**  
   Crea una base de datos llamada `RememberDebtsDB` y actualiza `src/main/resources/application.properties` con tus credenciales.

3. **Ejecuta la aplicación:**

./mvnw spring-boot:run

4. **Accede a la documentación de la API:**  
   [http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html)

---

## Ejemplo de Uso

### Registrar Usuario

POST /auth/register/usuario
{
"firstName": "Carlos",
"lastName": "Morales",
"userTelefono": "+51906344615",
"userEmail": "carlosjun.45@gmail.com",
"userPassword": "@#C1a2R3l4O5s#@"
}

### Registrar Deuda

POST /deudas
{
"userId": 1,
"nombre": "Préstamo Banco",
"categoriaNombre": "Préstamos",
"descripcion": "Cuota mensual",
"monto": 1200.00,
"fechaVencimiento": "2025-05-30",
"estado": "PENDIENTE",
"recurrente": true,
"frecuencia": "MENSUAL"
}

---

## Equipo de Desarrollo

- **Carlos Morales** - Líder de Proyecto
- Miguel Escobar
- Mateo Castillo
- Oscar Llaure

---

## Licencia

Este proyecto está bajo la licencia MIT.

---

## Tareas del Sprint (Desarrolladas)

- Registro y autenticación de usuarios (JWT)
- CRUD de usuarios, roles, deudas, pagos, categorías y alertas
- Gestión de estados de usuario y bloqueo de acceso
- Validaciones de unicidad y reglas de negocio
- Documentación Swagger de la API
- Scripts de carga inicial de roles y categorías

---

¿Dudas o sugerencias? ¡Contáctanos!
