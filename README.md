# FPS Global — Downloads oficiais

**FPS Global Beta v1.0** é um payload experimental para **PS5 13.60** que permite aplicar patches de 60 FPS em jogos e versões compatíveis, com interface web e controle de ativação/desativação.

## Download

**[Baixar FPS Global Beta v1.0](https://github.com/gustalhenri16/fps-global-releases/releases/tag/v1.0-beta)**

Na página da versão, baixe o **pacote ZIP** completo (recomendado) ou os arquivos individuais:

- `FPS-Global-Manual-13.60.elf` — payload para o PS5
- `patches.db` — catálogo de patches compatíveis
- `SHA256SUMS.txt` — somas SHA-256 para verificar os arquivos

## Como usar

1. Feche o jogo e encerre versões anteriores do FPS Global.
2. Carregue `FPS-Global-Manual-13.60.elf` pelo método de payload compatível com seu PS5.
3. Caso já exista `/data/fps60/patches.db`, **faça backup** e substitua-o pelo arquivo desta versão.
4. Inicie um jogo com patch suportado: o autoload verifica título e versão. Use a interface do FPS Global para ativar/desativar o patch durante a sessão.

## O que inclui a Beta v1.0

- Autoload de patches compatíveis por jogo e versão.
- Botão de **ativar/desativar** com o jogo aberto.
- Controle do **007 First Light — PPSA11386 / 01.018.000**, incluindo os **3 offsets do MC4** e a rotina de desativação validada em teste real no PS5.
- Notificações com nome do jogo, estado **60 FPS Ativado / Desativado** e crédito do criador.
- Interface web com modo escuro e catálogo de 181 grupos de patches.

## Enviar patches adicionais

A comunidade pode contribuir com patches para futuras versões, enviando arquivos para:

- [`cheats/mc4/`](cheats/mc4/) — arquivos MC4
- [`cheats/json/`](cheats/json/) — arquivos JSON
- [`cheats/xml/`](cheats/xml/) — arquivos XML

Leia as [instruções de contribuição](cheats/README.md) e abra um Pull Request informando jogo, Title ID, versão e créditos do patch.

**Atenção:** patches enviados nessas pastas **não são ativados automaticamente** pela Beta v1.0. Cada patch precisa ser revisado e incluído em uma compilação futura.

## Avisos

- **Beta experimental.** O funcionamento real de liga/desliga foi confirmado no 007 First Light na versão indicada; outros jogos não estão necessariamente validados.
- Patches atuam na **memória do processo em execução**, não nos arquivos instalados do jogo. Use por sua conta e risco; podem ocorrer travamentos.
- Nem todos os jogos suportam 60 FPS e mudar os valores de memória não garante que o motor gráfico mudará imediatamente o limite.
- Este é o **repositório público de downloads**. O código-fonte de desenvolvimento não é distribuído aqui.

## Versões

Acompanhe as versões na seção **[Releases](https://github.com/gustalhenri16/fps-global-releases/releases)**. Para verificar a integridade dos downloads, execute `sha256sum -c SHA256SUMS.txt` na pasta dos arquivos.
