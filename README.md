# 🚀 Monitoreo LLM UXD

**LLM Endpoint Tester & Benchmarker** — Herramienta ligera para probar y medir la velocidad de respuesta de agentes de IA alojados en n8n, AWS Lambda, o cualquier webhook.

<p align="center">
  <a href="https://uxdigitalchile.github.io/Monitoreo_LLM_UXD/">
    <img src="https://img.shields.io/badge/🚀_ABRIR_MONITOR-Probar_Ahora-6366F1?style=for-the-badge&logoColor=white" alt="Abrir Monitor">
  </a>
</p>

> 📌 **Demo en vivo:** [https://uxdigitalchile.github.io/Monitoreo_LLM_UXD/](https://uxdigitalchile.github.io/Monitoreo_LLM_UXD/)

---

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat&logo=tailwind-css&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-green.svg)

---

## 📋 Descripción

Herramienta de archivo único (HTML) diseñada para realizar pruebas de rendimiento y funcionalidad de endpoints LLM. Ideal para:

- ✅ Probar webhooks de **n8n** con AI Agents
- ✅ Validar endpoints de **AWS Lambda** o API Gateway
- ✅ Medir latencia de cualquier API REST que responda JSON
- ✅ Debugging rápido sin necesidad de Postman o herramientas complejas

---

## ✨ Características

| Característica | Descripción |
|----------------|-------------|
| 🎨 **Interfaz Moderna** | Diseño dark mode con Tailwind CSS vía CDN |
| ⚡ **Métricas en Tiempo Real** | Latencia (ms), Status Code, Tamaño de respuesta |
| 🔐 **Autenticación** | Soporte para Bearer Token opcional |
| 📝 **JSON Editable** | Template personalizable con placeholder `{{message}}` |
| 📊 **Historial** | Registro de las últimas 10 requests |
| 💾 **Persistencia** | Guarda configuración en localStorage |
| 📋 **Copiar Respuestas** | Botones para copiar respuesta y JSON raw |
| ⌨️ **Atajos** | `Ctrl+Enter` para enviar rápidamente |

---

## 🖼️ Preview

```
┌─────────────────────────────────────────────────────────────────┐
│  ⚡ LLM Endpoint Tester                              ● Éxito   │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  [Endpoint URL: https://n8n.ejemplo.com/webhook/xxx/chat    ]  │
│                                                                 │
│  [User Message / Query                                       ]  │
│                                                                 │
│  ┌─ JSON Body Template ──────────────────────────────────────┐ │
│  │ {                                                         │ │
│  │   "action": "sendMessage",                                │ │
│  │   "sessionId": "test-001",                                │ │
│  │   "chatInput": "{{message}}"                              │ │
│  │ }                                                         │ │
│  └───────────────────────────────────────────────────────────┘ │
│                                                                 │
│  [ 🚀 Enviar Request ]                                         │
│                                                                 │
├─────────────────────────────────────────────────────────────────┤
│  Latencia: 3215ms  │  Status: 200  │  Tamaño: 1.2KB            │
├─────────────────────────────────────────────────────────────────┤
│  Respuesta del Agente:                                         │
│  "¡Hola! Soy tu asistente de biología..."                      │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🚀 Instalación

No requiere instalación. Es un archivo HTML autocontenido.

### Opción 1: Descarga directa
```bash
# Clonar repositorio
git clone https://github.com/uxdigitalchile/Monitoreo_LLM_UXD.git

# Abrir en navegador
open index.html
```

### Opción 2: Uso directo
1. Descarga `Monitoreo_LLM_UXD.html`
2. Abre el archivo en cualquier navegador moderno
3. ¡Listo para usar!

---

## 📖 Uso

### Configuración Básica

1. **Endpoint URL**: Ingresa la URL de tu webhook
   ```
   https://tu-n8n.cloud/webhook/xxx-xxx/chat
   ```

2. **Bearer Token** (opcional): Si tu endpoint requiere autenticación

3. **JSON Body**: Ajusta el template según tu API
   ```json
   {
     "action": "sendMessage",
     "sessionId": "test-session-001",
     "chatInput": "{{message}}"
   }
   ```

4. **User Message**: Escribe tu mensaje de prueba

5. Click en **Enviar Request** o presiona `Ctrl+Enter`

### Ejemplo para n8n Chat Trigger

```json
{
  "action": "sendMessage",
  "sessionId": "mi-sesion-123",
  "chatInput": "{{message}}"
}
```

### Ejemplo para API OpenAI-Compatible

```json
{
  "model": "gpt-4",
  "messages": [
    {"role": "user", "content": "{{message}}"}
  ]
}
```

### Ejemplo Genérico

```json
{
  "query": "{{message}}"
}
```

---

## 🔧 Configuración para n8n

Si usas **n8n** con el nodo `Chat Trigger`, configura así:

| Campo | Valor |
|-------|-------|
| **URL** | `https://[tu-dominio]/webhook/[webhookId]/chat` |
| **Método** | `POST` |
| **Content-Type** | `application/json` |
| **Body** | Ver ejemplo arriba |

> 💡 **Tip**: El `sessionId` permite mantener contexto entre mensajes. Cámbialo para iniciar conversaciones nuevas.

---

## 📊 Interpretación de Métricas

| Métrica | Descripción | Valores Típicos |
|---------|-------------|-----------------|
| **Latencia** | Tiempo total de respuesta | 500ms - 5000ms para LLMs |
| **Status 200** | Éxito | ✅ Todo bien |
| **Status 400** | Error de cliente | ⚠️ Revisa el JSON body |
| **Status 401/403** | No autorizado | 🔐 Verifica el token |
| **Status 500** | Error del servidor | ❌ Revisa logs del endpoint |

---

## 🛠️ Tecnologías

- **HTML5** — Estructura
- **Tailwind CSS** (CDN) — Estilos
- **JavaScript Vanilla** — Lógica
- **Fetch API** — Requests HTTP
- **LocalStorage** — Persistencia de configuración

---

## 📁 Estructura del Proyecto

```
Monitoreo_LLM_UXD/
│
├── index.html    # Aplicación completa (único archivo)
├── README.md     # Este archivo
└── LICENSE       # Licencia MIT
```

---

## 🤝 Contribuciones

¡Las contribuciones son bienvenidas! 

1. Fork el proyecto
2. Crea tu feature branch (`git checkout -b feature/NuevaFuncion`)
3. Commit tus cambios (`git commit -m 'Add: nueva función'`)
4. Push al branch (`git push origin feature/NuevaFuncion`)
5. Abre un Pull Request

---

## 📝 Changelog

### v1.0.0 (2025)
- ✨ Release inicial
- 🎨 Interfaz dark mode con Tailwind CSS
- ⚡ Métricas de latencia y status
- 📝 JSON body editable con placeholder
- 📊 Historial de requests
- 💾 Persistencia en localStorage

---

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Ver el archivo [LICENSE](LICENSE) para más detalles.

---

## 👤 Autor

**UXDigital Chile**

- 🌐 Website: [uxdigital.cl](https://uxdigital.cl)
- 📧 Email: contacto@uxdigital.cl

---

## ⭐ ¿Te fue útil?

Si esta herramienta te ayudó, considera darle una ⭐ en GitHub.

---

<p align="center">
  Hecho con ❤️ para la comunidad de desarrolladores de IA
</p>
