# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

@AGENTS.md

## Proyecto

Arcade Vault es una plataforma para jugar online y competir por la mayor cantidad de puntos. Actualmente el repo es el scaffold de `create-next-app` (solo `app/layout.tsx` y `app/page.tsx` de plantilla); la funcionalidad aún no está implementada.

El desarrollo sigue **Spec Driven Design** con las skills `/spec` y `/spec-impl` de [Klerith/fernando-skills](https://github.com/Klerith/fernando-skills) (se instalan con `npx skills@latest add Klerith/fernando-skills`). Las nuevas funcionalidades deben especificarse primero con `/spec` e implementarse después con `/spec-impl`.

## Comandos

```bash
npm run dev     # servidor de desarrollo en http://localhost:3000
npm run build   # build de producción (también hace type-check)
npm run start   # sirve el build de producción
npm run lint    # ESLint (flat config en eslint.config.mjs)
npx tsc --noEmit  # solo type-check
```

No hay framework de tests configurado todavía.

## Stack y convenciones

- **Next.js 16.3 (App Router) + React 19.2 + TypeScript strict.** Las APIs difieren de versiones anteriores: consulta `node_modules/next/dist/docs/` (`01-app/`, `03-architecture/`, etc.) antes de escribir código de Next. Ejemplo: los layouts usan el helper global `LayoutProps<"/">` generado por Next para tipar props (ver `app/layout.tsx`).
- **Tailwind CSS v4** vía `@tailwindcss/postcss`. No existe `tailwind.config.*`: el tema se define en `app/globals.css` con `@import "tailwindcss"` y `@theme inline`, mapeando variables CSS (`--background`, `--foreground`, fuentes Geist) a tokens de Tailwind. El modo oscuro usa `prefers-color-scheme`.
- Alias de imports: `@/*` apunta a la raíz del repo (no hay carpeta `src/`).
