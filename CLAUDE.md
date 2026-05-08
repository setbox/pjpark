# CLAUDE.md

Guidance for Claude Code when working in this repository.

## Development

No build step. Open any `.html` directly or serve with `npx serve .` / `python3 -m http.server 8080`. Tailwind CSS and Inter load via CDN.

## Architecture

Multi-page static site for **PJ Park** (pjpark.com.br) - escritório online para empresas inativas, uma divisão da Setbox Sistemas Digitais. Pages: `index` (home), `baixa-de-empresa/`, `servicos/`, `blog/`. All assets in `assets/`. See `DESIGN.md` for component patterns.

## Nav

Logo: `apple-touch-icon.png` (`h-8 w-auto rounded-lg`), links to home.

Order: `[logo]` | Baixa de empresa | Serviços adicionais | Blog | `[Começar →]` (CTA).

Active link: `font-medium style="color:#ff3f6e;"`. Inactive: `text-sm text-[#111111] hover:opacity-50 transition-opacity hidden md:block`.

CTA "Começar →" links to `https://app.pjpark.com.br`, style: `background:#ff3f6e` hover `#193044`.

No sub-nav. Standalone site — no Setbox navbar.

## Footer

Logo Setbox (`setbox-lateral.png`, `h-6 w-auto`, links to `https://setbox.com.br`) + © 2026 Setbox Serviços Digitais + endereço. Sem colunas adicionais. Todos os links Setbox são absolutos.

```html
<footer class="border-t border-[#E5E5E5]">
  <div class="max-w-5xl mx-auto px-4 md:px-8 py-10 md:py-14">
    <a href="https://setbox.com.br" target="_blank"><img src="[path]/setbox-lateral.png" alt="Setbox" class="h-6 w-auto mb-5" width="1405" height="466"></a>
    <p class="text-[12px] text-[#BBBBBB] mb-1">© 2026 Setbox Serviços Digitais</p>
    <p class="text-[12px] text-[#BBBBBB]">Rua João Bettega, 649 - Sala 3A<br>Curitiba / PR</p>
  </div>
</footer>
```

## Asset Paths (by depth)

| Arquivo | `assets/` prefix |
|---|---|
| `index.html` | `assets/` |
| `baixa-de-empresa/`, `servicos/`, `blog/` | `../assets/` |
| `blog/devo-inativar-minha-empresa/` | `../../assets/` |

## Content Rules

- Language: Brazilian Portuguese
- No trailing period on any title or subtitle (h1-h6)
- Never use em dash anywhere - use hyphen (-) or comma
- All app CTAs: `https://app.pjpark.com.br`
- Contact email: `contato@setbox.com.br`
- Domain: `pjpark.com.br`

## Image Rules

- All `<img>` must have `width`, `height`, and `loading="lazy"` — except nav/footer logos (above fold)

## Color Palette (PJ Park)

| Token | Valor | Uso |
|---|---|---|
| `accent` | `#ff3f6e` | CTAs, labels, link ativo, nav logo |
| `accent-hover` | `#193044` | Hover de botões (inverte para navy) |
| `dark` | `#193044` | Fundo de seções hero escuras |
| `dark-secondary` | `#2b4153` | Botões secundários sobre fundo dark |
| `bg-muted` | `#f0f4f8` | Fundo de seções alternadas |
| `icon-bg` | `#fff0f4` | Fundo de ícone em card |
| `text-on-dark` | `#c7cbcf` | Texto secundário sobre fundo navy |

Labels de seção: `text-[11px] font-semibold tracking-wide uppercase" style="color:#ff3f6e;"`

Bullets: `<span class="font-bold flex-shrink-0" style="color:#ff3f6e;">→</span>`

## SEO

Every page needs: `meta[description]`, `link[canonical]`, Open Graph tags (`og:type/site_name/locale/url/title/description/image`), Twitter card. OG image: `assets/og-image.png` (1200x630). `og:site_name` = "PJ Park". Tailwind CDN: add `<link rel="preload" as="script">` before the `<script>` tag.
