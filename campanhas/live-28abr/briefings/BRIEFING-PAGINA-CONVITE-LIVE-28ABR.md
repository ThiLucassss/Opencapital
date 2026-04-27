# BRIEFING — Criar página `/convite-live-28abr` no Framer

> **Use este briefing num novo chat dedicado ao projeto Framer.**
> A campanha de email já está em andamento (chat separado). Esta página é o destino do **canal WhatsApp** da campanha.

---

## 1. Contexto

Estamos rodando a **Campanha Live 28/04 · Print & Trade** da OpenCapital. A live acontece **terça-feira 28 de abril de 2026 às 20h00 (BRT)**. O objetivo é captar confirmações de presença.

A campanha tem dois canais:
- **Email** (ActiveCampaign) — já tem HTML pronto, inclui videos + CTA embutido
- **WhatsApp** (disparo em **grupos**, broadcast) — precisa de **UMA URL única** pra apontar, que seja uma "versão web" do conteúdo do email, porque colar 3 links crus no WhatsApp fica feio e reduz conversão

**Esta nova página `/convite-live-28abr` é essa versão web.** Atua como o "corpo do email" renderizado em landing page — o usuário clica em 1 link no WhatsApp, cai nessa página, assiste os vídeos inline (sem sair pro YouTube), e clica no CTA pra confirmar presença.

---

## 2. Arquitetura do funil

```
┌─────────────────────────────┐
│ WHATSAPP: teaser + 1 link   │
│ → lp.theopencapital.org/    │
│   convite-live-28abr        │
└─────────────┬───────────────┘
              ↓
┌─────────────────────────────────────┐
│ /convite-live-28abr  ← CRIAR ESTA   │
│ hero + videos + countdown + CTA     │
└─────────────┬───────────────────────┘
              ↓ (clique no CTA)
┌─────────────────────────────────────┐
│ /live-28abr-confirmado  ← JÁ EXISTE │
│ (página de thank you com calendário)│
│ Site Tracking dispara automation AC │
└─────────────────────────────────────┘
```

---

## 3. Referências

### Página referência visual
**`/replay-live`** (no projeto Framer) — é considerada a landing mais bem construída do projeto. Use-a como referência de:
- Hierarquia visual
- Espaçamento e ritmo de leitura
- Qualidade de tipografia
- Padrão de CTAs
- Design system em ação
- Tratamento de videos embed

Abrir no Framer, estudar a estrutura XML dos componentes, e replicar o mesmo nível de polimento.

### Conteúdo/copy base
O conteúdo da página deve **espelhar o HTML do email E1** (que já foi escrito e aprovado). Arquivo de origem:

**`c:/Users/Thiago/Documents/opencapital/campanhas/live-28abr/emails/E1-anuncio-ataque.html`**

Copie os mesmos blocos de copy (com ajustes pontuais pra formato web — parágrafos podem ser mais curtos). **Não reescreva a copy**; use o que está aprovado.

---

## 4. Projeto Framer

**Nome do projeto:** "O novo jeito de fazer dinheiro"

**Como conectar:** abrir o projeto → `Cmd+K` → buscar "MCP" → abrir plugin MCP

---

## 5. O que já existe no projeto (REUSAR)

Componentes já criados pra essa campanha — **devem ser reaproveitados** nesta página:

| Componente | Code file ID | Insert URL | Para quê |
|---|---|---|---|
| `Live28_Hero` | `qnQi7Tq` | `https://framer.com/m/Live28-Hero-QM3suw.js` | Hero com badge "Você está dentro" — **NÃO usar aqui** (é da página de confirmação) |
| `Live28_Countdown` | `NrM1cQr` | `https://framer.com/m/Live28-Countdown-V2IiIf.js` | Contador regressivo até 28/04 20h BRT — **USAR** |
| `Live28_EventCard` | `BRbQBMN` | `https://framer.com/m/Live28-EventCard-jkAmBX.js` | Card com data/hora/duração/link via WApp — **USAR** |
| `Live28_CalButtons` | `prBkhGP` | `https://framer.com/m/Live28-CalButtons-vxICfp.js` | Botões Google/Apple Calendar — **NÃO usar aqui** (só após confirmar) |
| `Live28_ReminderFooter` | `Udrgu7H` | `https://framer.com/m/Live28-ReminderFooter-Q5qxY3.js` | Reminder + disclaimer legal — **USAR** |

