# Plan de Prevención de Recaída

PWA en español para acompañar el tratamiento de adicciones. Incluye señales de alerta, protocolo de crisis, técnicas de regulación, red de apoyo, registros diarios y evaluaciones momentáneas (EMA).

## Uso local

Abra el proyecto desde un servidor web local; no abra los archivos con `file://`, porque las PWA y Supabase requieren un origen web. Por ejemplo:

```powershell
python -m http.server 8080
```

Después visite `http://localhost:8080`. En un teléfono, publíquelo con HTTPS para poder instalarlo como aplicación.

## Configuración de Supabase

1. Cree un proyecto en Supabase y cambie `SUPABASE_URL` y `SUPABASE_KEY` en `index.html` y `panel-clinico.html`.
2. Cree las tablas `registros` y `ema` con las columnas que envía la aplicación.
3. Active Row Level Security (RLS). No use una clave `service_role` en archivos del navegador.
4. Cree una cuenta de Supabase Auth para cada terapeuta autorizado. El panel clínico usa correo y contraseña de Supabase; ya no guarda una contraseña en el código.
5. Defina políticas RLS que permitan al paciente insertar sus propios registros y solamente a usuarios clínicos autorizados leerlos. Para uso real con datos de salud, conviene vincular registros a un identificador de paciente autenticado, no al nombre.

## PWA y sin conexión

El servicio de trabajo guarda la interfaz, iconos y video para que las herramientas educativas sigan disponibles sin conexión. Los registros se almacenan localmente primero; cuando Supabase esté configurado se intentan enviar en ese momento.

## Importante

Esta herramienta es apoyo y no sustituye atención profesional ni servicios de emergencia. Revise y adapte los teléfonos de crisis, el contacto clínico y el contenido a su país, protocolo y población antes de publicar.
