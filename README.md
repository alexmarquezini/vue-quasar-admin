<p align="center">
    <a href="https://quasar-framework.org">
        <img width="200" src="https://quasar-framework.org/images/logo/xxhdpi.png">
    </a>
</p>

## vue-quasar-admin
&emsp;&emsp;[Quasar-Framework](https://quasar-framework.org/) é um framework de front-end de código aberto baseada em vue.js, que pode ajudar os desenvolvedores da web a criar rapidamente os seguintes sites: sites responsivos, aplicativos progressivos, aplicativos móveis (via Cordova), aplicativos de plataforma cruzada (via Electron).
&emsp;&emsp;O Quasar permite que os desenvolvedores publiquem em sites de várias plataformas, PWA, Mobile App e Electron App sem escrever o código uma vez. Ao usar o Quasar, você nem precisa do Hammerjs, Momentjs ou Bootstrap. Coisas, você pode usá-las muito facilmente. [vue-quasar-admin](http://jaycewu.coding.me/vue-quasar-admin) é um conjunto de sistema de gerenciamento de segundo plano baseado no Quasar-Framework que contém controle de permissão geral (atualmente apenas para PC).

[![](https://ci.appveyor.com/api/projects/status/github/wjkang/vue-quasar-admin?branch=master&svg=true)]()
[![vue](https://img.shields.io/badge/vue-2.5.16-brightgreen.svg)](https://github.com/vuejs/vue)
[![quasar framework](https://img.shields.io/badge/quasar-0.15.14-brightgreen.svg)](https://quasar-framework.org/)
[![MIT](https://img.shields.io/badge/license-MIT-brightgreen.svg)]()

[online demo ](http://jaycewu.coding.me/vue-quasar-admin)

Conta de login:

    admin 123

    test 123456

    website_admin 123456

Por favor, não modifique o nome da conta à vontade, outras operações são arbitrárias, você pode inicializar os dados através do botão "Inicialização de Dados" no canto superior direito.

## Fluxograma do sistema

![](https://raw.githubusercontent.com/wjkang/vue-quasar-admin/master/screenshot/flowchart.png)

## Funções e recursos

- Suporte de dados backend real
- Entrar / sair
- Layout flexível de Jiugongge
- Reduza a barra de menu esquerda
- navegação de tag
- Migalhas de pão
- Tela inteira / Sair da tela inteira
- Menu dinâmico
- O menu é dividido em módulos
- Controle de acesso geral
    - Controle de permissão de nível de menu
    - Controle de permissão de nível de interface
    - Controle de acesso em nível de elemento
- Efeito de carregamento globalmente configurável
- Tratamento de exceção de rede
- Módulo
    - Módulo de sistema
        - Configurações do sistema
            - Gestão do menu
        - gestão de autoridade
            - Gestão de funções
            - Gerenciamento de autoridade de função
            - Função de gerenciamento de usuários
            - Gerenciamento de funções do usuário
        - Organização
            - Gestão de departamento
            - Gestão de trabalho
        - Gestão de Usuários
    - Módulo do site
        - CMS
            - Gestão de artigos
    - Módulo de Desenvolvimento
        - Componentes oficiais
            - 。。。
        - Componente de negócios
            - sku
    - Registro de auditoria
    - Inicialização de dados

## Estrutura de arquivo
```shell
.
├── .quasar  Quasar CLI Configuração gerada
└── src
    ├── assets  recurso
    ├── components Componente personalizado
    ├── css Arquivo de estilo
    ├── layout Componente de layout
    ├── libs  Método de ferramenta
    ├── router  Configuração de roteamento
    ├── store  Gestão do estado
    ├── service  Gerenciamento de API
    ├── plugins  Componentes, instruções e plug-ins que requerem registro global
    └── pages
        ├── cms
        │   └── Gestão de artigos
        ├── develop
        │   ├── Componentes oficiais
        │   └── Componente de negócios
        ├── organization
        │   ├── Gestão de departamento
        │   └── Gestão de trabalho
        ├── other
        │   └── Registro de auditoria
        ├── permission
        │   ├── Gestão de funções
        │   ├── Gestão de permissões
        │   ├── Gerenciamento de autoridade de função
        │   ├── Função de gerenciamento de usuários
        │   └── Gerenciamento de funções do usuário
        ├── system
        │   ├── Gestão do menu
        ├── user
        │   └── Gestão de Usuários
        ├── 403 Sem página de permissão
        ├── index Casa
        └── login Página de login

```

## Instale e use

## Install
```bush
npm install -g vue-cli
```
```bush
npm install -g quasar-cli
```
```bush
npm install
```
## Run
### Development
```bush
quasar dev
```
### Production(Build)
```bush
quasar build
```

### Instalar daemon


[Programa de fundo](https://github.com/wjkang/quasar-admin-server)

```bush
git clone https://github.com/wjkang/quasar-admin-server.git
```

## Install
```bush
npm install
```
## Run
### Development
```bush
npm run start
```
### Production(Build)
```bush
npm run production
```
Uso de programa de back-end[koa2](https://github.com/koajs/koa)Construir e usar[lowdb](https://github.com/typicode/lowdb)Persista os dados em arquivos JSON (usar o armazenamento de arquivos JSON é para construir rapidamente demos).

## Etapas de desenvolvimento de funções (tome o gerenciamento de artigos como exemplo)
- a parte dianteira
    - Definir código de função：
    - post_view  - Visualização da lista de artigos
    - post_edit - Editor de artigos
    - post_del  - Excluir artigo
    - Nova página de lista de artigos  post.vue
    - Adicionar rota
    - Use a função de gerenciamento de menu para adicionar menus relacionados de "Gerenciamento de artigos". O nome do menu deve ser consistente com o campo de nome da rota adicionado na etapa anterior. Código de permissão Preencha o código de permissão definido da função "Exibir lista de artigos" (controle de permissão no nível do menu)
    - Use o gerenciamento de funções para inserir o nome da função definida e o código da função no menu recém-criado
    - Configurar funções e usuários
    - Definir permissões de função para as funções correspondentes no gerenciamento de permissão de função
- Extremidade traseira
    - db.json - Arquivar nova estrutura de armazenamento de artigos
    - services - Adicione postService.js para gravar operações em arquivos db.json
    - controllers - Adicione post.js e introduza postService.js para operações relacionadas
    - main-routes.js - Adicionar roteamento relacionado e usar middleware PermissionCheck para controle de permissão de nível de interface de back-end (código de função ou código de função pode ser usado)
- A parte dianteira
    - service - Adicionar post.js em, configurar operações relacionadas à API, configurar o campo de carregamento para implementar efeitos de carregamento personalizados e configurar o código de função e código de função no campo de permissão (para obter controle de permissão de nível de interface de front-end)
    - Volte para o arquivo post.vue, apresente a API para acessar o arquivo e escreva o código comercial
    - Use o comando v-permission para controlar a exibição dos elementos da página e use a codificação da função e da função (para obter o controle de permissão no nível do elemento)
    - Configure dontCache no módulo de app da loja para controlar se a página é armazenada em cache

Mais detalhes podem ver o código-fonte

## Mostrar resultados

![image](https://raw.githubusercontent.com/wjkang/vue-quasar-admin/master/screenshot/1.jpg)

![image](https://raw.githubusercontent.com/wjkang/vue-quasar-admin/master/screenshot/2.jpg)

![image](https://raw.githubusercontent.com/wjkang/vue-quasar-admin/master/screenshot/3.jpg)

![image](https://raw.githubusercontent.com/wjkang/vue-quasar-admin/master/screenshot/4.jpg)

![image](https://raw.githubusercontent.com/wjkang/vue-quasar-admin/master/screenshot/5.jpg)

![image](https://raw.githubusercontent.com/wjkang/vue-quasar-admin/master/screenshot/6.jpg)

![image](https://raw.githubusercontent.com/wjkang/vue-quasar-admin/master/screenshot/7.jpg)

![image](https://raw.githubusercontent.com/wjkang/vue-quasar-admin/master/screenshot/8.jpg)

![image](https://raw.githubusercontent.com/wjkang/vue-quasar-admin/master/screenshot/9.jpg)

![image](https://raw.githubusercontent.com/wjkang/vue-quasar-admin/master/screenshot/10.jpg)

![image](https://raw.githubusercontent.com/wjkang/vue-quasar-admin/master/screenshot/11.jpg)

![image](https://raw.githubusercontent.com/wjkang/vue-quasar-admin/master/screenshot/12.jpg)

![image](https://raw.githubusercontent.com/wjkang/vue-quasar-admin/master/screenshot/13.jpg)

#### Traduzido do original em Chinês pelo [Google Tradutor](https://translate.google.com).