**Página de confirmação já existente:** `/live-28abr-confirmado` (nodeId `pSzwvdFI2`) — o CTA desta nova página deve apontar pra ela.

---

## 6. O que criar de novo

### 6.1 Página
**Slug:** `/convite-live-28abr`
**Tipo:** web (publicável)
**URL final:** `https://lp.theopencapital.org/convite-live-28abr`

### 6.2 Novos code components

#### A) `ConviteLive28_Hero.tsx`
**Função:** hero de entrada que converte o headline do E1.
**Copy:**
- Badge superior vermelho: `● AO VIVO · TER 28/04 · 20H`
- H1: `Você ainda tá estudando análise técnica em 2026?`
- Subtítulo: `22 mil views em 8 dias mostram o que a IA tá fazendo. Assista antes da live — ela começa terça às 20h.`
- Fonts: DM Sans (heading) + Manrope (sub)
- Cores: bg `#08080B` ou `#0B0B10`, H1 branco, accent `#DC2626` (badge) e `#2479FB` (secundário)

#### B) `ConviteLive28_Videos.tsx`
**Função:** 2 vídeos do YouTube embutidos (iframe) que tocam INLINE na página.

Vídeos:
1. **R$ 1.700 de lucro com IA — day trade real**
   - ID: `yeUXsAWhHSw`
   - URL embed: `https://www.youtube.com/embed/yeUXsAWhHSw`
   - Views: 5,2 mil · 4 dias
2. **Day trade com IA — passo a passo**
   - ID: `2HV4noYpbaE`
   - URL embed: `https://www.youtube.com/embed/2HV4noYpbaE`
   - Views: 9,2 mil · 5 dias

**Requisitos:**
- Iframe responsivo 16:9 (padding-top: 56.25% trick)
- Título + metadata (views/dias) abaixo de cada vídeo
- Stack vertical em mobile, side-by-side ou stack vertical em desktop (recomendado: stack vertical sempre, cada video em card de até 720px de largura)
- Borda ou card com `border-left: 4px solid #DC2626` (mesmo estilo dos cards de vídeo no email)
- Legenda entre os dois: `22 mil visualizações em 8 dias · sem edição, sem corte`

#### C) `ConviteLive28_Copy.tsx`
**Função:** bloco de copy que vai entre os vídeos e a pré-CTA. Espelha a copy do E1:
- "Estudar análise técnica em 2026 é a mesma coisa que aprender a fazer cálculo no ábaco."
- "Funciona? Tecnicamente, sim."
- "Tem ferramenta melhor disponível? Tem."
- "A diferença entre quem usa e quem não usa? Astronômica."
- Fonte grande no destaque (H2/H3), prose em Manrope 16-18px

#### D) `ConviteLive28_CTA.tsx`
**Função:** seção final com o botão de confirmação.

Conteúdo:
- Pretítulo pequeno: `Terça, 28/04 · 20h00 · ao vivo · sem replay`
- Headline: `Terça que vem, 20h em ponto, vou entrar ao vivo.`
- Parágrafo curto: `Vou rodar a IA em tempo real, em 4 ativos diferentes. 90 minutos. Q&A no chat. E no fim uma oferta exclusiva que só vale durante a transmissão.`
- Botão CTA grande azul `#2479FB`:
  - Texto: `→ QUERO VER A IA OPERANDO AO VIVO`
  - **Link:** `https://lp.theopencapital.org/live-28abr-confirmado?utm_source=landing-convite&utm_medium=cta&utm_campaign=live28abr`
  - ⚠️ **Este é o único UTM da jornada WhatsApp** — os links incoming (WhatsApp → landing) são limpos, sem UTM. O UTM entra aqui, no botão interno da landing que leva pra confirmação, para medirmos efetivamente quem clicou através dessa rota.
