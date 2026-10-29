# Plano América — Funil com Quiz + Oferta de Saída

Site estático (HTML, CSS e JavaScript), com imagens locais otimizadas em WebP.

## Fluxo
- Entrada com cinco perguntas Sim/Não.
- Tela de oferta do **Plano América — R$ 17,99**.
- Clique em **QUERO SAIR DO BRASIL!** leva a `https://payfast.greenn.com.br/redirect/809892`.
- No desktop, ao sair com o ponteiro pelo topo, após 6,5 s, abre uma oferta especial. No celular, a oferta pode surgir após um gesto claro de rolagem para cima, e também há um link explícito na tela final.
- Oferta especial de **R$ 22,90** (`https://payfast.greenn.com.br/89j3m7f`), descrita na página como Plano América, Plano Portugal, Plano Espanha e Kit Prático. **Confira no Greenn se os quatro materiais estão realmente incluídos nesse checkout e entregues após a compra.**
- Contador de dez minutos, iniciado na primeira apresentação da oferta, persistido no `localStorage` entre atualizações, que desabilita o CTA nesta página ao expirar. O contador **não altera nem expira automaticamente o preço dentro do Greenn**: configure essa mesma limitação no checkout ou retire a promessa de tempo limitado antes de veicular campanhas.
- É possível fechar por X, Escape, fundo do modal ou "Prefiro continuar". A oferta de saída aparece no máximo uma vez por sessão; o link explícito permite reabrir enquanto o contador estiver ativo.

## Configuração
No `index.html`, localize `window.PLANO_AMERICA_CONFIG` para editar:
- `checkoutUrl` (compra principal)
- `comboCheckoutUrl` (pacote completo)
- `price` (R$ 17,99)
- `comboPrice` (R$ 22,90)
- `comboMinutes` (10)
- `guaranteeDays` (7)
- `preserveUtm` (true)

## Publicação
Envie `index.html` junto com a pasta `assets/` para a raiz de sua hospedagem. Mantenha os caminhos relativos. Não precisa de servidor de aplicações.

## Medição
O código envia ao `dataLayer` (caso presente): `quiz_start`, `quiz_answer`, `quiz_complete`, `view_offer`, `begin_checkout` (com `offer` principal/combo), `combo_view`, `combo_dismiss`, `combo_expired`. Adicione seu container GTM e configure os acionadores conforme a sua conta. Não há tag nem Pixel instalados por padrão.

## Cuidados comerciais
- Revise conteúdo e entregáveis do combo; não anuncie algo que o checkout não entrega.
- Certifique-se de que as regras da promoção de 10 minutos são implementadas no checkout, além do temporizador de interface.
- A garantia de 7 dias indicada para o guia principal deve estar refletida nos termos e processo real de reembolso.
- O material é informativo; não oferece garantia de imigração, emprego ou visto.
