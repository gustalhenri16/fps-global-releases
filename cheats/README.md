# Patches da comunidade

Este diretório recebe **patches adicionais enviados pela comunidade** para o FPS Global.

## Envie o arquivo na pasta correta

| Formato | Pasta | Exemplo de nome |
|---|---|---|
| CheatRunner MC4 | [`mc4/`](mc4/) | `PPSA12345_01.000.000.mc4` |
| CheatRunner JSON | [`json/`](json/) | `PPSA12345_01.000.000.json` |
| XML de patch | [`xml/`](xml/) | `PPSA12345_01.000.000.xml` |

**Padrão de nome sugerido:** `PPSA12345_01.000.000.ext` (ID do jogo, versão exata e formato). Um sufixo descritivo pode ser incluído, por exemplo `PPSA12345_01.000.000_60fps.mc4`.

## Como contribuir

1. Faça um **fork** deste repositório público.
2. Envie o arquivo na pasta correspondente (`cheats/mc4`, `cheats/json` ou `cheats/xml`).
3. Abra um **Pull Request** (PR) descrevendo o jogo, o ID `PPSA`, a versão exata, o objetivo do patch, os créditos do autor e se foi testado em PS5.
4. Mantenha os valores originais ON/OFF; não remova offsets, mesmo que os bytes ON e OFF sejam iguais.

**Importante:** os arquivos aqui são **contribuições para análise**. Colocar um patch nessa pasta **não instala**, **não ativa** e **não adiciona automaticamente** esse patch à Beta v1.0 nem ao `patches.db` distribuído. Patches precisam ser revisados, validados e incorporados em uma compilação posterior. Não envie conteúdo não autorizado, código-fonte privado, dados pessoais ou segredos. Patches de memória são experimentais e podem causar travamentos.

Este repositório distribui somente downloads compilados e arquivos de patches enviados pela comunidade — **não** o código-fonte do FPS Global.
