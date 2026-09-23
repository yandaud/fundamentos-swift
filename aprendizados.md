# Aprendizados — Reflexão final

## Sobre o projeto
O guia *Fundamentos de Swift* foi o conteúdo; o objetivo real foi praticar um fluxo de trabalho completo com Git e GitHub: branches, commits padronizados, pull request, conflito e publicação na `main`.

## O que aprendi

**Branches.** Trabalhar em `feature/modulos-guia` deixou a `main` sempre estável. Só o que foi revisado no pull request entrou nela.

**Commits atômicos e padronizados.** Cada commit registra uma única mudança (um módulo, um ajuste no README, um documento). Usar o padrão Conventional Commits (`docs:`, `docs(readme):`, `chore:`) deixou o histórico fácil de ler: dá para entender o projeto só pelo `git log --oneline`.

**Pull request.** O PR reuniu descrição, checklist e comentários de revisão em um só lugar. Mesmo trabalhando sozinho, revisar o próprio diff antes do merge ajudou a achar erros.

**Conflito de merge.** Aprendi a ler os marcadores `<<<<<<<`, `=======` e `>>>>>>>` e que resolver um conflito é uma decisão de conteúdo, não só técnica: a versão final combinou o melhor das duas.

## Dificuldades
- Entender qual lado era `HEAD` e qual era a branch que estava sendo integrada.
- Lembrar de fazer `push` depois de resolver o conflito para o PR ser atualizado.
- Escolher o tipo de merge no GitHub: o *merge commit* preserva os commits atômicos; o *squash* juntaria tudo em um só.

## O que eu faria diferente
- Proteger a `main` para aceitar mudanças só via pull request.
- Criar um modelo de PR (`.github/pull_request_template.md`) para padronizar descrições.
- Integrar a `main` na feature com mais frequência para evitar conflitos grandes.

## Conclusão
Git deixou de ser só "salvar o código" e passou a ser uma forma de organizar o trabalho, documentar decisões e colaborar com segurança.
