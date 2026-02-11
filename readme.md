#  CoinFast API v2: Resilient Crypto Backend

![Java](https://img.shields.io/badge/Java-21-orange?style=for-the-badge&logo=java)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3-green?style=for-the-badge&logo=spring)
![Docker](https://img.shields.io/badge/Docker-Available-blue?style=for-the-badge&logo=docker)
![Status](https://img.shields.io/badge/Build-Passing-success?style=for-the-badge)


##  Contexto del Proyecto

**CoinFast** es una empresa Fintech la cual ofrece servicios de cotización en tiempo real.
El cliente nos dice: "Nuestra aplicación permite a los usuarios cotizar criptomonedas en tiempo real y guardar sus conversiones favoritas. Pero cada viernes, cuando el equipo anterior subía cambios a producción, la API se rompía, los usuarios veían errores 500 y perdíamos dinero hasta que alguien hacía rollback manual a las 3 de la mañana."

Este proyecto no es solo una calculadora de divisas; es una implementación de referencia de prácticas **DevOps** y **SRE (Site Reliability Engineering)**. El objetivo principal es garantizar la disponibilidad (High Availability) y la observabilidad, incluso cuando las dependencias externas (como la API de CoinGecko) fallan o tienen latencia.

###  Objetivos
1.  **Resiliencia:** Implementación de patrones de tolerancia a fallos.
2.  **Observabilidad:** Métricas en tiempo real expuestas para Prometheus y Grafana.
3.  **Automatización:** Pipeline CI/CD con capacidades de "Self-Healing" (Rollback automático ante anomalías).

---

##  Arquitectura del Sistema

El sistema sigue un modelo de arquitectura monolítica modular, desacoplando la lógica de negocio de las integraciones externas.

### Diagrama de Contexto (C4 Model - Nivel 1)
![Diagrama de Contexto](docs/Contexto1.svg)

**Flujo de Datos:**
1.  **Clientes (Web/Mobile):** Solicitan una conversión de criptomonedas (ej. BTC a USD).
2.  **CoinFast Backend:** Procesa la solicitud, valida reglas de negocio y consulta tasas de cambio.
3.  **Proveedor Externo (CoinGecko):** Fuente de verdad para los precios de mercado.
4.  **Sistema de Monitoreo:** Prometheus recolecta métricas de latencia y errores cada 5s.

---

##  Stack Tecnológico

* **Lenguaje:** Java 21 (LTS)
* **Framework:** Spring Boot 3.5
* **Build Tool:** Maven
* **Contenedorización:** Docker & Docker Compose
* **Observabilidad:**
    * Micrometer (Instrumentación)
    * Prometheus (Recolección de métricas)
    * Grafana (Visualización - *Próximamente*)
* **Testing:** JUnit 5 & Mockito

---

##  Quick Start (Cómo correrlo)

### Prerrequisitos
* Docker & Docker Compose instalados.


### Ejecución con Docker ()
