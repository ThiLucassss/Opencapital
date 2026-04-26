# CRONOGRAMA — Campanha Live 28/04 (Print & Trade)

> **Base oficial:** `OpenCapital - Live 28 de Abril - Emails.pdf` (mesmo diretório)
> **Live:** segunda 28/04/2026 às 20h00 BRT
> **Lista destino:** principal OpenCapital (~5.004 contatos ativos · brief diz 4.900)
> **CTA padrão (email):** `https://lp.theopencapital.org/live-28abr-confirmado`
> **CTA padrão (whatsapp):** `https://lp.theopencapital.org/convite-live-28abr`

## Padrão de adaptação brief → arquivo final

Não copiamos o brief literal. Aplicamos esse pattern (validado no E1/W1):
- **Mantém:** assunto, preview, ângulo/gatilho, copy do corpo, P.S.
- **Adapta:** valores em R$ → escrita informal anti-spam ("dez mil", "3 mil novecentos") · `[Nome]` → `%FIRSTNAME%` · `[LINK BOTÃO]` → URL real com UTM
- **Adiciona (visual HTML):** header tag vermelho · CTA early above-the-fold (botão extra no topo) · hero date block preto com 28/04 · 20H00 · sub-CTA "link no WhatsApp 19h" · assinatura caligráfica do Suriel · footer legal (CNPJ Ports Capital) · unsubscribe
- **2 botões CTA por email** (top + bottom, mesma URL, UTM diferente: `email{N}-cta-top` e `email{N}-cta`)

## Distribuição completa (5 emails + 5 WhatsApps)

| # | Disparo brief | Disparo real | Peça | Gatilho | Vídeo(s) | Status |
|---|---|---|---|---|---|---|
| **E1** | Ter 22/04 19h | Sex 24/04 17h | `E1-anuncio-ataque.html` | Ataque ao "estudou anos" | LINK 1 (`yeUXsAWhHSw` R$ 1.700) + LINK 2 (`2HV4noYpbaE` passo a passo) | ✅ Enviado |
| **W1** | Ter 22/04 19h30 | Sex 24/04 ~17h30 | `W1-aviso-curto.txt` | Mesmo, encurtado | LINK 1 | ✅ Enviado |
| **E2** | Sex 25/04 11h | Sáb 25/04 ~17h | `E2-promessa-falsa.html` | **Promessa falsa = morta** (ataque indústria de gurus) | LINK 3 (`gG2bUUwDFpE` R$ 2.255) | ⏳ Aguardando aprovação |
| **W2** | Sex 25/04 14h | Sáb 25/04 ~17h30 | `W2-provocacao.txt` | **Provocação + guru Lamborghini** | LINK 3 | ⏳ Aguardando aprovação |
| **E3** | Dom 27/04 19h | Dom 27/04 19h | `E3-recap-ultimo-call.html` | Última chance + dor específica (mão treme / segura na perda) | LINK 4 (`_wwMqYp2ze0` "A melhor IA") | ⬜ A fazer |
| **W3** | Dom 27/04 20h | Dom 27/04 20h | `W3-audio-suriel.txt` | **Áudio do Suriel · 50s** (não texto) — script no brief pág 16 | — | ⬜ A fazer (Suriel grava) |
| **E4** | Seg 28/04 9h | Seg 28/04 9h | `E4-e-hoje.html` | Compromisso + expectativa | — | ⬜ A fazer |
| **W4** | Seg 28/04 12h | Seg 28/04 12h | `W4-lembrete.txt` | Lembrete dia D | — | ⬜ A fazer |
| **E5** | Seg 28/04 19h | Seg 28/04 19h | `E5-1h-antes.html` | Ação imediata (link da live) | — | ⬜ A fazer |
| **W5** | Seg 28/04 19h55 | Seg 28/04 19h55 | `W5-5min.txt` | Chamada final · 5 min | — | ⬜ A fazer |

## Pendências travando peças posteriores

1. ✅ **LINK 4** confirmado: `_wwMqYp2ze0` ("A MELHOR IA PARA GANHAR COM DAY TRADE — Inteligência Artificial")
2. **Oferta exclusiva da live** — brief pág 19 lista 4 opções (A: desconto direto · B: bônus · C: vitalício · D: combo). Recomendação do brief: **D**. **Você ainda não decidiu** — sem isso, P.S./gancho de E4/E5 fica genérico
3. **Áudio do W3** — Suriel precisa gravar entre 25-26/04. Script pronto no brief pág 16 (50-60s, tom baixo conversacional)
4. **Pós-live (29-30/04)** — brief sugere sequência de fechamento de carrinho 48h depois (não está na campanha original mas Suriel pode pedir)

## Automation (pós-clique do CTA do email)
Trigger: "Visits a web page" contém `live-28abr-confirmado`
→ Subscribe to **LIVE-28ABR-CONFIRMADOS** (list ID 8)
→ Add tag `quer-live-ia-28abr` (tag ID 9)

## Métricas-alvo (brief pág 3)

| Métrica | Mínimo | Saudável | Excelente |
|---|---|---|---|
| Abertura email | 30% | 40% | 50%+ |
| Clique no botão CTA | 15% (~735) | 25% (~1.225) | 35%+ (~1.715) |
| Clique nos vídeos YouTube | 5% (~245) | 10% (~490) | 15%+ (~735) |
| Confirmados → ao vivo | 40% | 55% | 70%+ |
| Vendas via live (oferta) | 20 | 60 | 120+ |
