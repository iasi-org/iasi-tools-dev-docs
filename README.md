[🇪🇸 **Castellano**](README.md) | [🇬🇧 English](README.en.md)

# iasi-quarto-docs

> Documentación oficial de `iasi.quarto`.

`iasi-quarto-docs` contiene la documentación completa de **iasi.quarto**, el framework de ingeniería documental basado en Quarto que forma parte del ecosistema **IASI (Ingeniería Aumentada por Sistemas Inteligentes)**.

Este repositorio no contiene el código del framework.

Contiene el conocimiento necesario para utilizarlo, comprenderlo y seguir su evolución.

---

# ¿Por qué existe?

La documentación de `iasi.quarto` tiene necesidades distintas del propio paquete.

Debe poder:

- evolucionar de forma independiente;
- generar varios libros;
- compartir recursos comunes;
- publicarse en HTML y PDF;
- documentar tanto el uso como la arquitectura y el proceso de diseño.

Por ello, la documentación se mantiene en un repositorio independiente.

---

# Los libros

`iasi-quarto-docs` genera tres libros complementarios.

## Manual de usuario

Orientado a quienes desean utilizar `iasi.quarto`.

Incluye:

- instalación;
- estructura de proyectos;
- configuración;
- API pública;
- renderizado;
- ejemplos;
- resolución de problemas.

## Guía del desarrollador

Orientada a quienes desean comprender, mantener o ampliar `iasi.quarto`.

Incluye:

- arquitectura;
- organización del paquete;
- motores internos;
- convenciones;
- pruebas;
- contribución.

## El viaje

Documenta la evolución del proyecto.

Recoge:

- decisiones de ingeniería;
- experimentos;
- alternativas descartadas;
- errores;
- cambios de dirección;
- necesidades que dieron lugar a nuevas funcionalidades.

Porque comprender cómo se construyó una solución es también parte del conocimiento.

---

# Estructura

```text
iasi-quarto-docs/
├── user-guide/
├── developer-guide/
├── journey/
└── shared/