# Configuración MCP STDIO en Claude

En esta sección vamos a configurar un servidor MCP basado en **STDIO** para integrarlo con Claude.

---

## 📌 Paso 1: Agregar configuración MCP

Debes copiar el siguiente bloque dentro de la propiedad `mcpServers` en tu archivo de configuración principal de Claude:

```json
"mcpServers": {
  "spring-ai-weather": {
    "command": "java",
    "args": [
      "-Dspring.ai.mcp.server.stdio=true",
      "-Dspring.main.banner-mode=off",
      "-Dlogging.level.root=OFF",
      "-jar",
      "/Users/{nombre-usuario}/Desktop/SpringAI/springai-mcp-stdio-server/target/springai-mcp-stdio-server-0.0.1-SNAPSHOT.jar"
    ]
  }
}
```

---

## ⚠️ Importante

- Reemplaza `{nombre-usuario}` por tu usuario real del sistema.
- Asegúrate de que el `.jar` ya esté generado ejecutando:

```bash
mvn clean package
```

- Verifica que la ruta al `.jar` sea correcta según tu máquina.

---

## 📌 Paso 2: Resultado final del archivo de configuración

Tu archivo completo debería quedar así:

```json
{
  "preferences": {
    "quickEntryShortcut": "double-tap-option",
    "coworkWebSearchEnabled": true,
    "coworkScheduledTasksEnabled": false,
    "ccdScheduledTasksEnabled": false
  },
  "mcpServers": {
    "spring-ai-weather": {
      "command": "java",
      "args": [
        "-Dspring.ai.mcp.server.stdio=true",
        "-Dspring.main.banner-mode=off",
        "-Dlogging.level.root=OFF",
        "-jar",
        "/Users/{nombre-usuario}/Desktop/SpringAI/springai-mcp-stdio-server/target/springai-mcp-stdio-server-0.0.1-SNAPSHOT.jar"
      ]
    }
  }
}
```

---

## 🚀 ¿Qué hace esta configuración?

- Ejecuta tu servidor MCP usando Java en modo STDIO  
- Permite que Claude se comunique directamente con tu aplicación  
- Expone las tools definidas en tu proyecto Spring AI  

---

## 🧠 Nota

STDIO permite comunicación directa entre procesos (sin HTTP), lo que lo hace ideal para integraciones locales rápidas con herramientas como Claude o Codex.
