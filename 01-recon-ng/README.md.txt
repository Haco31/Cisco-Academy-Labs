# Laboratorio: Recon-ng (Cisco Academy)

## 🎯 Objetivo
El propósito de este laboratorio es aprender a utilizar el framework **Recon-ng** para realizar reconocimiento pasivo (OSINT) sobre un dominio específico, sin interactuar directamente con el objetivo.

## 🚀 Pasos Realizados

1. **Configuración del Workspace:**
   - Creación de un entorno de trabajo aislado para el proyecto.
2. **Instalación de Módulos:**
   - Uso del Marketplace para instalar módulos de `discovery` y `reporting`.
3. **Recolección de Datos:**
   - Agregado de dominios y búsqueda de subdominios, hosts y contactos.
4. **Generación de Reporte:**
   - Exportación de los resultados en formato HTML/CSV.

## 💻 Comandos Clave Utilizados
```bash
# Iniciar recon-ng
recon-ng

# Crear workspace
workspaces create bodoque

# Buscar e instalar un módulo
marketplace search hackertarget
marketplace install hackertarget

marketplace search bing
marketplace install bing_domain_web

marketplace search discovery
marketplace install interesting_file

# Ejecutar módulo
modules load recon/domains-hosts/hackertarget
run

marketplace load recon/domains-hosts/bing_domain_web
run

marketplace load discovery/info_disclosure/interesting_file
run