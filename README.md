# Lab 01 — Cuenta de emergencia (Break-Glass) en Microsoft Entra ID

## Por qué hice este lab
Estoy montando un portfolio práctico de Azure/IAM y, antes de tocar cosas delicadas como **Conditional Access** y **MFA**, quería cubrir lo más básico: **no quedarme fuera del tenant por un error mío**.

Este lab es literalmente “seguro de vida” para cuando estás aprendiendo y pruebas políticas.

## Objetivo
Tener una cuenta de emergencia que me permita recuperar el tenant si:
- me bloqueo por una política de CA mal configurada,
- falla el MFA,
- o accidentalmente dejo fuera a los administradores.

## Qué hice 
1) Creé un usuario dedicado para emergencias: `break-glass emergency account`  
2) Le asigné el rol **Administrador global** (solo para recuperación).  
3) En Conditional Access, lo **excluí** de la política de MFA para evitar un lock-out total.  
4) Deshabilité **Security Defaults** porque en este tenant estoy gestionando la seguridad con CA y me estorbaba para configurar/validar.

> Nota: en mi caso la directiva está en **“Solo informe”** (report-only) mientras reviso que no me bloqueo. La idea es pasarla a **Activado** cuando esté seguro.

## Evidencias (hechas por mí en el portal)

### 1) Usuario break-glass creado
Se ve el usuario creado como *Miembro* (no Guest), lo que permite asignarle roles administrativos.

![Usuario de emergencia](images/01-user-created.png)

### 2) Rol Global Administrator asignado
Se ve la cuenta break-glass dentro del rol **Administrador global**.

![Rol Global Admin](images/02-global-admin.png)

### 3) Exclusión en Acceso Condicional
En la directiva de CA se ve la cuenta break-glass en “usuarios excluidos”.

![Exclusión CA](images/03-ca-exclusion.png)

## Cosas que tuve en cuenta (para que no sea “una cuenta sin MFA y ya”)
- No es una cuenta para el día a día. Es para emergencias.
- Contraseña larga/única y guardada fuera del tenant.
- Sin licencias asignadas.
- Revisión periódica: si hay un inicio de sesión con esta cuenta, se investiga sí o sí.

## Qué diría en una entrevista (como lo explicaría yo)
“Antes de tocar Conditional Access, creo una cuenta break-glass. Le doy Global Admin solo para recuperación y la excluyo de la política de MFA para no depender de CA/MFA en una emergencia. La protejo con controles compensatorios (contraseña offline, cero uso diario y revisión de accesos). Así evito bloquear el tenant por un error de configuración mientras practico.”

