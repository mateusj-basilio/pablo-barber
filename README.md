# Pablo Lems - Barbearia

Site do barbeiro Pablo Lems, especialista em corte clássico e visagismo, com atendimento em Imbuia (SC) e região. Landing page de página única, otimizada para SEO local, com agendamento via WhatsApp.

**Site no ar:** https://mateusj-basilio.github.io/pablo-barber/

## Seções

Hero, Sobre, Filosofia, Serviços, Qualificações, Formação, Galeria, Depoimentos, Instagram, FAQ, Contato e botão flutuante de WhatsApp (componentes em `src/components/`).

## Stack

- [Astro](https://astro.build) (site estático)
- Tailwind CSS 4 (via `@tailwindcss/vite`)
- Alpine.js (interatividade leve)
- `@astrojs/sitemap` (sitemap automático)

## Como rodar localmente

Pré-requisito: Node.js 22.12 ou superior.

```bash
npm install
npm run dev        # http://localhost:4321/pablo-barber
```

| Comando | Ação |
|---|---|
| `npm run build` | Gera o site estático em `dist/` |
| `npm run preview` | Pré-visualiza o build localmente |

O `astro.config.mjs` define `site` e `base: '/pablo-barber'` para funcionar no GitHub Pages.

## Deploy

Cada push na branch `main` dispara o workflow `.github/workflows/deploy.yml`, que faz o build com `withastro/action` e publica no GitHub Pages.

## Documentação interna

- `SYSTEM_DESIGN.md` e `design-system/` - decisões de design
- `AGENTS.md` / `CLAUDE.md` - instruções para agentes de IA