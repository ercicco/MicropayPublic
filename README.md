
# 📄 Documentación del Endpoint `Activate.php`

## 🧩 Descripción General

**MicroPay** es una plataforma de pago interoperable que permite la activación de máquinas mediante billeteras digitales. Nuestros dispositivos se integran fácilmente con equipos que usan fichas, billetes o cospeles, modernizándolos para aceptar pagos digitales.

> 💡 **Ventaja diferencial:** El dispositivo **solo permite mostrar el QR de pago si la máquina está en condiciones de operar**. De lo contrario, el QR no se presenta al usuario, evitando cobros indebidos y mejorando la experiencia del cliente.

---

## 🔗 Detalles del Endpoint

- **URL de Producción:** `https://dominio_correspondiente/Activate.php`
- **Método:** `POST`

---

## 🔐 Autenticación

Este endpoint requiere un token de autenticación válido enviado en el encabezado HTTP.

- **Encabezado obligatorio:**

```http
Authorization: e44601d1fbdc632d231ce657f0f3a443
```

> 🔒 *El token será provisto por Micropay en el momento de la integración.*

---

## 📥 Parámetros

| Parámetro | Tipo   | Obligatorio | Descripción                                      |
|-----------|--------|-------------|--------------------------------------------------|
| `pid`     | string | Sí          | Identificador único del dispositivo a activar.   |

---

## ✅ Respuestas

### ✔️ Éxito

```json
{
  "status": "ok",
  "message": "Activación exitosa para el pid proporcionado."
}
```

### ❌ Token inválido

```json
{
  "status": "error",
  "message": "Token de autenticación inválido."
}
```

### ❌ `pid` faltante o inválido

```json
{
  "status": "error",
  "message": "El parámetro 'pid' es obligatorio y debe ser válido."
}
```

### ❌ Error interno

```json
{
  "status": "error",
  "message": "Ocurrió un error inesperado. Por favor, intente nuevamente más tarde."
}
```

---

## 🧪 Ejemplo de uso

```bash
curl -X POST https://dominio_correspondiente/Activate.php \
  -H "Authorization: e44601d1fbdc632d231ce657f0f3a443" \
  -d "pid=123456"
```

---

## 📌 Consideraciones

1. El parámetro `pid` debe pertenecer a un dispositivo registrado y autorizado.
2. El token será provisto por Micropay en el momento de la integración.
3. Si la máquina no está en condiciones, el QR de pago no se mostrará, evitando pagos innecesarios.

---

## ⚠️ Notas Finales

Esta documentación es confidencial y propiedad intelectual de **MicroPay**. Está destinada exclusivamente a socios tecnológicos y desarrolladores autorizados. Queda prohibida su reproducción o distribución total o parcial sin el consentimiento expreso de la empresa.

📧 Para dudas o consultas técnicas, por favor contacte al sector de **soporte técnico o desarrollo** de MicroPay.
