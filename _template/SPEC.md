# Modelo OpenCapital — HTML de Plano/Briefing/Campanha

> Especificação do modelo padrão para gerar páginas HTML de plano operacional de campanhas, briefings e estratégias.
>
> **Exemplo canônico em uso:** [`campanhas/live-28abr/index.html`](../campanhas/live-28abr/index.html) — copiar este arquivo e adaptar é a forma recomendada de iniciar uma nova campanha.

---

## 1. Estrutura de pastas (por campanha)

```
campanhas/<slug-da-campanha>/
├── index.html              ← Plano/briefing visual (este modelo)
├── briefings/              ← PDFs e .md de briefing original
├── emails/                 ← E1-nome.html, E2-nome.html, ...
├── whatsapp/               ← W1-nome.txt, W2-nome.txt, ...
└── assets/                 ← imagens, base64, scratch
```

**Slug da campanha:** kebab-case, curto, com data se relevante. Ex: `live-28abr`, `lancamento-print-trade`, `webinar-junho`.

**Nomenclatura das peças:** `<canal><N>-<gancho-curto>.<ext>` — onde `canal` é `E` (email) ou `W` (whatsapp). Ex: `E3-recap-ultimo-call.html`, `W2.5-add-agenda.txt`.

---

## 2. Estrutura do `index.html`

Ordem fixa das seções:

1. **HERO** — fundo preto, badge vermelho da campanha, H1 grande, lead, meta (data + nº de peças)
2. **TOC sticky** — navegação ancora pra cada seção
3. **01 · Notas operacionais** — pendências, tarefas, setup técnico, métricas (TUDO o que não é a copy)
4. **02 · Cronograma** — tabela das peças + tabela de vídeos/recursos linkados
5. **DIVIDER preto · "SEÇÃO 1 DE 2 — EMAILS"**
6. **Cards de email** (E1, E2, E3, ...) — cada um com: header (nome + gatilho + data + status), tabela ASSUNTO/PREVIEW/VÍDEO, body-preview compacto, bloco 🔧 Adaptações vs brief, fileref
7. **DIVIDER preto · "SEÇÃO 2 DE 2 — WHATSAPP GRUPOS"**
8. **Cards de WhatsApp** (W1, W2, ...) — mesma estrutura de header + bolha verde imitando WhatsApp + adaptações + fileref
9. **03 · Páginas Framer** (ou outras integrações)
10. **Footer**

> ⚠️ Não criar seção "Notas operacionais finais" / "Resumo de entrega" no fim. Toda informação operacional vai pro topo (seção 01) — evita duplicação.

---

## 3. Design tokens (OpenCapital)

| Token | Valor |
|---|---|
| Tipografia heading | `'DM Sans'` (700-800) |
| Tipografia corpo | `'Manrope'` (400-700) |
| Background body | `#F4F6FA` |
| Background card | `#fff` |
| Background dark hero/divider | `#08080B` ou `#141417` |
| Azul primário (CTA) | `#2479FB` |
| Vermelho urgência | `#DC2626` |
| Verde WhatsApp | `#16A34A` (borda) · `#DCF8C6` (bolha) · `#075E54` (texto bold) |
| Amarelo extra/warning | `#F59E0B` |
| Cinza neutral todo | `#9CA3AF` (borda) · `#6B7280` (texto secondary) |

---

## 4. Componentes/classes CSS reutilizáveis

| Classe | Uso |
|---|---|
| `.section` | Bloco branco com padding 40px, border-radius 8px |
| `.section-num` | Badge preto com número da seção (01, 02...) |
| `.divider` | Separador preto full-width entre seções de canal (EMAILS / WHATSAPP) |
| `.peca` | Card de uma peça (email/whatsapp) — borda esquerda azul |
| `.peca-w` | Variação verde (WhatsApp) |
| `.peca-extra` | Variação amarela (peça extra/não no brief original) |
| `.peca-todo` | Variação cinza (peça ainda a executar) |
| `.peca-header` | Cabeçalho do card com título, gatilho, data, status |
| `.gatilho` | Linha vermelha em uppercase com ▼ + nome do gatilho psicológico |
| `.kv` + `.kv-row` | Tabela compacta ASSUNTO/PREVIEW/VÍDEO |
| `.kv-val.assunto` | Highlight amarelo no campo Assunto |
| `.body-preview` | Caixa cinza clara com a copy resumida (parágrafos quebrados, NUNCA texto corrido) |
| `.body-preview .h` | Frase de destaque dentro da body-preview (DM Sans 700) |
| `.body-preview .marker` | Marcador inline tipo `▸ CTA top` ou `📅 Hero date` (background colorido) |
| `.body-preview .ps` | P.S. com border-top tracejado |
| `.body-preview .callout` | Caixa vermelha de escassez/atenção |
| `.wa-bubble` | Bolha verde imitando WhatsApp (white-space: pre-wrap) |
| `.wa-bubble em` | Negrito do WhatsApp (verde escuro) |
| `.adapt` | Bloco azul claro com 🔧 Adaptações vs brief |
| `.fileref` | Pílula preta no rodapé do card apontando o arquivo físico |
| `.warn` | Callout amarelo pra pendências |
| `.task-list` | Lista de checkboxes ☐ |
| `.pill` + `.pill-done`/`.pill-now`/`.pill-todo`/`.pill-live` | Status pills |
| `.toc` | Navegação sticky no topo |