- Microcopy abaixo: `1 clique. Sem inscrição. Sem formulário. Te mando o link no WhatsApp 1 hora antes.`

---

## 7. Estrutura da página (ordem dos blocos)

```
1. ConviteLive28_Hero            ← novo
2. Live28_Countdown              ← reuso
3. ConviteLive28_Videos          ← novo (2 iframes YouTube)
4. ConviteLive28_Copy            ← novo (punchline "análise técnica = ábaco")
5. Live28_EventCard              ← reuso (card com data/hora/duração)
6. ConviteLive28_CTA             ← novo (botão final)
7. Live28_ReminderFooter         ← reuso (reminder + disclaimer legal)
```

---

## 8. Design system (coerência com a identidade existente)

**Fonts:**
- DM Sans (headings, botões, números grandes) — pesos 400/500/600/700/800
- Manrope (corpo, parágrafos) — pesos 300/400/500/600/700
- Import: `@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700;800&family=Manrope:wght@300;400;500;600;700&display=swap');`

**Cores:**
- Background principal: `#08080B` (dark) — manter consistência com página `/live-28abr-confirmado`
- Card secundário: `#111115`
- Texto branco: `#FFFFFF`
- Texto cinza médio: `#9CA3AF`
- Texto cinza escuro: `#6B7280`
- Accent azul (primário): `#2479FB`
- Accent azul hover: `#1B6AE0`
- Alerta/urgência vermelho: `#DC2626`
- Vermelho claro: `#F87171`

**Espaçamento:**
- Seguir o padrão dos componentes `Live28_*` já criados (padding lateral `24px`, gap vertical entre blocos `0px` porque cada componente já tem padding próprio)

---

## 9. Responsividade

- **Desktop primary** — mesma largura que `/confirmacao-whats` (breakpoint 1521px referencial)
- **Phone + PhoneSmall** — replicar variantes como na página `/confirmacao-whats` ou `/replay-live`
- YouTube iframes devem ser 100% responsivos (max-width 720px em desktop, 100% em mobile, aspect-ratio 16:9)

---

## 10. Publicação

- Publicar em `lp.theopencapital.org/convite-live-28abr`
- Confirmar que o subdomínio já aponta pro Framer (CNAME configurado)
- **Site Tracking do ActiveCampaign** deve estar instalado no Framer — é obrigatório pro trigger de automation "Visits a web page" funcionar na página de confirmação

---

## 11. Checklist antes de considerar pronto

- [ ] Página publicada e acessível em `lp.theopencapital.org/convite-live-28abr`
- [ ] Variantes Desktop + Phone + PhoneSmall funcionando
- [ ] 2 vídeos tocam inline (sem sair da página)
- [ ] Countdown mostra contagem correta pra 28/04 20h BRT
- [ ] Botão CTA clicável e redireciona pra `/live-28abr-confirmado` com UTMs preservadas
- [ ] Fontes carregam (DM Sans + Manrope)
- [ ] Nenhuma imagem crítica sem fallback
- [ ] SEO meta tags básicas (title, description)
- [ ] Site Tracking AC ativo
- [ ] Testado no celular real (WhatsApp → clicar no link → navegar → confirmar)

---

## 12. Prazo

Pra ontem. Ideal: **ter a página pronta antes de sexta 24/04 às 21h** (quando vai começar o disparo do WhatsApp W1, que aponta pra ela).

---

## Arquivos de contexto relevantes no workspace

- `campanhas/live-28abr/emails/E1-anuncio-ataque.html` — HTML do email E1 (base da copy)
- `campanhas/live-28abr/briefings/` — este arquivo e outros briefings da campanha
- `campanhas/live-28abr/whatsapp/` — mensagens de WhatsApp que apontam pra essa página
