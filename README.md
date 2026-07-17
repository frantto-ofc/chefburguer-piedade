# Chef Burguer Piedade — landing page

Prévia de proposta comercial. Página estática, arquivo único, sem build e sem dependências
além do Google Fonts.

- `index.html` — a página inteira (HTML + CSS + JS inline)
- `assets/` — mídias reais da casa, em WebP com fallback JPEG

## Deploy

Site estático puro. Na Vercel, não precisa de configuração: o `index.html` na raiz é servido
direto. Sem build command, sem output directory, framework "Other".

## Configuração

Telefone, endereço, horário, Instagram e `ORDER_URL` estão centralizados no objeto `CONFIG`,
no `<script>` ao final do `index.html`. É o único lugar a editar para trocar qualquer contato.

## Dados — origem e confirmações

| Dado | Valor | Origem |
|---|---|---|
| Cardápio, preços, promoções | 4 promoções + 16 burguers | `app.cardapioweb.com/chef_burguer1` |
| `ORDER_URL` | `app.cardapioweb.com/chef_burguer1` | bio do Instagram ("Pede aqui!") |
| Endereço | R. do Jangadeiro, 1668 — Candeias | Google Maps + rodapé do cardápio |
| CNPJ | 36.229.073/0001-05 | rodapé do cardápio |
| Horário | Ter–Dom, 18:00–23:59 | confirmado pelo cliente em 17/07/2026 |
| Nota | 4,6 de 5 · 84 avaliações | Google |
| Avaliações | Nathalia Rocha, Lee Charles Vargas | Google |

Nada foi inventado. Onde falta dado real, há placeholder marcado — nunca conteúdo fictício.

## Pendências

### Antes de virar o site oficial

- [ ] **`robots`** — está `noindex,nofollow` de propósito, por ser prévia hospedada fora do
      domínio do cliente. Trocar para `index,follow` só quando for o site oficial.
- [ ] **`canonical`** — comentada no `<head>`, aguarda o domínio definitivo.
- [ ] **`og:image`** — hoje é relativa (`assets/hero-burguer.jpg`). Open Graph pede URL
      absoluta: trocar por `https://DOMINIO/assets/hero-burguer.jpg` ao publicar.

### Conteúdo que falta

- [ ] **Fotos de ambiente, equipe e bastidores** — a galeria e a seção de história seguem
      com placeholder. Existem no feed do @chefburguerpiedade (o post do letreiro neon com o
      salão é ideal para a história), mas as URLs do Instagram são assinadas e expiram:
      precisam ser salvas manualmente em `assets/`.

### Para alinhar com o cliente

- [ ] **Horário no sistema de pedidos** — o site diz 18:00 (confirmado), mas o
      `app.cardapioweb.com` está configurado para abrir às **17:30**. O cliente vê 18:00 aqui
      e consegue pedir 17:30 lá.
- [ ] **CEP na bio do Instagram** — a bio diz `54430-315`; o Google Maps e o rodapé do próprio
      cardápio dizem `54440-160`. A bio está errada.
- [ ] **`?s=insta` no link do cardápio** — a bio usa esse sufixo, que aparenta ser marcação de
      origem. Foi removido aqui para o tráfego do site não ser atribuído ao Instagram.
      Confirmar se o cardapioweb aceita outro valor (ex.: `?s=site`).

## Notas técnicas

- **Contraste**: dourado sobre creme reprova (1,81:1). Por isso o dourado só aparece sobre
  fundo escuro (8,93:1) e as comandas usam texto carvão com acento tijolo (7,43:1).
- **Mídias**: os arquivos do CDN do cardapioweb têm extensão errada — os `.png` e `.webp` de lá
  são todos JPEG por dentro. Foram renomeados conforme o conteúdo real e reconvertidos.
- **Responsivo**: verificado em 360, 375, 768, 1024, 1280 e 1440px — sem rolagem horizontal,
  sem elementos estourando e sem alvos de toque abaixo de 44×44px.
