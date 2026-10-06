# PlusTV Player - Canal Roku (v1.6)

v1.6 - ATUALIZAR SEM REENVIAR À LOJA
A Roku NÃO permite que um canal baixe código novo da internet: telas e lógica novas só entram enviando um novo pacote na loja. Por isso este pacote já vem "dirigido pelo painel":
- Tudo que é servidor (login, planos, Pix, DNS, cobrança, endpoints, regras) muda só publicando o painel — a TV não precisa de nada.
- Ajustes do canal (aviso na tela, modo manutenção, tempos de pular abertura, salto das setas, contagem do próximo episódio) ficam em Admin > Web Player > "Ajustes remotos do canal Roku" e valem na hora em todas as TVs.
- Logo e cores do dono já vêm do painel.
Só será preciso reenviar o pacote para mudanças de código do canal (telas/botões novos). Mantenha o endereço do painel (PANEL_URL) sempre o mesmo domínio.


v1.5: controles estilo Netflix em filmes/séries: Esquerda/Direita = -10s/+10s, Retroceder/Avançar = -30s/+30s, OK = pausar, barra de progresso com o tempo; "Pular abertura" nas séries (primeiros 2:30, pula para 1:30) e contagem "Próximo em 10" à direita (OK muda na hora). A Roku não permite imagem de prévia do quadro sem arquivos BIF do servidor; a prévia mostra o tempo.

v1.4: aviso 1 dia antes do vencimento (e no dia, e quando já venceu) com botões Renovar/Fechar. Se o servidor tiver Mercado Pago conectado e o cliente for cadastrado no sistema, a TV mostra o QR Code Pix, confirma o pagamento sozinha e renova o acesso; senão aparece só "Fechar". Tudo funciona só com o controle remoto (setas, OK e Voltar).
v1.3: MAC / ID da TV nas Configurações.

v1.2: novo menu Configurações (Formato do fluxo, Próximo episódio automático, Alterar PIN, Conteúdo adulto com PIN, Pastas ocultas, Refazer reconhecimento do aparelho).

Novidades da v1.1
- Depois do login aparece "Carregando conteúdos..." com barra e etapas Canais / Filmes / Séries; o menu só abre quando termina.
- "Formato do fluxo" (agora dentro de Configurações): Automático, HLS (m3u8) ou TS (OK alterna).
  No Automático o canal usa o formato que já funcionou nesta Roku e, se falhar, troca sozinho para o outro. Filmes/séries que falharem tentam também a versão .mp4.
- Requer o painel v807 ou mais novo (endpoint /api/public/roku/login).

## Instalar para teste (modo desenvolvedor)
1. Na Roku: Home x3, Cima x2, Direita, Esquerda, Direita, Esquerda, Direita. Ative o modo desenvolvedor e crie uma senha. Anote o IP.
2. No computador (mesma rede): http://IP-DA-ROKU, usuário `rokudev` e a senha criada.
3. Upload -> escolha plustv-roku-canal.zip -> Install. O canal abre sozinho.

## Configuração
- Endereço do painel: função PANEL_URL() no início de components/MainScene.brs (hoje https://konnex.business). Se mudar, gere o zip de novo (o manifest precisa ficar na raiz do zip).
- A cada nova versão para a loja, aumente build_version (e minor/major) no manifest.

## Publicar na Roku Channel Store (resumo)
1. Crie conta gratuita em developer.roku.com e ative o modo desenvolvedor na sua Roku.
2. Gere a chave de assinatura: conecte por telnet/SSH ao IP da Roku (porta 8085), rode `genkey`, anote a senha e o "DevID" e guarde o arquivo de senha. NUNCA perca essa chave: ela assina todas as atualizações do canal.
3. Com o zip instalado, abra http://IP-DA-ROKU > "Packager": informe nome do app e a senha da chave > "Package". Baixe o arquivo .pkg.
4. No Developer Dashboard > Manage My Channels > Add Channel > Non-Certified/Public Channel (canal público exige certificação). Faça upload do .pkg.
5. Preencha: nome, descrição, categoria (ex.: Mídia/Entretenimento), classificação indicativa, país/idioma, URL da política de privacidade, e-mail/URL de suporte.
6. Imagens da loja (tamanhos do dashboard, confira lá): poster HD 540x405 e SD 290x218, mais capturas de tela 1280x720. O ícone do menu (336x210 / 246x140) e a splash já estão no pacote.
7. Informe o tipo de acesso: canal com login (usuário e senha do cliente). A Roku pede uma conta de teste: crie um usuário válido de teste e informe nos campos de teste/notas.
8. Envie para certificação e aguarde a revisão (costuma levar de alguns dias a semanas). Corrija o que a Roku apontar e reenvie.

Alternativa sem certificação: no Dashboard crie um canal NÃO certificado (beta) e compartilhe o código de acesso (link roku.com/add/CÓDIGO). Quem tiver o código instala direto na TV, sem passar pela revisão, com limite de uso.

## Atenção para aprovação
- A Roku reprova canais que distribuem conteúdo sem licença. Descreva o app como player: o cliente entra com a própria conta do provedor, o app não traz canais próprios. Não use nomes/logos de terceiros nem a palavra "IPTV pirata"/listas públicas nas imagens e descrições.
- Precisa de política de privacidade pública (pode ser uma página no seu site).
- Teste em Roku real (nunca testado nesta versão) e confira o Voltar/OK em todas as telas, pois a revisão testa isso.
