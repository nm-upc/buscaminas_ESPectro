# 💣 Buscaminas

Implementación del Buscaminas clásico para la consola portátil ESPectro (ESP32-S3).

Parte del proyecto ESPectro — [base_espectro](https://github.com/bf-upc/base_espectro)

## Descripción

Buscaminas es una adaptación del clásico juego de lógica para la plataforma ESPectro. El objetivo es descubrir todas las casillas seguras del tablero evitando las minas ocultas. Cada partida genera una distribución aleatoria de minas y garantiza que el primer movimiento sea seguro.

El juego incluye sistema de banderas, almacenamiento de récords, historial de partidas y soporte para actualización OTA mediante el Game Loader integrado en ESPectro.

## Controles

| Control | Acción |
|----------|----------|
| Joystick | Mover el cursor por el tablero |
| Pulsación del joystick (SW) | Colocar o quitar bandera |
| Botón A | Descubrir casilla |
| Botón B | Salir de la partida |
| Botón B (menú principal) | Acceder al Game Loader |

## Mecánica de juego

- Tablero de **10 × 13 casillas**.
- **15 minas** distribuidas aleatoriamente.
- El primer movimiento nunca contiene una mina.
- Descubre todas las casillas seguras para ganar.
- Marca posibles minas utilizando banderas.
- Al descubrir una mina, la partida termina inmediatamente.

## Sistema de puntuación

- +1 punto por cada casilla segura descubierta.
- La puntuación máxima corresponde a descubrir todas las casillas libres del tablero.
- El récord se guarda automáticamente en la memoria flash (NVS).
- El historial de las últimas 20 partidas es accesible desde el dashboard web.

## Dashboard

Con la consola encendida, conéctate a la red WiFi **ESPectro**:

**SSID:** `ESPectro`  
**Contraseña:** `gameloader`

Abre en tu navegador:

```text
http://192.168.4.1
```

Desde el dashboard podrás:

- Consultar récords y estadísticas.
- Ver el historial de partidas.
- Monitorizar información del sistema.
- Instalar nuevas versiones del juego mediante OTA.
- Gestionar otros juegos compatibles con ESPectro.

## Audio

El juego utiliza salida de audio I2S para reproducir:

- Sonido de derrota al activar una mina.
- Melodía de victoria al completar el tablero.
- Sonido de inicio de la consola ESPectro.

## Compilar y flashear

```bash
git clone https://github.com/bf-upc/base_espectro
cd base_espectro
pio run --target upload
```

## Requisitos

- PlatformIO
- ESP32-S3
- Librería `lovyan03/LovyanGFX @ ^1.1.12`

## Características

- Interfaz gráfica optimizada para pantalla ILI9488.
- Control mediante joystick analógico.
- Sistema de banderas.
- Generación aleatoria de minas.
- Primer movimiento protegido.
- Guardado automático de récords.
- Historial de partidas.
- Dashboard web integrado.
- Actualización OTA mediante Game Loader.
- Efectos de sonido mediante I2S.
- Integración completa con la plataforma ESPectro.

## Firmware

El binario compilado se encuentra normalmente en:

```text
.pio/build/rymcu-esp32-s3-devkitc-1/firmware.bin
```

Este archivo puede cargarse directamente desde el Game Loader sin necesidad de utilizar conexión USB.

## Proyecto ESPectro

ESPectro es una consola portátil basada en ESP32-S3 diseñada para desarrollar, distribuir y ejecutar videojuegos independientes mediante actualizaciones OTA y un sistema de gestión integrado.
