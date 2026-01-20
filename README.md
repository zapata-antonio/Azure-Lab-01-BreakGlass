# 🧪Lab 01 — Continuidad del Tenant (Cuenta de Emergencia - Break-Glass)

## 🎯 Objetivo
Garantizar el acceso administrativo al tenant de Azure en caso de fallo del MFA, bloqueo accidental del administrador o caída del sistema de identidad.

Este laboratorio implementa el patrón profesional **Break-Glass Account** recomendado por Microsoft.

---

## 🧩 Escenario
La empresa **Zapata-Cloud** necesita proteger su tenant frente a bloqueos totales por políticas de seguridad mal configuradas (MFA, Conditional Access, Identity Protection).

Si todos los administradores quedaran bloqueados, la empresa perdería acceso a su infraestructura Cloud.

Para evitarlo, se diseña una cuenta de emergencia altamente protegida, sin MFA y excluida de políticas de acceso condicional.

---

## 🛠️ Tareas realizadas
1. Creación de una cuenta de emergencia (Break-Glass).
2. Asignación del rol **Administrador global**.
3. Exclusión de la cuenta en políticas de Acceso Condicional (MFA).
4. Definición de un protocolo de uso seguro.

🔐 Los valores de seguridad predeterminados (Security Defaults) fueron deshabilitados para evitar conflictos y permitir la gestión de la seguridad mediante políticas de Acceso Condicional.

---
## 📸 Evidencias

### 1️⃣ Cuenta break-glass creada
La cuenta **emergencia.admin** existe en el tenant Zapata-Cloud y es de tipo *Member* (no Guest), lo que permite asignarle roles administrativos.

![Usuario de emergencia](images/01-user-created.png)

---

### 2️⃣ Rol Global Administrator asignado
La cuenta break-glass tiene el rol **Global Administrator**, lo que le permite recuperar el tenant ante cualquier bloqueo.

![Rol Global Admin](images/02-global-admin.png)

---

### 3️⃣ Exclusión en Acceso Condicional
La cuenta de emergencia está excluida de las políticas de Acceso Condicional (MFA), evitando un bloqueo total del tenant.

![Exclusión CA](images/03-ca-exclusion.png)
---

## ✅ Checklist de control

> Se marca solo tras validar cada punto en el portal.

- [X] La política de Acceso Condicional exige MFA a usuarios normales  
- [X] La cuenta break-glass está excluida  
- [X] La cuenta break-glass no se usa para trabajo diario  

---

## 🧠 Buenas prácticas aplicadas
- Contraseña larga y almacenada fuera del tenant  
- No se asignan licencias  
- No se usa para login diario  
- Se revisa periódicamente  

---

## 🗣️ Qué explicaría en una entrevista

> “Para evitar un lock-out total del tenant, implemento cuentas break-glass con rol Global Admin, excluidas de Acceso Condicional y MFA, protegidas con contraseña fuerte y uso controlado. Esto garantiza la continuidad operativa incluso si el sistema de identidad falla.”

---

