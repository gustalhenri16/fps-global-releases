# FPS Global — Downloads oficiais

Repositório público destinado exclusivamente à distribuição dos builds compilados do **FPS Global para PS5 13.60**. O desenvolvimento e o código-fonte são mantidos em um repositório separado e privado.

## Última versão: FPS Global v1.0.1

**[Baixar FPS Global v1.0.1](https://github.com/gustalhenri16/fps-global-releases/releases/tag/v1.0.1)**

Arquivo: `FPS-Global-v1.0.1-PS5-13.60.elf`.

Esta versão inclui autoload de patches compatíveis, botão Ativar/Desativar durante o jogo, preferências persistentes de desativação, atualização sob demanda de 9 repositórios, leitura de MC4/JSON/XML e interface web em modo escuro.

### Estrutura no PS5

```text
/data/fps60/
├── repos/
│   └── cheats/
│       ├── json/
│       ├── mc4/
│       │   └── PPSA11386_01.018.000.mc4
│       └── xml/
├── enabled.txt
├── disabled_v3.txt
└── fps60.log
```

Os patches baixados ou copiados manualmente são armazenados na mesma estrutura. Os repositórios **não precisam ser baixados a cada início do ELF**. O MC4 integrado do 007 First Light (`PPSA11386 / 01.018.000`) é instalado automaticamente na pasta `mc4` se estiver ausente.

### Instalação

1. Encerre o jogo e o payload antigo.
2. Envie o arquivo `FPS-Global-v1.0.1-PS5-13.60.elf` para o PS5 pelo loader de payloads compatível.
3. Abra `http://IP-DO-PS5:8060/` na mesma rede.
4. Verifique o jogo e a versão na aba Jogos. Use Ativar/Desativar quando necessário.
5. Para carregar um patch adicionado manualmente, coloque-o em `repos/cheats/{json,mc4,xml}` e reinicie o ELF.

Consulte os detalhes, fontes integradas e limitações no **[changelog v1.0.1](RELEASE-NOTES-v1.0.1.md)** e na descrição da release.

## Versões anteriores

- [FPS Global Beta v1.0](https://github.com/gustalhenri16/fps-global-releases/releases/tag/v1.0-beta) — versão beta original com banco de patches externo.

## Avisos

Software experimental: patches modificam a memória de processos do jogo. O patch deve corresponder ao Title ID e à versão exata; operações de memória não garantem 60 FPS reais em todos os jogos. Patches podem causar travamento e não são recomendados para partidas online.
