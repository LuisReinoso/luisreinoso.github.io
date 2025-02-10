---
title: Cómo utilizar MCP Server con Supabase y Cursor
date: 2024-02-09 19:46:00 -05:00
permalink: "/how-to-use-mcp-server-supabase/"
categories:
- mcp-server
- supabase
- cursor
- composer
- agente
- normal
- query string
- postgres
- mcp server
tags:
- mcp-server
- supabase
- cursor
- composer
- agente
- normal
- query string
- postgres
- mcp server
layout: post
---

## Introducción

MCP Server es un protocolo open source para conectar diversas plataformas para alimentar un modelo largo de lenguaje.

En este caso, vamos a utilizar Supabase como base de datos y Cursor para usarlo en Composer, sea en modo agente o normal.

## Instalación

Para ellos vamos a clonar el repositorio de [MCP Server](https://github.com/modelcontextprotocol/servers).

```bash
git clone git@github.com:modelcontextprotocol/servers.git
```

Ir a la carpeta de supabase.

```bash
cd servers/postgres/src/
```

Instalar las dependencias.

```bash
pnpm install
```

Construir el proyecto.

```bash
pnpm build
```

## Instalación en Cursor

Para ello vamos a Cursor donde puedes agregar un MCP server de la siguiente manera.

Copia el path hasta el archivo `index.js` del MCP Server que acabamos de construir.

```bash
/Users/juanpablonunez/Documents/modelcontextprotocol/servers/postgres/src/index.js
```

Ve a la configuración de Cursor > Features > MCP Server

Click en "add new MCP server"

![image](/static/img/posts/add-new-mcp-server.png)

Selecciona el tipo de servidor "command"
Agrega el nombre de descriptivo
Y finalmente agrega el path del archivo `index.js` del MCP Server que acabamos de construir.

![image](/static/img/posts/edit-mcp-server.png)

Este es el resultado si todo salió bien.

![image](/static/img/posts/mcp-server-cursor-installed.png)


## Ejecución

Para usarlo vas a composer y pide que te haga una búsqueda en la base de datos.

![image](/static/img/posts/mcp-server-execution.png)

## Conclusiones

- Es una herramienta muy poderosa para conectar diversas plataformas para alimentar un modelo largo de lenguaje.
- Es muy fácil de instalar y usar.
- Es una herramienta que se puede usar en modo agente o normal.
- Se puede conectar cualquier sistema creando nuestros propios MCP Server.
- En este proyecto usamos Supabase como base de datos, pero se puede conectar cualquier base de datos PostgreSQL con este ejemplo.
- Aquí estamos trabajando con un proyecto localmente, por eso el query string está con el usuario y contraseña de Supabase local de la base de datos.

## Referencias

- [MCP Server](https://github.com/modelcontextprotocol/servers)
- [Cursor - MCP Server Docs](https://docs.cursor.com/advanced/model-context-protocol)



























