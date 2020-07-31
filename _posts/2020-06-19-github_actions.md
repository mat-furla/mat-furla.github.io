---
layout: article
title: Github Actions - Entendendo a Ferramenta e Empacotando uma Aplicação Angular
tags: Angular Electron Github
aside:
  toc: true
article_header:
  type: cover
  image:
    src: https://i.imgur.com/8jLPDnO.png
---

Existem algumas práticas que estão sendo cada vez mais colocadas em execução nas áreas de desenvolvimento
de software, estas são chamadas de *Continuous Integration* (CI) e envolvem os desenvolvedores integrarem
seus códigos em um repositório compartilhado e terem tarefas de *build*, *deploy* e *error tests*
completamente automatizadas nesse ambiente. Este é um assunto bem complexo e pode ser dividido em
inúmeros tópicos que não cabem nesse artigo, caso deseje ler mais sobre isso recomendo o seguinte post, 
[Continuous Integration Essentials](https://codeship.com/continuous-integration-essentials).

Várias ferramentas surgiram nesse contexto e se diferenciam em relação a preços, se são projetos
comerciais ou públicos, etc. As mais famosas são:

 - [Travis CI](https://travis-ci.org/)
 - [Jenkins](https://www.jenkins.io/)
 - [Circle CI](https://circleci.com/)

Abordaremos aqui uma ferramenta criada pelo próprio *GitHub*, o [Github Actions](https://github.com/features/actions) e como forma de exemplo empacotaremos uma
aplicação Angular para a plataforma Windows.



## <i class="las la-lg la-code-branch"></i> Entendendo o Github Actions

Primeiramente acho que vale responder a pergunta, o que é o *Github Actions*?

Segundo a definição do próprio *Github*:

"GitHub Actions makes it easy to automate all your software workflows, now with world-class CI/CD. Build, test, and deploy your code right from GitHub. Make code reviews, branch management, and issue triaging work the way you want"
{:.info}

Explicando bem sucintamente, criaremos uma lista de ações (*workflows*) que serão ativados através de ações determinadas, como
por exemplo, *push* em um repositório específico, criação de tags de versão, quando erros são reportados
etc, etc. As possibilidades são ilimitadas.

O *Actions* oferece algumas vantagens quanto aos outros serviços se você já utiliza o *Github*, como a
possibilidade de utilizar com repositórios privados.



## <i class="las la-lg la-folder-open"></i> Preparando o Repositório

Como durante o processo serão necessárias algumas mudanças entre os diretórios é importante deixar claro
desde o início como a aplicação está estruturada:

```
Main_Directory
└── Angular_Application
    ├── dist
    ├── e2e
    ├── node_modules
    ├── src
    ├── angular.json
    ├── browserslist
    ├── karma.conf.js
    ├── package-lock.json
    ├── package.json
    ├── tsconfig.app.json
    ├── tsconfig.json
    ├── tsconfig.spec.json
    └── tslint.json
```

---