---

## 5. Padrão da `body-preview` (resumo do email)

A body-preview é a **copy do email resumida** dentro do card do plano — não é o HTML real do email. Regras:

1. **NUNCA escrever em parágrafo único corrido.** Sempre quebrar em `<p>` separados, mantendo a respiração do email original.
2. **Marcadores visuais** pra elementos estruturais do email:
   - `<span class="marker">▸ CTA top</span>` ou `▸ CTA bottom`
   - `<span class="marker marker-video">▶ Vídeo X (thumbnail clicável)</span>`
   - `<span class="marker marker-date">📅 Hero date · DD/MM · HHHmm</span>`
   - `<span class="marker marker-live">▶ ENTRAR NA LIVE AGORA → {{URL}}</span>` (botão grande de live)
3. **Frase-âncora** com `<p class="h">` pra destaque (a "frase martelo" do email).
4. **P.S.** sempre com `<p class="ps"><strong>P.S.</strong> — ...</p>`.
5. **Callouts** (escassez, urgência, alerta) usam `<div class="callout">`.

---

## 6. Padrão `.wa-bubble` (mensagem do WhatsApp)

- `white-space: pre-wrap` preserva quebras de linha do texto
- Negrito do WhatsApp: usar `<em>` (que CSS estiliza com cor verde escuro + bold) — representa o `*texto*` real
- Sempre 2 links: 🎥 YouTube + 🔐 Landing
- Sem `[Nome]` (disparo em grupos por padrão)
- Para áudio: usar bolha de fundo `#F0F9F4` + borda verde mais grossa, com header "🎤 Script para X gravar"

---

## 7. Bloco obrigatório 🔧 Adaptações vs brief

Todo card de peça deve ter:

```html
<div class="adapt">
<div class="adapt-title">🔧 Adaptações vs brief</div>
<ul>
<li>...item 1...</li>
<li>...item 2...</li>
</ul>
</div>
```

**Função:** documentar o que foi mudado/melhorado em relação ao briefing original. Esta é a forma rastreável de mostrar evolução do material.

Tipos comuns de adaptações a registrar:
- Mudança de horário/data por replanejamento
- Valores em R$ informais (anti-spam)
- Adição de 2º CTA / hero date / sub-CTA
- Encurtamento (com %)
- Adaptação pra grupo (sem `[Nome]`)
- Adição de placeholders `{{XXX}}` pra preencher na hora
- Peça nova não prevista no brief
- Substituição de elemento literal do brief

---

## 8. Placeholders `{{XXX}}`

Padrão pra valores que só serão conhecidos na hora do disparo:
- `{{LINK_DA_LIVE}}` — URL da transmissão
- `{{N_CONFIRMADOS}}` — contador de inscritos
- `{{REBRANDLY_LINK}}` — link encurtado
- `{{VIDEO_X_ID}}` — ID YouTube ainda não confirmado

**Sempre listar na seção 01 (Substituições de última hora)** quantas ocorrências e em quais arquivos.

---

## 9. Cards de status (pills)

| Pill | Quando usar |
|---|---|
| `.pill-done` (verde) | Peça enviada |
| `.pill-now` (amarelo) | Peça do dia atual ou em ação imediata |
| `.pill-todo` (azul claro) | Peça futura ainda a fazer |
| `.pill-live` (vermelho) | Live em si / momento ao vivo |

A cor da borda esquerda do `.peca` deve refletir o estado:
- `.peca` (azul) = email enviado/normal
- `.peca-w` (verde) = WhatsApp enviado/normal
- `.peca-extra` (amarelo) = peça extra/não no brief
- `.peca-todo` (cinza) = ainda a fazer

Combinar: `<div class="peca peca-w peca-todo">` = WhatsApp ainda a fazer.

---

## 10. Como criar uma nova campanha

```bash
# 1. Cria pasta
mkdir -p campanhas/<slug>/{emails,whatsapp,briefings,assets}

# 2. Copia o exemplo canônico como ponto de partida
cp campanhas/live-28abr/index.html campanhas/<slug>/index.html

# 3. Adapta hero, cronograma, peças

# 4. Adiciona o card no índice mestre raiz (index.html da raiz do repo)
```

---

## 11. Princípios

- **Leveza primeiro** — o plano tem que ser escaneável. Uma pessoa abre, entende a campanha em 2 minutos.
- **Nada de redundância** — se uma informação aparece na seção 01, não repete no fim. Se aparece no cronograma da 02, não repete em "resumo de entrega".
- **Pendências sempre no topo** — o leitor precisa saber o que está bloqueando antes de ler a copy.
- **Adaptações documentadas** — toda divergência do brief original tem que estar em `.adapt`. Se mudou e não documentou, vai gerar confusão depois.
- **Placeholders explícitos** — nunca enviar com `{{XXX}}` sem lista prévia do que precisa substituir.
- **Mobile-friendly** — media query em 680px ajusta hero/divider/cards.
