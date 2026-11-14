# FPS Global v1.0.1 — PS5 13.60

Payload nativo **ELF** para aplicar patches compatíveis de FPS em jogos PS5. Esta versão corrige a notificação de inicialização (antes mostrava **v0.01**, agora mostra **v1.0.1**) e reúne as funcionalidades da Beta: patches locais MC4/JSON/XML, catálogo integrado, atualização de repositórios, ativação/desativação durante o jogo e interface em modo escuro.

## O que está implementado

- **Autoload:** um patch local ou integrado compatível pode ser aplicado automaticamente ao iniciar o jogo, quando existe uma escolha única para o Title ID e a **versão exata** instalada. Um MC4 local compatível tem prioridade sobre um JSON local antigo.
- **Ativar / Desativar:** o botão na aba **Jogos** aplica o patch na memória do processo e tenta restaurar os bytes OFF explícitos ou os valores originais capturados. As escritas são verificadas; caso a restauração não seja segura, o aplicativo informa a falha em vez de afirmar que desligou.
- **Preferências persistentes:** o estado escolhido pelo usuário é salvo. Desativar um patch impede a reativação automática ao reabrir o jogo ou reiniciar o ELF, até que o usuário ative novamente.
- **Notificações:** mensagens de **60 FPS Ativado** e **60 FPS Desativado**, com o nome do jogo e os créditos do autor, quando aplicáveis.
- **Patches externos:** importação de arquivos **MC4 criptografado (CheatRunner), JSON e XML** compatíveis com o carregador nativo, para o executável `eboot.bin`. Arquivos incompatíveis são ignorados e registrados no log.
- **Interface web:** aba Jogos, lista de patches por jogo/versão, indicação de aplicação, atualização de repositórios, logs e **modo escuro**.
- **Catálogo:** mantém os patches integrados da Beta; não exige um `patches.db` externo para o ELF desta release.

## Estrutura de arquivos no PS5

O ELF cria automaticamente a árvore unificada, usada **tanto por patches adicionados manualmente quanto pelos baixados dos repositórios**:

```text
/data/fps60/
├── repos/
│   └── cheats/
│       ├── json/       # Patches JSON
│       ├── mc4/        # Patches MC4
│       │   └── PPSA11386_01.018.000.mc4
│       └── xml/        # Patches XML
├── enabled.txt         # Preferências ON
├── disabled_v3.txt     # Preferências OFF persistentes
└── fps60.log           # Diagnóstico
```

Pastas antigas como `/data/fps60/cheats/{json,mc4,xml}` e `/data/fps60/repos/{json,mc4,xml}` são migradas quando possível **sem sobrescrever os arquivos existentes**. Arquivos transferidos manualmente são detectados na próxima inicialização do ELF.

### 007 First Light — MC4 integrado ao ELF

- Jogo: **007 First Light**, Title ID `PPSA11386`.
- Versão exata: **`01.018.000`**.
- Arquivo: `/data/fps60/repos/cheats/mc4/PPSA11386_01.018.000.mc4`.
- O ELF **instala o MC4 automaticamente se ele ainda não existir**, preservando qualquer arquivo já presente nesse caminho. A implementação usa o carregador MC4 genérico, sem uma rotina especial de escrita para esse jogo.
- O patch mantém suas três escritas originais e os créditos **by gusta**. Uma variante de versão diferente não deve ser aplicada à `01.018.000`.

## Atualizar repositórios

Na interface web, clique em **Atualizar Repositórios** para consultar estas 9 fontes:

1. [Illusion / PS-Game-Patch](https://github.com/illusionyy/PS-Game-Patch)
2. [CheatRunner Patches](https://github.com/notmaj0r/CheatRunner_Patches)
3. [adnmix](https://github.com/adnmix/playstation-game-patches)
4. [Nikoru14](https://github.com/Nikoru14/Fatal-Frame-2-Remake-60FPS-Patch-PS5)
5. [RDX-Sci01](https://github.com/RDX-Sci01/HEN-PPSA-Cheats)
6. [HEN Cheats / TeeKay87](https://github.com/TeeKay87/HEN-Cheats-Collection)
7. [etaHEN](https://github.com/etaHEN/PS5_Cheats)
8. [CN Cheats Collection](https://github.com/a83848400/CN-Cheats-Collection)
9. [GoldHEN](https://github.com/GoldHEN/GoldHEN_Cheat_Repository)

O atualizador consulta os índices, baixa candidatos, valida se são patches PS5/60 FPS compatíveis e os salva por formato em **`repos/cheats/json`**, **`repos/cheats/mc4`** ou **`repos/cheats/xml`**. Arquivos idênticos já salvos não são regravados. A interface informa quantos arquivos foram verificados, importados, ignorados ou rejeitados, incluindo contadores de MC4.

**Os arquivos baixados ficam salvos no PS5:** **não é necessário atualizar os repositórios toda vez que o ELF inicia**. O botão faz uma nova consulta quando acionado.

Após a atualização, os patches online para **jogos e versões instalados** entram na lista Jogos **sem reiniciar o ELF**. Novos patches baixados **não são aplicados automaticamente**: é necessário ativá-los explicitamente. Arquivos adicionados manualmente por FTP são lidos na inicialização do ELF.

## Instalação e uso

1. Feche o jogo e encerre qualquer execução anterior do payload.
2. Baixe o arquivo **`FPS-Global-v1.0.1-PS5-13.60.elf`** nos Assets desta release e envie pelo loader de payloads do PS5.
3. Abra **`http://IP-DO-PS5:8060/`** no navegador do PC ou celular da mesma rede.
4. Consulte a aba **Jogos**, confira o Title ID e a versão exata, e use **Ativar / Desativar** quando necessário.
5. Se adicionar um arquivo MC4/JSON/XML manualmente, coloque-o na pasta correspondente em `/data/fps60/repos/cheats/` e reinicie o ELF para importá-lo.
6. Para conferir aplicação ou erros, veja `/data/fps60/fps60.log` e um contador de FPS no console.

## Limitações importantes

- **Não é um desbloqueio global garantido de 60 FPS**: cada patch deve corresponder à versão exata do jogo e à lógica de limitação de FPS desse título.
- A indicação de patch aplicado confirma a operação de memória monitorada pelo aplicativo, **não a taxa real de quadros**. Alguns jogos podem continuar abaixo de 60 FPS por limites internos ou de desempenho.
- A restauração OFF pode ser recusada quando a memória foi alterada pelo jogo ou por outro payload; isso evita sobrescrever dados desconhecidos.
- Os formatos e patches de terceiros precisam ser compatíveis com o carregador desta versão; nem todos os cheats genéricos são patches FPS ou suportam reversão.
- **Beta/uso experimental.** A compilação e os testes automatizados não substituem testes em PS5 real. Evite usar patches de memória em partidas online.

**Arquivo principal desta release:** `FPS-Global-v1.0.1-PS5-13.60.elf`. Binário idêntico ao compilado e verificado para esta versão, distribuído neste repositório público de downloads.
