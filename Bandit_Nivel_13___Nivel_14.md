# 🔐 Bandit Level 13 → 14

<div align="center">

![Nivel](https://img.shields.io/badge/Nivel-13_→_14-blue?style=for-the-badge)
![Dificultad](https://img.shields.io/badge/Dificultad-Medio-orange?style=for-the-badge)

**Objetivo:** Usar clave SSH privada para conectarse

[🌐 Desafío Original](https://overthewire.org/wargames/bandit/bandit14.html) | [📺 Video Tutorial](#)

</div>

---


Para usar la clave privada y entrar a **bandit14**, sigue estos pasos detallados:

---

## **1️⃣ Verifica que tienes la clave privada**

Ejecuta:

```bash
ls -l
```

Si ves `sshkey.private` en la lista, significa que la clave está en tu directorio actual.

Si no la ves, usa:

```bash
cat sshkey.private
```

Para asegurarte de que la clave está correctamente guardada.

---

## **2️⃣ Corrige los permisos de la clave (si es necesario)**

El sistema no te permitirá usar la clave si tiene permisos muy abiertos. Ajusta los permisos ejecutando:

```bash
chmod 600 sshkey.private
```

Esto restringe el acceso para que solo tú puedas leerla.

---

## **3️⃣ Usa la clave privada para conectarte a bandit14**

Ejecuta el siguiente comando:

```bash
ssh -i sshkey.private bandit14@localhost
```

📌 **Explicación**:

- `ssh` → Inicia una conexión SSH.
- `-i sshkey.private` → Usa la clave privada para autenticarte.
- `bandit14@localhost` → Indica que quieres conectarte como `bandit14` en `localhost` (la misma máquina).

---

## **4️⃣ Si hay un error sobre "Host authenticity"**

Si ves un mensaje preguntando:

```plaintext
The authenticity of host 'localhost (127.0.0.1)' can't be established.
Are you sure you want to continue connecting (yes/no)?
```

Escribe:

```plaintext
yes
```

Y presiona **Enter**.

---

## **5️⃣ Si sigues teniendo errores**

Si ves algo como **"Permission denied (publickey)"**, intenta forzar la conexión con este comando:

```bash
ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no -i sshkey.private bandit14@localhost
```

📌 **Explicación de los parámetros extra**:

- `-o UserKnownHostsFile=/dev/null` → Evita problemas con el archivo de hosts conocidos.
- `-o StrictHostKeyChecking=no` → No pregunta si confías en la conexión.

---

## **6️⃣ Obtener la contraseña de bandit14**

Si logras conectarte correctamente, ejecuta este comando para ver la contraseña del siguiente nivel:

```bash
cat /etc/bandit_pass/bandit14
```

---


---

<div align="center">

**[⬅️ Nivel Anterior](./Bandit_Nivel_12___Nivel_12.md)** | **[🏠 Volver al README](./README.md)** | **[➡️ Siguiente Nivel](./Bandit_Nivel_14___Nivel_15.md)**

</div>
