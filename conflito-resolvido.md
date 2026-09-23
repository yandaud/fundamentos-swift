# Conflito de merge resolvido

## Contexto
Conflito criado de forma controlada para praticar a resolução manual.

- **Arquivo:** `README.md`
- **Trecho:** linha logo abaixo de `## Objetivo`
- **Branches envolvidas:** `main` × `feature/modulos-guia`

## Como o conflito foi gerado
1. Na `feature/modulos-guia`, o objetivo foi alterado no commit `docs(readme): detalha objetivo do guia`.
2. Na `main`, a **mesma linha** foi alterada de outra forma no commit `docs(readme): reescreve objetivo com foco em iOS`.
3. Ao rodar `git merge main` dentro da feature, o Git não conseguiu decidir sozinho qual versão manter.

## Marcadores exibidos pelo Git

```text
## Objetivo
<<<<<<< HEAD
Aprendizado em linguagem Swift, do zero até o primeiro app para iOS.
=======
Ensinar os fundamentos de Swift a iniciantes, com foco no desenvolvimento para iOS.
>>>>>>> main
```

| Marcador | Significado |
|---|---|
| `<<<<<<< HEAD` | Início da versão da branch atual (`feature/modulos-guia`) |
| `=======` | Separa as duas versões |
| `>>>>>>> main` | Fim da versão que veio da `main` |

## Decisão
Nenhuma versão foi descartada inteira. Mantive o início da `main` (deixa claro o público: iniciantes) e o final da feature (meta concreta: primeiro app para iOS).

Resultado final:

```text
## Objetivo
Ensinar os fundamentos de Swift a iniciantes, do zero até o primeiro app para iOS.
```

## Comandos usados

```bash
git switch feature/modulos-guia
git merge main
# CONFLICT (content): Merge conflict in README.md
# edição manual do README.md, removendo os três marcadores
git add README.md
git commit -m "chore(merge): resolve conflito no objetivo do README"
git push
```

## Verificação
- `git status` sem arquivos em conflito.
- `grep -n "<<<<<<<\|>>>>>>>" README.md` sem resultados.
- O pull request deixou de mostrar *This branch has conflicts*.

## Lição
Conflito não é erro: é o Git pedindo uma decisão humana quando duas pessoas (ou branches) mudam o mesmo trecho. Commits pequenos e integração frequente com a `main` deixam os conflitos menores e mais fáceis de resolver.
