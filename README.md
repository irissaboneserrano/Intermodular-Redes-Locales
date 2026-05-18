# Intermodular-Redes-Locales
# Proyecto Intermodular
## Redes Locales
### 1º SMR

**Alumno:** Iris Saboné Serrano

---

## 1. Análisis de red

La empresa **IS PixelEstudio** cuenta con **6 equipos** destinados a diferentes funciones dentro del estudio: **administración, gerente, dos de diseño gráfico, marketing** y **soporte técnico.**

Además dispone de una **impresora** de red que será utilizada por todos los empleados.

La empresa necesita una **red local** que permita la comunicación entre los equipos, el acceso a **internet** y la **compartición** de **archivos**, ya que los diseñadores trabajan con archivos pesados que deben ser accesibles en varios equipos.

Está distribuida en una única planta, lo que facilita la instalación de la red y reduce costes.

Se han definido diferentes zonas de trabajo. En la zona principal se encuentran los equipos de **administración** y del **gerente** destinados a tareas de gestión y organización de la empresa. La **impresora** se encuentra en una zona común accesible para todos los empleados.

En otra zona se ubican los equipos de **diseño** y **marketing**, ya que comparten archivos de forma constante y necesitan trabajar de forma colectiva.

Además, se ha definido una zona técnica donde se encuentra el **equipo** del **técnico** informático junto con los dispositivos de red, como el router y el switch, situados en un pequeño armario de comunicaciones desde el cual se distribuye la conexión al resto de equipos. Esta distribución permite una **organización eficiente** del espacio y optimiza el funcionamiento de la red local.

---

## 2. Diseño de la red

La red de la empresa se ha organizado en diferentes zonas de trabajo según las funciones de cada departamento.

Por un lado se encuentran los equipos de **diseño** y **marketing** en la misma zona, ya que lo más seguro es que **compartan archivos** constantemente entre ellos y trabajen de forma colaborativa.

En otra zona están los equipos de **administración** y **gerencia**, que se dedican a tareas de gestión y organización.

El **técnico** se encuentra en una zona **cercana** al área de **comunicaciones** para facilitar el mantenimiento.

Y por último una **impresora** en un **área** totalmente **accesible**, de manera que todos los usuarios de la empresa puedan utilizarla sin problema.

---

## 3. Plan de direccionamiento IP

**Rango de red:** 192.168.1.0 – 192.168.1.255

**Máscara de red:** 255.255.255.0

**Gateway:** 192.168.1.1

### Asignación de IP

| Dispositivo | Dirección IP |
|---|---|
| Administración | 192.168.1.10 |
| Gerente | 192.168.1.11 |
| Diseño1 | 192.168.1.12 |
| Diseño2 | 192.168.1.13 |
| Marketing | 192.168.1.14 |
| Técnico | 192.168.1.15 |
| Impresora | 192.168.1.20 |

---

## 4. Servicios de red básicos

**Compartición de archivos**
- Permite que los dos equipos de diseño trabajen sobre los mismos archivos
- Acceso a carpetas compartidas en red

**Compartición de la impresora**
- La impresora está disponible para todos los equipos
- No necesita conexión directa por cable a cada ordenador

**Acceso a Internet**
- Todos los equipos acceden a internet a través del router
- El router actúa como puerta de enlace

**Usuarios en red**
- Cada trabajador tiene su usuario
- Permite controlar accesos y permisos

---

## 5. Simulación o explicación de funcionamiento

Antes de empezar a **configurar** cada **dispositivo**, es necesario **conectarlos**, para ello se utiliza el **cable directo** y se conecta con el **puerto disponible** de cada uno.

### Configuración del router

```
Router(config)#interface gig0/0
Router(config-if)#ip address 192.168.1.1 255.255.255.0
```

En cuanto a los **equipos**, para todos es el **mismo proceso**, solo que asignando una **IP distinta** a cada uno, por ejemplo en el de **Administración:**

| Campo | Valor |
|---|---|
| Interface | FastEthernet0 |
| IP Configuration | Static |
| IPv4 Address | 192.168.1.10 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 192.168.1.1 |

Para hacer una **comprobación** de la **conectividad** entre dos equipos, en uno de ellos se accede al equipo → Desktop → **Command Prompt** y se hace **ping** al otro equipo, por ejemplo entre los de **diseño**:

```
C:\>ping 192.168.1.13

Pinging 192.168.1.13 with 32 bytes of data:
Reply from 192.168.1.13: bytes=32 time=2ms TTL=128
Reply from 192.168.1.13: bytes=32 time<1ms TTL=128
Reply from 192.168.1.13: bytes=32 time<1ms TTL=128
Reply from 192.168.1.13: bytes=32 time<1ms TTL=128

Ping statistics for 192.168.1.13:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 2ms, Average = 0ms
```

Todos los **equipos** están conectados a través de un **switch**, por lo tanto existe una **comunicación** entre ellos dentro de la **red local.**

Los equipos podrán **compartir archivos** y todo lo necesario, así como acceder a **internet** a través del **router**.
