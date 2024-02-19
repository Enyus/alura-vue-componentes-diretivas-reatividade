# Curso <img src="./images/icons/alura_logo.png" style="height: 24px"> : Vue 3 - Componentes, Diretivas e Reatividade no Framework
Repositório para guardas as anotações e prática do curso da Alura Vue 3: Entendendo Componentes, Diretivas e Reatividade no Framework

| :placard: Vitrine.Dev |     |
| -------------  | --- |
| :sparkles: Nome        | **Curso Alura : Vue 3 - Componentes, Diretivas e Reatividade no Framework**
| :label: Tecnologias | TypeScript, VueJs
| :rocket: URL         | 

<!-- Inserir imagem com a #vitrinedev ao final do link -->
![](./images/homepage.png#vitrinedev)

## Conteúdos
* [Detalhes do Projeto](#-detalhes-do-projeto)
    * [Iniciando um Projeto Vue](#iniciando-um-projeto-vue)
    * [Extensões úteis do VSCode](#extensões-úteis-do-vscode)
    * [Preparação Inicial](#preparação-inicial)
    * [O básico do Vue](#o-básico-do-vue)
    * [A estrutura de um componente Vue](#a-estrutura-de-um-componente-vue)
    * [Importando componentes dentro de outro componente](#importando-componentes-dentro-de-outro-componente)
* [Para Rodar o Projeto](#-para-rodar-o-projeto)
* [Links](#links)

<a href="#" style="display: block; text-align: right">⬆️Topo⬆️</a>


## 🗈 Detalhes do projeto
Este projeto é o meu primeiro contato com o Framework Vue. Nesta seção tentarei colocar o passo a passo do que foi feito, para usar de referência para projetos futuros em VueJs.


### Iniciando um projeto Vue
1. É necessário ter o __Node__ instalado;
2. Na linha de comando do diretório inicial, usar o comando ```npm create vue```;
3. Como nenhuma versão específica do Vue foi exigida no comando, ele pedirá para confirmar a versão mais recente (no meu caso a @3.9.2).
![Confirmação da versão do Vue](./images/versao-vue.png)
4. Ao confirmar, as perguntas básicas de criação de projeto serão apresentadas:
![Perguntas para criação do projeto](./images/perguntas-vue.png)
5. O projeto será criado na pasta com o nome informado ("Project name", no meu caso, "cookin-up") e serão apresentadas os próximos comandos para abrir o projeto e instalar as dependências iniciais:
![Comandos abrir projeto vue criado](./images/instrucoes-abrir-projeto-vue.png)
```cmd
<!-- No prompt de comando -->
cd cookin-up
npm install
npm run format
npm run dev
```
6. Ao inserir os comandos, um servidor local será criado, na porta __5173__ o app básico será iniciado:
![Página home básica do Vue](./images/home-vue.png)

<a href="#" style="display: block; text-align: right">⬆️Topo⬆️</a>


### Extensões Úteis do VSCode
O instrutor recomenda a instalação das seguintes extensões do VSCode para facilitar o trabalho com o framework Vue:
- Vue Language Features (Volar)
- TypeScript Vue Plugin (Volar)

<a href="#" style="display: block; text-align: right">⬆️Topo⬆️</a>

### Preparação Inicial
Conforme indicado pelo instrutor, alguns arquivos podem ser deletados e/ou alterados, para a criação do app **cookin´up**, então foram tomados os seguintes passos inicias na pasta gerada pelo Vue:
1. Todos os componentes da pasta ```src/components``` foram deletados;
2. Na pasta ```src/assets``` foram deletados os arquivos *base.css* e *logo.svg*, foram colocadas aqui a pasta das imagens que será usada no projeto e o arquivo *main.css* foi alterado de acordo com definições pré-estabelecidas;
3. No arquivo *index.html*, na tag ```<head>```, foi importada as fontes que serão utilizadas (Nunito Sans e Paytone One) e o título da página foi alterado para "Cookin´Up"; aqui também tomei a liberdade de trocar o favicon por um ícone retirado do Figma;
4. No arquivo *App.vue*, que é o componente principal de renderização do framework, o código foi trocado para apenas uma saudação.
5. Como passo opcional o instrutor recomenda ativar o "Modo de Aquisição" (ou "Takeover Mode") da extensão Volar para melhorar o desempenho do Vue com Typescript, que demanda os seguintes passos:
    1. Acionar a paleta de comando com Ctrl + Shift + P;
    2. Digite built e selecione "Extensions: Show Built-in Extensions";
    3. Digite typescript na caixa de pesquisa de extensão (não remova o prefixo @builtin).
    4. Clique no pequeno ícone de engrenagem da "TypeScript and JavaScript Language Features" e selecione "Disable (Workspace)".
    5. Recarregue o VSCode.

<a href="#" style="display: block; text-align: right">⬆️Topo⬆️</a>


### O básico do Vue
Como boa parte dos frameworks de front end, o Vue usa a geração de html dinamicamente através de javascript. Vamos passar pelos arquivos principais para ter uma ideia de como isso é feito:

#### index.html
```html
<!DOCTYPE html>
<html lang="pt-br">
  <head>
    (...)
  </head>
  <body>
    <div id="app"></div>
    <!-- Esta <div> será usada como tag pai de todos os componentes do aplicativo Vue, em especial o componente principal, App.vue, por isso é importante que sua identificação serja alterada com muito cuidado -->
    <script type="module" src="/src/main.ts"></script>
    <!-- Este script indica o arquivo principal do app, o main.ts, que é o responsável por criar/renderizar dinamicamente os componentes em html -->
  </body>
</html>
```

#### main.ts
```ts
import './assets/main.css'

import { createApp } from 'vue'
// O código acima é principalmente a importação dos objetos/funções principais do Vue.
import App from './App.vue'
// Importação do componente principal do vue, o App

createApp(App).mount('#app')
// Aqui está a ação principal do vue, onde o componente App é efetivamente criado como html/css/js e montado na div principal (com o id="app")
```

#### App.vue
```vue
<template>
  <h1>Meu primeiro projeto Vue!</h1>
  <!-- tags html a serem inseridas quando o componente for chamado -->
</template>
```

<a href="#" style="display: block; text-align: right">⬆️Topo⬆️</a>


### A estrutura de um componente Vue
Um componente Vue tem a seguinte aparência:
```vue
<script lang="ts">
    // Código JavaScript ou Typescript, linguagem definida pelo atributo "lang"
    // Aqui aparece a parte lógica do componente, assim como a importação de possíveis outros componentes filhos
</script>

<template>
    <!-- estrutura html do componente-->
</template>

<style scoped>
    /* Estilização do componente */
    /* O atributo "scoped" indica que a estilização afetará apenas este componente, se ele não for declarado, a estilização afetará todos os componentes como uma tag <style> normal */
</style>
``` 
<a href="#" style="display: block; text-align: right">⬆️Topo⬆️</a>


### Importando Componentes dentro de outro Componente
Como vimos acima, o componente raiz ```App``` é adicionado no arquivo ```index.html``` através da função ```createApp(App).mount('#app')``` no arquivo ```App.vue``` na raiz do projeto. Mas para importar um componente dentro de outro componente, uma outra arquitetura é usada:
```vue
<script lang="ts">
import Banner from './components/Banner.vue';
// O componente é importado da pasta componentes

export default {
  components: { Banner: Banner }
}
// É necessário também exportar o componente importado (ainda não sei por quê)
</script>

<template>
  <Banner />
  <!-- Para efetivamente introduzir o componente filho dentro do componente pai, ele é chamado usando uma tag com o nome do componente filho; é convenção nomear componentes em Pascal Case (camel case com primeira letra maiúscula) -->
</template>
``` 

<a href="#" style="display: block; text-align: right">⬆️Topo⬆️</a>


## 📀 Para rodar o projeto
- Clonar o repositório;
- Entrar na pasta __cookin-up__ com ```cd cookin-up```;
- Instalar as dependências necessárias ```npm install```;
- Rode o projeto com o comando ```npm run dev``` e o app estará rodando no servidor local na porta __5173__ (http://localhost:5173/).

<a href="#" style="display: block; text-align: right">⬆️Topo⬆️</a>


## Links
- A parte prática do curso envolve o desenvolvimento de um aplicativo chamado CookinUp. [Este é o arquivo Figma do Projeto](https://www.figma.com/file/J4J2EY9BDJKYueH7QGrsnz/Cookin'UP-%7C-Vue-1-(Copy)?type=design&node-id=1901-2&mode=design&t=odeZYaNpiVTuXDSt-0);
- [Documentação do Vue](https://br.vuejs.org/v2/guide/index.html);
- [Projeto final do instrutor](https://github.com/alura-cursos/cookin-up/tree/main).

<a href="#" style="display: block; text-align: right">⬆️Topo⬆️</a>
