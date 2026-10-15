# forge-releases

As distribuições oficiais e versionadas do **FORGE — Executable AI Engineering Playbook**.

## O que é o FORGE

Uma playbook de engenharia com IA, do pedido a Produção, e um programa pequeno (Python, só biblioteca padrão) que impõe o que uma ferramenta consegue impor: a verificação do conteúdo exato, as aprovações humanas observadas na plataforma, e a promoção do mesmo artefacto de Qual a Produção.

## FORGE e forge-releases

| | |
|---|---|
| [paulojjardim/FORGE](https://github.com/paulojjardim/FORGE) | o código, a playbook e a documentação — a origem de cada versão |
| **paulojjardim/forge-releases** (este) | só as distribuições: uma GitHub Release por versão, com os artefactos construídos da tag do FORGE |

Este repositório não tem código do FORGE. Cada release aqui corresponde a uma tag `forge-vX.Y.Z` do FORGE.

## Como identificar uma versão oficial

Cada release (`forge-vX.Y.Z`) traz:

- `forge_ai_playbook-X.Y.Z-py3-none-any.whl` — o pacote, para o `pip`;
- `forge.pyz` — o mesmo, num só ficheiro, para correr sem instalar (`python forge.pyz`);
- `SHA256SUMS` — o SHA-256 de cada artefacto;
- `MANIFEST.json` — o produto, a versão, o commit e a árvore Git de origem, a data e os artefactos.

O `source_commit` do manifesto é o commit da tag `forge-vX.Y.Z` no FORGE.

## Como obter e verificar

```bash
curl -LO https://github.com/paulojjardim/forge-releases/releases/download/forge-v1.0.1/forge_ai_playbook-1.0.1-py3-none-any.whl
curl -LO https://github.com/paulojjardim/forge-releases/releases/download/forge-v1.0.1/SHA256SUMS
sha256sum -c SHA256SUMS --ignore-missing
```

## Como usar num projeto

A CI do projeto instala o FORGE pela variável **`FORGE_SOURCE`** (GitHub: Settings → Secrets and variables → Actions → Variables) — uma especificação do `pip`, **fixada por hash**:

```
forge-ai-playbook @ https://github.com/paulojjardim/forge-releases/releases/download/forge-v1.0.1/forge_ai_playbook-1.0.1-py3-none-any.whl#sha256=2ad561b6c4724b3fadd425d5e157ddb9fb38b8d9e31611caa31fb5d6843ed8e6
```

Na máquina de quem trabalha, o mesmo:

```bash
python -m pip install "forge-ai-playbook @ https://github.com/paulojjardim/forge-releases/releases/download/forge-v1.0.1/forge_ai_playbook-1.0.1-py3-none-any.whl#sha256=2ad561b6c4724b3fadd425d5e157ddb9fb38b8d9e31611caa31fb5d6843ed8e6"
forge --version
```

Depois, `forge console` (**Setup**) ou `forge adopt`. O guia: o [Quick Start](https://github.com/paulojjardim/FORGE/blob/forge-v1.0.1/docs/FORGE_QUICKSTART.md) e o [manual de instalação e administração](https://github.com/paulojjardim/FORGE/blob/forge-v1.0.1/docs/FORGE_INSTALL_AND_ADMIN.md).

## Versões

| Versão | Tag no FORGE | Commit de origem |
|---|---|---|
| 1.0.1 | [forge-v1.0.1](https://github.com/paulojjardim/FORGE/releases/tag/forge-v1.0.1) | `81a13ff` |

A `1.0.0` foi distribuída pelo repositório `forge-proof`, hoje arquivado; as releases dele continuam a descarregar-se.
