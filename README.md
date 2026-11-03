# PinoleroPrints

Sitio web oficial de **PinoleroPrints**: diseño, personalización y producción textil en Nicaragua.

[![Astro](https://img.shields.io/badge/Astro-6-BC52EE?logo=astro&logoColor=white)](https://astro.build)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![Node.js](https://img.shields.io/badge/Node.js-%E2%89%A522.12-339933?logo=node.js&logoColor=white)](https://nodejs.org)
[![Licencia](https://img.shields.io/badge/Licencia-Proprietaria-red)](LICENSE)

> [!IMPORTANT]
> Software **propietario**, desarrollado en colaboración entre **PinoleroPrints** y **RK8**. Todos los derechos reservados. No se permite su copia, clonación, redistribución ni uso comercial sin autorización escrita de ambos titulares. Consulta [LICENSE](LICENSE) antes de interactuar con este repositorio.

---

## Tabla de contenido

- [Descripción](#descripción)
- [Stack tecnológico](#stack-tecnológico)
- [Requisitos](#requisitos)
- [Instalación](#instalación)
- [Scripts disponibles](#scripts-disponibles)
- [Estructura del proyecto](#estructura-del-proyecto)
- [Convenciones](#convenciones)
- [Despliegue](#despliegue)
- [Licencia](#licencia)
- [Autor](#autor)

## Descripción

PinoleroPrints es un sitio de una sola página (landing) orientado a la conversión, que presenta los servicios de sublimación, impresión DTF, bordado, grabado láser y diseño gráfico, junto con un catálogo de productos y canales de contacto directo.

El sitio prioriza:

- **Rendimiento**: generación estática (SSG) con Astro e imágenes optimizadas en WebP.
- **SEO**: metadatos canónicos, Open Graph, Twitter Cards, datos estructurados `LocalBusiness` y sitemap.
- **Accesibilidad**: contraste de color ajustado y navegación responsive.
- **Mantenibilidad**: contenido tipado y separado de la capa de presentación.

## Stack tecnológico

| Tecnología | Versión | Rol |
|---|---|---|
| [Astro](https://astro.build) | 6 | Framework y generación estática |
| [Tailwind CSS](https://tailwindcss.com) | 4 | Estilos utilitarios |
| [Sharp](https://sharp.pixelplumbing.com) | 0.35 | Optimización de imágenes |
| [pnpm](https://pnpm.io) | 11.10 | Gestor de paquetes |
| Node.js | ≥ 22.12.0 | Entorno de ejecución |

La integración `@astrojs/sitemap` genera el sitemap en el build.

## Requisitos

- Node.js `>= 22.12.0`
- pnpm `11.x` (se recomienda instalarlo con [Corepack](https://nodejs.org/api/corepack.html): `corepack enable`)

## Instalación

```bash
git clone git@github.com:RK8-HQ/PinoleroPrints.git
cd PinoleroPrints
pnpm install
```

> La clonación solo está autorizada al personal con permiso expreso del titular (ver [Licencia](#licencia)).

## Scripts disponibles

| Comando | Descripción |
|---|---|
| `pnpm dev` | Servidor de desarrollo en `http://localhost:4321` |
| `pnpm build` | Build de producción en `./dist/` y copia del sitemap a `sitemap.xml` |
| `pnpm preview` | Vista previa local del build |
| `pnpm astro` | CLI de Astro (`astro check`, `astro add`, etc.) |

Antes de abrir un PR o desplegar, el build debe completar sin errores:

```bash
pnpm build
```

## Estructura del proyecto

```text
.
├── .github/workflows/deploy.yml   # CI/CD a GitHub Pages
├── public/                        # Recursos estáticos (favicon, CNAME, og-image, robots.txt)
├── src/
│   ├── assets/                    # Imágenes WebP/SVG y barrel de exportaciones
│   │   └── icons/                 # Iconos de redes sociales
│   ├── components/                # Componentes Astro reutilizables
│   │   ├── Header.astro
│   │   ├── HeroSection.astro
│   │   ├── ServicesSection.astro
│   │   ├── CatalogSection.astro
│   │   ├── AboutSection.astro
│   │   └── Footer.astro
│   ├── constants/                 # Contenido y configuración tipados
│   │   ├── urls.ts
│   │   ├── services.ts
│   │   ├── products.ts
│   │   └── navigation.ts
│   ├── layouts/Layout.astro       # Layout base: SEO, Open Graph, analytics
│   ├── pages/index.astro          # Página principal
│   └── styles/global.css          # Tailwind y estilos globales
├── astro.config.mjs
├── package.json
├── pnpm-lock.yaml
├── pnpm-workspace.yaml
└── tsconfig.json
```

## Convenciones

- **Path alias**: `@/` apunta a `src/`. Ejemplo: `import { URLS } from "@/constants"`.
- **Barrel files**: cada carpeta expone sus módulos mediante `index.ts`.
- **Nomenclatura**: componentes en `PascalCase`; constantes y tipos en `camelCase` / `PascalCase`.
- **Separación de responsabilidades**: los datos viven en `src/constants/` tipados de forma explícita; los componentes solo los consumen.
- **Imágenes**: se importan desde `src/assets/` y se pasan como props desde la página.

## Despliegue

El despliegue es automático: cada push a `main` dispara el workflow [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml), que instala dependencias con `--frozen-lockfile`, ejecuta el build y publica `dist/` en **GitHub Pages**.

- Dominio: [pinoleroprints.rk8.dev](https://pinoleroprints.rk8.dev)
- El dominio personalizado se configura en `public/CNAME`.
- Analytics: Cloudflare Web Analytics.

## Licencia

Este software es una obra desarrollada en colaboración entre **PinoleroPrints** y **RK8**, y se distribuye bajo una **licencia propietaria restrictiva**. Copyright © 2026 PinoleroPrints y RK8 (-RK8HQ). **Todos los derechos reservados.**

Los derechos de propiedad intelectual son **cotitulares**: ninguna de las partes puede otorgar licencias, ceder o autorizar el uso del software a terceros sin el consentimiento previo y por escrito de la otra. No se concede permiso para copiar, clonar, bifurcar (fork), redistribuir, modificar, sublicenciar ni utilizar este software, su código fuente o sus recursos con fines comerciales o de cualquier otra índole. El acceso al repositorio no otorga ningún derecho de uso.

Las marcas y elementos de identidad de cada parte pertenecen a su respectivo titular. En caso de conflicto con un contrato escrito entre ambas partes, prevalece el contrato.

El texto legal completo está en [LICENSE](LICENSE).

## Autor

**PinoleroPrints y RK8 (-RK8HQ)**

- GitHub: [@RK8-HQ](https://github.com/RK8-HQ)
- Sitio: [rk8.dev](https://rk8.dev)

Para consultas comerciales o de licenciamiento, contactar a ambas partes a través de los canales publicados en el sitio.
