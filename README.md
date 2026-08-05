# Ponto de Virada — Landing Page

## Estrutura
```
index.html              → landing principal (17 seções)
oferta-exclusiva.html   → página de upsell pós-compra (Etapa 3)
assets/css/             → tokens, base, layout, components, sections
assets/js/               → main.js + módulos independentes
```

## Antes de publicar — 3 coisas para trocar

1. **Links de checkout da Kiwify**
   Abra `assets/js/modules/checkoutLinks.js` e troque:
   - `etapa1` → link de checkout do produto "O Ponto Cego" (R$37,90)
   - `pacoteCompleto` → link de checkout do pacote com as 3 etapas

2. **Order bump da Etapa 2**
   Configurado dentro da própria Kiwify: no produto "Etapa 1", vá em
   Editar produto → Configurações → Order Bump, e adicione o produto
   "A Nova Fase" como oferta adicional no checkout.

3. **Links de aceite/recusa da Oferta Exclusiva**
   Abra `oferta-exclusiva.html`, no `<script>` no final do arquivo,
   e troque pelos links gerados em: Editar produto (Etapa 1) →
   Configurações → Upsell de 1 clique. A Kiwify vai pedir a URL
   dessa página (`oferta-exclusiva.html`) para exibir automaticamente
   depois do pagamento aprovado.

## Rodando localmente

Como `main.js` usa ES Modules (`import`/`export`), abrir o `index.html`
direto no navegador (`file://`) não funciona — os módulos exigem que
o site seja servido por um servidor, mesmo que local.

Formas simples de testar antes de publicar:
- VS Code: extensão "Live Server", clique com o botão direito no
  `index.html` → "Open with Live Server"
- Terminal: `npx serve` dentro da pasta do projeto

## Publicando no GitHub Pages

1. Suba a pasta inteira para um repositório
2. Nas configurações do repositório, ative o GitHub Pages apontando
   para a branch principal
3. O site publicado já serve os módulos corretamente via HTTP,
   sem nenhuma configuração extra

## Onde ajustar a identidade visual

Tudo começa em `assets/css/tokens.css` — cor, tipografia e
espaçamento vêm todos desse arquivo. Mudar o tom de dourado, por
exemplo, é uma única linha (`--gold`) que se propaga pro site
inteiro.

## Efeitos desativados por padrão em certas condições

- Cursor customizado: só aparece em desktop com mouse (nunca em
  touch)
- Glow de scroll: desativado abaixo de 720px de largura
- Todas as animações respeitam `prefers-reduced-motion`
