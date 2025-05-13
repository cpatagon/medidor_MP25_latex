# Sistema de Medición de Material Particulado Fino (MP₂,₅)

## Descripción

Este repositorio contiene el desarrollo completo de un sistema embebido para la medición, almacenamiento y transmisión de datos de material particulado fino (MP₂,₅) en el aire. El dispositivo está diseñado para ser integrado en redes de monitoreo de calidad del aire urbanas, contribuyendo a la gestión ambiental y la protección de la salud pública.

## Características Principales

- **Medición redundante**: Implementación de tres sensores SPS30 para mayor precisión y confiabilidad.
- **Procesamiento avanzado**: Microcontrolador STM32F429ZI para adquisición y análisis de datos en tiempo real.
- **Sensores ambientales complementarios**: Módulo DHT22 para medición de temperatura y humedad.
- **Almacenamiento local**: Sistema de archivos FAT32 en memoria microSD.
- **Conectividad inalámbrica**: Módulo ESP8266 para transmisión de datos a servidores remotos.
- **Gestión de energía**: Sistema de alimentación con respaldo para operación continua.
- **Sincronización temporal**: RTC DS3231 de alta precisión para registro exacto de mediciones.

## Arquitectura del Sistema

El sistema está estructurado en los siguientes subsistemas principales:

1. **Adquisición de datos**: Sensores SPS30 (material particulado), DHT22 (temperatura/humedad) y DS3231 (reloj de tiempo real).
2. **Procesamiento**: Microcontrolador STM32F429ZI con arquitectura de software modular.
3. **Almacenamiento**: Módulo microSD para registro local de mediciones.
4. **Comunicación**: Módulo ESP8266 para transmisión inalámbrica de datos.
5. **Alimentación**: Fuente S-25-5 con sistema de respaldo para operación continua.

## Estructura del Repositorio

```
├── Hardware/
│   ├── Esquemáticos/        # Diagramas circuitales del sistema
│   ├── PCB/                 # Diseños de circuito impreso
│   └── BOM/                 # Lista de materiales
├── Firmware/
│   ├── Core/                # Código base del sistema
│   ├── Drivers/             # Controladores de periféricos
│   ├── Middleware/          # Capas intermedias (FatFS, etc.)
│   ├── App/                 # Lógica de aplicación
│   │   ├── Acquisition/     # Módulos de adquisición de datos
│   │   ├── Analysis/        # Procesamiento estadístico
│   │   ├── Storage/         # Gestión de almacenamiento
│   │   └── Communication/   # Protocolos de transmisión
│   └── Tests/               # Pruebas unitarias y de integración
├── Documentation/
│   ├── Datasheets/          # Hojas de datos de componentes
│   ├── Protocols/           # Documentación de protocolos implementados
│   ├── UserManual/          # Manual de usuario del sistema
│   └── CalibrationProcedure/# Procedimientos de calibración
└── Tools/
    ├── Calibration/         # Herramientas para calibración
    └── DataAnalysis/        # Scripts para análisis de datos
```

## Tecnologías Implementadas

- **Hardware**: Diseño de PCB multicapa con consideraciones EMI/EMC.
- **Firmware**: Arquitectura de software en capas con patrones "observar y reaccionar" y "segmentación de procesos".
- **Protocolos**: UART, I²C, SPI, y comunicación inalámbrica TCP/IP.
- **Procesamiento de Datos**: Implementación de algoritmos estadísticos para validación y corrección de mediciones.
- **Pruebas**: Framework de pruebas unitarias para validación sistemática de componentes de software.

## Resultados y Validación

El sistema ha sido validado mediante:

- Pruebas de correlación entre sensores redundantes (r > 0.90).
- Comparativa con estaciones de referencia SINCA.
- Análisis de comportamiento en episodios críticos de contaminación (hasta 600 μg/m³).
- Evaluación de completitud de datos (>90%).

## Requisitos de Construcción

### Hardware
- Placa de desarrollo STM32F429ZI Nucleo
- 3x Sensores SPS30
- Módulo RTC DS3231
- Sensor DHT22
- Módulo ESP8266
- Adaptador microSD
- Fuente de alimentación S-25-5

### Software
- STM32CubeIDE 1.13.0
- GCC ARM 10.3
- KiCad 8.0 (para modificación del diseño de PCB)

## Licencia

Este proyecto está disponible bajo licencia [especificar licencia].

## Autor

Mg. Luis Alberto Gómez Parada

## Agradecimientos

Este proyecto fue desarrollado como parte de la Carrera de Especialización en Sistemas Embebidos de la Facultad de Ingeniería de la Universidad de Buenos Aires, bajo la dirección del Ing. Juan Manuel Cruz Beaufrere y la codirección de la Dra. Zoe Fleming.
