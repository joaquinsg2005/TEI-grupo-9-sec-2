# Sistema IoT de Monitoreo de Calidad del Aire

Monitor de calidad del aire en salas basado en **ESP32-S3** y sensor **MQ-135**,
con semáforo LED de alerta, dashboard web en tiempo real y persistencia de datos
en la nube (Firebase Realtime Database).

**Grupo 9 — Sección 2 · TEI201 — Taller de Diseño en Ingeniería (UAI)**

---

## Integrantes
Benjamín Pomar
Joaquín Sotomayor
Martin Williamson
Valeria Alfaro
---

## Problema que resuelve

En salas cerradas, la mala ventilación deteriora la calidad del aire (acumulación
de CO₂ y gases), lo que afecta la concentración y el bienestar de las personas sin
que estas lo perciban. En el Avance 1 identificamos que existían variables que afectaban 
significativamente el desempeño y salud de los estudiantes en horas de alta afluencia y 
coincidentes con temperaturas más bajas lo que propicia la concentración del aire. 
Este sistema mide la calidad del aire de forma continua,
la clasifica con un semáforo visible, guarda el histórico y avisa cuándo conviene
ventilar.

---

## Cómo funciona (ciclo de datos)

1. **Captura:** el MQ-135 mide la calidad del aire cada 3 segundos (promedio de 10
   lecturas para reducir ruido).
2. **Información:** el valor se clasifica en un semáforo — verde (buena), amarillo
   (regular) o rojo (mala) — según umbrales calibrados con mediciones reales.
3. **Persistencia:** los datos se envían a Firebase Realtime Database; el valor en
   vivo se actualiza cada 3 s y el histórico se guarda cada 60 s.
4. **Decisión:** el LED rojo se enciende como alerta cuando la calidad supera el
   umbral, indicando que se debe ventilar la sala.

---

## Componentes necesarios (hardware)

| Componente | Cantidad | Detalle |
|----------------------|----------|------------------------------------|
| ESP32-S3             | 1        | Microcontrolador con WiFi |
| Sensor MQ-135        | 1        | Sensor de calidad de aire / gases |
| Semáforo LED rojo / amarillo / verde | 1 | Semáforo de estado |
| Cables jumper hembra-hembra  | —        | Montaje |
| Batería 18650        | 1        |   Fuente de energía  |
| Battery shield       | 1        |  Contenedor batería  |

> El BOM completo con costos está en `BOM.md`.

---

## Cómo replicar el proyecto

### 1. Firmware (ESP32-S3)
1. Instalar el **Arduino IDE** y el soporte para placas **ESP32** (Arduino-ESP32).
2. Instalar la librería **FirebaseClient** (de Mobizt) desde el Library Manager.
3. Abrir `firmware/sensor_calidad_aire_3.ino`.
4. Completar las credenciales del WiFi (hotspot) y de Firebase.
5. Seleccionar la placa *ESP32S3 Dev Module* y el puerto correcto, y subir el código.

### 2. Firebase
1. Crear un proyecto en [Firebase](https://console.firebase.google.com).
2. Activar **Realtime Database** (modo de prueba) y **Authentication** (Email/Password).
3. Copiar la configuración del proyecto al firmware y al dashboard.

### 3. Dashboard
- Abrir `dashboard/dashboard_historico.html` en un navegador.
- Pegar la configuración de Firebase en el bloque `firebaseConfig`.
- Muestra el estado en vivo y las tendencias (última hora / 24 h / 7 días).

---

## Estructura del repositorio

```
TEI-grupo-9-sec-2/
├── README.md
├── FUENTES.md
├── firmware/
│   └── sensor_calidad_aire_3.ino
├── hardware/
│   ├── esquematico.pdf
│   └── BOM.xlsx
├── diseño-3d/
│   ├── encapsulado.f3d
│   ├── planos.pdf
│   └── renders/
├── testing/
│   └── protocolo_pruebas.pdf
├── dashboard/
│   └── dashboard_historico.html
└── docs/
    └── reporte_final.pdf
```

---

## Integridad académica

Las librerías, el código externo y los usos de IA están declarados en
[`FUENTES.md`](./FUENTES.md).
