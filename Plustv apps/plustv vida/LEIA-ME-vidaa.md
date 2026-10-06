# PlusTV Player - TVs VIDAA (Hisense e outras)

VIDAA usa apps web "hospedados": você não envia um pacote, envia o ENDEREÇO do seu player. O Web Player (painel v821) já tem o modo TV para VIDAA.

Endereço do app:
- Geral: https://SEU-PAINEL/player?tv=vidaa
- Player de um servidor específico: https://SEU-PAINEL/player/LINK-DO-SERVIDOR?tv=vidaa

Modo TV: setas navegam, OK clica, Voltar volta/fecha o player (se não for tratado, a TV sai do app), teclas de mídia (play, pause, avançar, retroceder), foco destacado. Vale a mesma cobrança por ativos (Roku, LG, Samsung e VIDAA somam juntos) e a mesma configuração (tamanho das letras 130% por padrão, pastas adultas com PIN etc.). O app se atualiza sozinho pelo painel.

## Testar
1. No navegador da TV Hisense/VIDAA (ou pelo modo desenvolvedor do portal VIDAA), abra o endereço acima.
2. Navegue só com o controle e confira login, listas, reprodução ao vivo e Voltar.

## Publicar na VIDAA App Store
1. Cadastre-se no portal de desenvolvedores VIDAA (developer.vidaa.com) como empresa/pessoa.
2. Crie o app tipo "hosted/web app" informando o endereço acima, nome, descrição, categoria, classificação, política de privacidade, ícone e capturas (confira tamanhos e regras no portal, pois mudam).
3. Informe uma conta de teste (usuário/senha) e envie para análise.

## Importante
- O endereço fica gravado no cadastro da loja. Se você mudar de domínio, precisa atualizar/reenviar o cadastro. Para ficar seguro, use um domínio curto fixo que só redireciona para o painel e cadastre esse domínio na loja.
- Modelos VIDAA mais antigos têm navegador antigo: o Web Player mostra um aviso vermelho se a TV for antiga demais. Para TVs assim não há modo lite (diferente da Samsung).
- A VIDAA/Hisense reprova apps com conteúdo sem licença: apresente como player (o cliente entra com a conta do provedor).
- Nunca testado numa TV VIDAA real. Teste canais ao vivo (HLS/TS) em mais de um modelo.
