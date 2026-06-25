# BOM — Lista de Materiales

Proyecto: **Sistema IoT de Monitoreo de Calidad del Aire**
Grupo 9 — Sección 2 · TEI201

> Precios **estimados** referenciales del mercado chileno (CLP), junio 2026.
> Reemplazar por los valores reales de boleta si están disponibles.

| # | Componente | Cant. | Especificación | Costo unitario (CLP) | Costo total (CLP) |
|---|------------------------------|:----:|---------------------------------------------|---------------------:|------------------:|
| 1 | ESP32-S3 DevKit | 1 | Microcontrolador con WiFi 2.4 GHz, ADC 12-bit | 10.000 | 10.000 |
| 2 | Sensor MQ-135 | 1 | Sensor de calidad de aire / gases, salida analógica, alimentación 5 V | 3.500 | 3.500 |
| 3 | LED 5 mm rojo | 1 | Indicador semáforo, ~2 V / 20 mA | 150 | 150 |
| 4 | LED 5 mm amarillo | 1 | Indicador semáforo, ~2 V / 20 mA | 150 | 150 |
| 5 | LED 5 mm verde | 1 | Indicador semáforo, ~2 V / 20 mA | 150 | 150 |
| 6 | Resistencia 220 Ω | 3 | 1/4 W, limitadora de corriente de los LEDs | 50 | 150 |
| 7 | Resistencia 10 kΩ | 1 | 1/4 W, divisor de tensión (AOUT del MQ-135) | 50 | 50 |
| 8 | Resistencia 20 kΩ | 1 | 1/4 W, divisor de tensión (AOUT del MQ-135) | 50 | 50 |
| 9 | Shield de batería 18650 | 1 | Módulo de carga + boost a 5 V | 4.000 | 4.000 |
| 10 | Batería 18650 | 1 | Li-ion 3.7 V, ~2200 mAh | 3.000 | 3.000 |
| 11 | Protoboard | 1 | 830 puntos | 2.500 | 2.500 |
| 12 | Cables jumper (set) | 1 | ~40 unidades, macho-macho / macho-hembra | 2.000 | 2.000 |
| | | | | **TOTAL** | **25.700** |

---

## Justificación de componentes (resumen)

- **ESP32-S3:** elegido por su WiFi integrado (necesario para enviar datos a Firebase), ADC de 12 bits para leer el sensor analógico y suficiente memoria para el servidor web local.
- **MQ-135:** sensor de bajo costo sensible a gases asociados a mala calidad del aire (CO₂, amoníaco, humo), adecuado para monitoreo en interiores.
- **Semáforo LED:** convierte la lectura en una señal visual inmediata e interpretable (decisión de ventilar).
- **Shield + batería 18650:** permiten operación autónoma en campo, sin depender de estar conectado al PC.
- **Divisor de tensión:** protege el ADC del ESP32-S3 (máx. 3.3 V) de la salida del MQ-135 alimentado a 5 V.

> Nota: el costo total es bajo (~$25.700 CLP), lo que respalda la viabilidad económica del prototipo para replicación.
