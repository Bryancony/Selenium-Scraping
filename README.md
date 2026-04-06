# Selenium-Scraping
## Objeto del Trabajo

Implementar dos escenarios de automatización web con Selenium:
1. **Opción A:** Reconocimiento automatizado con Shodan
2. **Opción C:** Automatización de login con fuerza bruta controlada

---

## Opción A: Reconocimiento Automatizado (Shodan + Scraping)

### Descripción
Este script automatiza la explotación de información pública en Shodan mediante:
- Login automático en la plataforma
- Ejecución de 3 búsquedas distintas
- Extracción de datos: consulta, título, URL
- Captura automática de pantalla de resultados

### Archivo
`opcion_a_shodan.py`

### Requisitos Previos
- Cuenta activa en Shodan (https://www.shodan.io)
- Credenciales válidas (email + contraseña)

### Cómo Usar
```bash
# Opción 1: Variables de entorno
set SHODAN_USER=tu_email@example.com
set SHODAN_PASSWORD=tu_contraseña
python opcion_a_shodan.py

# Opción 2: Editar el archivo
# Reemplaza USER y PASSWORD en el script directamente
python opcion_a_shodan.py
```

### Búsquedas Configuradas
- `Apache` - Búsqueda de servidores Apache
- `nginx` - Búsqueda de servidores nginx
- `IIS` - Búsqueda de servidores IIS de Microsoft

### Salida Esperada
```
============================================================
SCRAPING CON SELENIUM - OPCIÓN A: SHODAN
============================================================

[*] Iniciando sesión en Shodan...
    [+] Usuario ingresado
    [+] Contraseña ingresada
    [+] Botón de login presionado
    [+] Login exitoso!

[*] Búsqueda #1: 'Apache'
    [+] Búsqueda 'Apache' ingresada
    [+] Búsqueda enviada
    [+] Resultados cargados
    [+] Título: Apache - Shodan
    [+] URL: https://www.shodan.io/search?query=Apache
    [+] Captura guardada: screenshots/shodan_search_1_Apache.png

[SIMILAR PARA LAS OTRAS BÚSQUEDAS]

============================================================
RESUMEN DE RESULTADOS
============================================================

Búsqueda #1:
  Query: Apache
  Título: Apache - Shodan
  URL: https://www.shodan.io/search?query=Apache
  Screenshot: screenshots/shodan_search_1_Apache.png

[+] Total de búsquedas exitosas: 3/3
[+] Todas las capturas guardadas en la carpeta 'screenshots'
```

### Evidencias Generadas
- 3 screenshots automáticos en `screenshots/`
- Salida por consola con detalles de cada búsqueda
- URL final y título de cada página

---

## Opción C: Automatización de Login (Fuerza Bruta Controlada)

### Descripción
Este script automatiza intentos de login con credenciales en Herokuapp:
- Prueba de múltiples combinaciones usuario/contraseña
- Detección automática de login exitoso
- Captura de pantalla de cada intento
- Reporte de intentos fallidos y exitosos

### Archivo
`opcion_c_bruteforce.py`

### Destino de Pruebas
`https://the-internet.herokuapp.com/login`

**Nota:** Este sitio está diseñado específicamente para prácticas de seguridad y contiene vulnerabilidades intencionadas.

### Credenciales de Prueba
```
1. tomsmith:wrong              → Fallido
2. admin:admin                 → Fallido
3. tomsmith:SuperSecretPassword! → EXITOSO ✓
4. user:password               → Fallido
5. test:test123                → Fallido
```

### Cómo Usar
```bash
# Activar entorno virtual
.\venv\Scripts\activate

# Ejecutar script
python opcion_c_bruteforce.py
```

### Salida Esperada
```
======================================================================
AUTOMATIZACIÓN DE LOGIN - OPCIÓN C: FUERZA BRUTA CONTROLADA
======================================================================
Objetivo: https://the-internet.herokuapp.com/login
Total de intentos: 5

[*] Intento #1: tomsmith:wrong
    [+] Página de login cargada
    [+] Usuario: tomsmith
    [+] Contraseña: *****
    [+] Botón de login presionado
    [✗] Login fallido
    [+] Mensaje: Your password is invalid!
    [+] Screenshot: screenshots/intento_1_tomsmith.png

[*] Intento #2: admin:admin
    [+] Página de login cargada
    [+] Usuario: admin
    [+] Contraseña: *****
    [+] Botón de login presionado
    [✗] Login fallido
    [+] Mensaje: Your username is invalid!
    [+] Screenshot: screenshots/intento_2_admin.png

[*] Intento #3: tomsmith:SuperSecretPassword!
    [+] Página de login cargada
    [+] Usuario: tomsmith
    [+] Contraseña: **********************
    [+] Botón de login presionado
    [✓] LOGIN EXITOSO!
    [+] Mensaje: You logged into a secure area!
    [+] Screenshot: screenshots/intento_3_tomsmith.png

[... CONTINUACIÓN CON INTENTOS 4 Y 5 ...]
