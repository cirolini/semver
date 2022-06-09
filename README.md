# semver

## O que é esse repo?

É para explicar o modelo de versionamento semântico utilizado e como podemos aplicar ele em nossos projetos. Utilizamos uma aplicação chamada [semantic-release](https://github.com/semantic-release/semantic-release/), que faz o trabalho de analisar nossas commit msg e a partir de tags especificas consegue gerar uma release versionada automaticamente das nossas aplicações.

Utilizamos os mesmos conceitos do [semver](https://semver.org/lang/pt-BR/). O resumo da definição esta  aqui em baixo, mas recomendo que leiam toda a documentação do site.

>Dado um número de versão MAJOR.MINOR.PATCH, incremente a:
>
>1. versão Maior(MAJOR): quando fizer mudanças incompatíveis na API,
>1. versão Menor(MINOR): quando adicionar funcionalidades mantendo compatibilidade, e
>1. versão de Correção(PATCH): quando corrigir falhas mantendo compatibilidade.
>
>Rótulos adicionais para pré-lançamento(pre-release) e metadados de construção(build) estão disponíveis como extensão ao >formato MAJOR.MINOR.PATCH.

## Como usar esse repo?

Para você utilizar o mesmo conceito de releases semanticas, veja o video que vou gravar e colocar o link aqui em breve. Depois disso copie o arquivo `.github/workflows/release.yml` e o `.releaserc` para o seu projeto, faça pequenas alterações para tudo funcionar e [voila](https://i.pinimg.com/564x/8a/1e/44/8a1e44ccbe9a13519f515d658f9998d3.jpg).

## Como formatar meus PRs?

Por default, o semantic-release usa a [Angular Commit Message Conventions](https://github.com/angular/angular/blob/master/CONTRIBUTING.md#-commit-message-format), mas podem ver outras formas que ele suporta em na pagina do [plugin](https://github.com/semantic-release/commit-analyzer#options), então de forma resumida:

```
<type>(<scope>): <short summary>
  │       │             │
  │       │             └─⫸ Summary in present tense. Not capitalized. No period at the end.
  │       │
  │       └─⫸ Commit Scope: animations|bazel|benchpress|common|compiler|compiler-cli|core|
  │                          elements|forms|http|language-service|localize|platform-browser|
  │                          platform-browser-dynamic|platform-server|router|service-worker|
  │                          upgrade|zone.js|packaging|changelog|docs-infra|migrations|ngcc|ve|
  │                          devtools
  │
  └─⫸ Commit Type: build|ci|docs|feat|fix|perf|refactor|test
```

O `<type>` e `<summary>` campos são obrigatórios, o campo `(<scope>)` é opcional.


### Type

Must be one of the following:

* **build**: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
* **ci**: Changes to our CI configuration files and scripts (examples: CircleCi, SauceLabs)
* **docs**: Documentation only changes
* **feat**: A new feature
* **fix**: A bug fix
* **perf**: A code change that improves performance
* **refactor**: A code change that neither fixes a bug nor adds a feature
* **test**: Adding missing tests or correcting existing tests


### Summary
Use the summary field to provide a succinct description of the change:

* use the imperative, present tense: "change" not "changed" nor "changes"
* don't capitalize the first letter
* no dot (.) at the end

## Exemplos de PRs

| Commit message                                                                                                                                                                                   | Release type               |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------- |
| `fix(pencil): stop graphite breaking when too much pressure applied`                                                                                                                             | ~~Patch~~ Fix Release      |
| `feat(pencil): add 'graphiteWidth' option`                                                                                                                                                       | ~~Minor~~ Feature Release  |
| `perf(pencil): remove graphiteWidth option`<br><br>`BREAKING CHANGE: The graphiteWidth option has been removed.`<br>`The default graphite width of 10mm is always used for performance reasons.` | ~~Major~~ Breaking Release <br /> (Note that the `BREAKING CHANGE: ` token must be in the footer of the commit) |
