# System Design & AI Guidelines: Pablo Lems Barber

Este documento serve como a "Bíblia" do projeto. Qualquer Inteligência Artificial (ou desenvolvedor) que trabalhar neste repositório **DEVE** seguir rigorosamente estas diretrizes para manter a integridade, performance e tom de marca do site.

## 1. Identidade e Tom de Marca (Copywriting)
- **O Foco é Pessoal:** O site é sobre o **Pablo Lems**, um barbeiro de elite e visagista, e não sobre a "DJ Barbearia" (que é apenas o local físico onde ele atende).
- **Voz Ativa e Singular:** NUNCA use pronomes no plural como "Nós", "Nosso", "Garantimos". SEMPRE use a primeira pessoa do singular: "Eu", "Meu", "Garanto", "Minhas técnicas". 
- **Autoridade (Elite):** O tom deve ser de alta sofisticação, precisão cirúrgica e exclusividade. Palavras-chave permitidas e encorajadas: *Visagismo, Geometria Craniana, Consultoria de Imagem, Alto Padrão, Estética Masculina*.

## 2. Tech Stack e Performance
- **Framework Core:** Astro.js (SSG - Static Site Generation).
- **Estilização:** TailwindCSS v4 + Variáveis de CSS Nativas (`src/styles/global.css`).
- **Scripts Nativos:** Usamos **Alpine.js** via CDN/Integração para modais rápidos e lógicas de UI simples (ex: `x-data`).
- **Animações (REGRAS RÍGIDAS):** 
  - **NÃO UTILIZAR GSAP** ou bibliotecas pesadas de JS para animação.
  - Todas as animações de "Reveal" (aparecer ao rolar a tela) usam a API nativa do navegador `IntersectionObserver`. O script de controle está cravado no `<head>` do `Layout.astro`.
  - Para animar novos elementos, basta adicionar a classe `gsap-reveal` (mantivemos o nome da classe por legado estrutural).
- **Imagens:** TODAS as imagens devem ser renderizadas usando o componente `<Image />` do `astro:assets` (para conversão automática em `.webp` e lazy-loading). Nunca use `<img>` cru.
- **Fontes:** As fontes devem ser carregadas estritamente no `<head>` com `<link rel="preconnect">` para evitar *Render Blocking* e problemas de FOUT. O CSS base NUNCA deve usar `@import` para fontes.

## 3. SEO e AEO (Search & Answer Engine Optimization)
- O site é uma máquina de captação orgânica focada no **Alto Vale - SC** (Imbuia, Ituporanga, Rio do Sul, etc.).
- **GEO Tags:** Injetadas no `<head>` (`Layout.astro`).
- **Schema.org:** O `Layout.astro` possui um JSON-LD extremamente rico classificando Pablo Lems como `Person` e `HealthAndBeautyBusiness`. 
- **FAQ:** A seção de Perguntas Frequentes (`FAQ.astro`) possui Schema nativo de `FAQPage` para garantir rich snippets e respostas diretas para as IAs (ChatGPT, Perplexity).

## 4. Estrutura do Projeto
- `src/layouts/Layout.astro`: Contém todo o SEO global, carregamento de fontes e o observer de animação.
- `src/pages/index.astro`: O maestro. Apenas importa e empilha os componentes da página (Hero, About, Philosophy, etc.). Nenhum HTML solto deve existir aqui.
- `src/components/*.astro`: Cada seção lógica do site (Contato, Galeria, Treinamentos) tem seu próprio arquivo modular, para facilitar a edição.

## 5. Regra de Ouro para IAs
Antes de adicionar qualquer nova funcionalidade, verifique se isso pode ser resolvido com as ferramentas nativas (Astro/Tailwind/Alpine) antes de sugerir a instalação de novos pacotes `npm`. O objetivo principal desta arquitetura é a **velocidade absurda de carregamento (Lighthouse 100)** e **manutenção zero de servidor**.
