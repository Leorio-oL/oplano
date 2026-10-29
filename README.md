# Plano América — Funil com Quiz + Oferta de Saída

Site estático (HTML, CSS e JavaScript), com imagens locais otimizadas em WebP.

## Fluxo
- Entrada com cinco perguntas Sim/Não.
- Tela de oferta do **Plano América — R$ 17,99**.
- Clique em **QUERO SAIR DO BRASIL!** leva a `https://payfast.greenn.com.br/redirect/809892`.
- No desktop, ao mover o ponteiro para fora pelo topo, após 6,5 s, abre a oferta especial. No celular, depois de concluir o quiz, o pop-up abre após 11 segundos de visualização da oferta ou diante de um gesto de retorno por rolagem. A oferta aparece no máximo uma vez por sessão.
- Oferta especial de **R$ 22,90** (`https://payfast.greenn.com.br/89j3m7f`), descrita na página como Plano América, Plano Portugal, Plano Espanha e Kit Prático. **Confira no Greenn se os quatro materiais estão realmente incluídos nesse checkout e entregues após a compra.**
- Contador de dez minutos, iniciado na primeira apresentação da oferta, persistido no `localStorage` entre atualizações, que desabilita o CTA nesta página ao expirar. O contador **não altera nem expira automaticamente o preço dentro do Greenn**: configure essa mesma limitação no checkout ou retire a promessa de tempo limitado antes de veicular campanhas.
- É possível fechar por X, Escape, fundo do modal ou "Prefiro continuar". O link **"Conhecer o pacote com todos os guias"** agora vai **diretamente** ao checkout de R$ 22,90, mesmo se o pop-up já tiver sido fechado. O temporizador do pop-up não controla a validade desse link.

## Ajustes desta revisão
- Corrigido o link "Conhecer o pacote com todos os guias": usa um `<a href>` real, com URL de checkout configurada, rastreamento de clique e preservação de UTMs.
- Fonte de **7 dias de garantia** aumentada para 15 px no desktop e 14 px no mobile, com selo de destaque.
- Pop-up revisado: layout responsivo com rolagem interna nas telas menores, botão e fechamento visíveis, suporte a mobile após 11 segundos na tela final.
- Mantidos scripts de rastreamento, imagens, copy e demais ajustes do ZIP enviado.

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
