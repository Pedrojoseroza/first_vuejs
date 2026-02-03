# **Anotações básicas sobre o [vue.js](https://vuejs.org/)** 

## Aula 01: 

  Instalação do vue pode ser feita diretamente por linha de comando no diretório desejado: 
  ```
  npm create vue@latest
  ```
  É recomendado a instalação do [docker](https://docker.com) para instalação do banco de dados também.

## Aula 02: Base e deploy 

- Os componentes de arquivo único (Single-file Components) são uma forma de definir componentes no VueJs. São componentes que são definidos em um único arquivo (arquivos .vue), encapsulando os componentes  lógicos (JavaScript), de template (HTML) e de estilos (CSS).  
  O arquivo App.vue (já vem na própria instalação do pacote), é um exemplo de componente de arquivo único. Como explicado anteriormente, um componente VueJS tem três partes: lógica, template e estilos  
- A parte lógica dos componentes, escrita em JavaScript ou TypeScript pode ser desenvolvida usando **API de opções ou API de composição**. Estudaremos essas duas formas na próxima etapa.  
  Na parte de template o Vue usa uma sintaxe baseada em HTML, que permite a utilização de diretivas e expressões. As **diretivas** são instruções especiais que são adicionadas ao template para alterar o comportamento da renderização. As expressões são trechos de código que são avaliados e renderizados como texto.  
- Durante o desenvolvimento, a aplicação é executada localmente, no computador do desenvolvedor. Para que a aplicação possa ser acessada por outros usuários, ela precisa ser publicada em um servidor.  
  Duas etapas são necessárias para publicar uma aplicação VueJs:  
- **Compilação da aplicação**  
- **Publicação da aplicação**

### **Compilação da Aplicação:** 

A compilação da aplicação pode ser feita pelo comando: 

npm run build

Esse comando gera uma pasta dist com os arquivos estáticos da aplicação. Esses arquivos são os que serão publicados no servidor.

Além disso, esses arquivos são otimizados para serem servidos em produção. Por exemplo, os arquivos CSS e JS são minificados, e os arquivos de imagem são otimizados.

### **Publicação da Aplicação:**

A publicação da aplicação é feita copiando os arquivos da pasta dist para o servidor web. Essa etapa pode ser feita de diversas formas, dependendo do servidor web utilizado. Por exemplo, você pode instalar um servidor Web usando o Nginx ou o Apache, ou você pode utilizar um serviço de hospedagem de sites. Neste curso, usaremos o [Surge](https://surge.sh/), por isso usaremos o seguinte comando:   
**npm install \-g surge**

**surge**

## Aula 03: Sintaxe

O VueJs permite a criação de templates HTML que são renderizados dinamicamente com base nos dados da aplicação. Essa renderização é feita de forma declarativa, ou seja, o desenvolvedor declara o que deve ser renderizado, e não como deve ser renderizado. Isso permite que o VueJs faça o trabalho de atualizar a interface do usuário de forma eficiente. Todas as templates são sintaticamente válidas no HTML, e podem ser usadas em qualquer lugar que aceite HTML.

### **Interpolação de texto:** 

A interpolação de texto, interpola HTML e JS, é a forma mais básica de renderização de dados. Ela permite a renderização de dados em texto simples. Para isso, basta usar a sintaxe *{{Variável}}*. Também conhecido como **mustache**.

### **HTML puro:** 

O padrão de interpolação de texto não é adequado para renderizar HTML puro. Para isso, o VueJs oferece a diretiva **v-html**. Que, basicamente, faz o HTML ser interpretado como HTML, tipo tags, ao invés de diretamente texto, o que ocorre sem **v-html**.  
```HTML
<script setup>  
  const rawHtml = '<span style="color: red">Este é um texto em vermelho</span>';  
</script>  
<template>  
  <p>Usando interpolação de textos: {{rawHtml}}</p>  
  <p>Usando v-html: <span v-html="rawHtml"></span></p>  
</template>
```

Nota: No VueJS, o atributo v-html é chamado de diretiva. Diretivas são atributos especiais que começam com v- e que são usados para modificar o comportamento de um elemento. Diretivas são usadas para renderizar dados, modificar o comportamento de um elemento, ou modificar o comportamento de um elemento de acordo com o estado da aplicação.

### **Expressões JavaScript:** 

Expressões simples, como operadores ternários, operadores aritméticos, podem ser feitos diretamente no *{{Mustache}},* e até algumas funções simples, .join(), .reverse().  
Porém, não é possível fazer controles de fluxos dentro do mustache, como if ou loops, for, while. Essas operações mais simples podem ser feitas em: 

* Interpolação de texto  
* Em qualquer diretiva Vue (atributos que começam com v-)

Não podemos esquecer que podemos chamar qualquer tipo de função, declarada no script, dentro do mustache, passando parâmetro ou não.

### 	**Diretivas:** 

As diretivas são atributos especiais que começam com v-. Elas são usadas para modificar o comportamento de um elemento ou componente.
Exemplos de diretivas e suas respectivas funções: 
- **v-if / v-else-if / v-else:** Usadas para renderização condicional de elementos. Se a expressão for verdadeira, o elemento é inserido no DOM; caso contrário, é removido.
- **v-show:** Alterna a visibilidade de um elemento com base em uma condição, usando a propriedade CSS display (o elemento permanece no DOM).
- **v-for:** Utilizada para renderização de listas, iterando sobre um array ou objeto para criar múltiplos elementos HTML.
- **v-bind:** Permite a ligação dinâmica de atributos HTML (como src, href, class, style) a dados reativos na instância Vue. Possui a abreviação :.
- **v-on:** Anexa ouvintes de eventos (como click, input, submit) aos elementos DOM, executando métodos definidos no componente. Possui a abreviação @.
- **v-model:** Cria uma ligação de dados bidirecional em elementos de formulário (input, select, textarea), sincronizando automaticamente o valor do input com o estado da aplicação.
- **v-text:** Atualiza o conteúdo de texto do elemento. É semelhante à interpolação {{ ... }}.
- **v-html:** Renderiza HTML bruto dentro do elemento, o que pode ser útil, mas deve ser usado com cautela para evitar ataques XSS(Cross-Site Scripting, vulnerabilidades em sites que permitem a invasores injetar scripts maliciosos).
- **v-once:** Renderiza o elemento e seu conteúdo apenas uma vez, e as atualizações de dados subsequentes não afetarão mais esse elemento.
- **v-cloak:** Oculta elementos não compilados até que a instância Vue esteja pronta, prevenindo a exibição de mustache tags brutas durante o carregamento inicial.

### 	**Parâmetros ou argumentos:**

Algumas diretivas permitem que sejam passados parâmetros ou argumentos. Por exemplo, a diretiva **v-bind** (vincular em português) é usada para associar um atributo de um elemento a uma expressão. O valor do atributo é atualizado sempre que a expressão for atualizada. Por exemplo, o atributo **href** dentro de uma tag **a (\<a v-bind:href=”var”\>**asdsads**\</a\>).** Podemos abreviar a o v-bind, substituindo apenas por “**:**”.  
Outro exemplo de diretiva que permite parâmetros é a diretiva **v-on**. Essa diretiva é usada para associar um evento de um elemento a uma expressão. Como um click ou um hover. A diretiva v-on pode ser usada de forma abreviada, usando apenas o prefixo **@**.

### **Argumentos dinâmicos:** 

Algumas diretivas permitem que sejam passados argumentos 	dinâmicos, isto é, argumentos que podem estar associados a variáveis, podendo assim variar o atributo HTML passado como variável, por exemplo, em um v-on, variar o tipo de evento associado, a esta condição. Por exemplo:
``` HTML
<script setup>  
  const nomeEvento = 'click';  
  function mostrarAlerta {  
    alert('Botão clicado!');  
  };  
</script>  
                   
<template>  
  <button v-on:[nomeEvento]="mostrarAlerta">Clique aqui</button>  
</template>

```

### 	**Modificadores:** 

  Modificador é um sufixo especial, denotado por um ponto (.), adicionado às diretivas (v-on ou v-model) para modificar seu comportamento padrão. Por exemplo:   
```HTML
<template>  
  <form v-on:submit.prevent="mostrarAlerta">...</form>  
</template>
```
Nesse exemplo, a função mostrarAlerta é executada sempre que o formulário for submetido. Contudo, o modificador **.prevent** informa ao Vue para chamar o método event.preventDefault() que dependendo do evento em questão, parará seu comportamento padrão, um exemplo é em formulários, evitando que o formulário seja submetido quando a página é reiniciada.

## Aula 04: Reatividade: 

Uma das características mais importantes do VueJS é a reatividade, que define que quando o estado de um objeto é alterado, os objetos que dependem desse estado são atualizados automaticamente.   
De outra forma, podemos dizer que a reatividade, no VueJS, é a forma de criar variáveis que, quando alteradas, o seu valor é atualizado automaticamente na interface do usuário, e vice-versa.

### **Declarando variáveis reativas:** 
	
  Podemos declarar variáveis reativas no vue de duas formas, com **reactive** ou **ref**.
  - **Usando ref:**
    A função ref recebe um valor como parâmetro, um valor inicial dependependo da situação, e retorna um obejto que possui uma propriedade **value** que contém o valor passado como parâmetro. Para alterar o valor da variável é preciso acessar a propriedade value.
    Exemplos de uso da função ref:   
    - const nome = ref('João'); // string
    - const idade = ref(30); // number
    - const preco = ref(10.5); // number
    - const ativo = ref(true); // boolean
    - const frutas = ref(['maçã', 'banana']); // array de strings
  - **Usando reactive:**
    Mas, para declarar objetos, o uso do reactive é mais recomendado, pois assim não é necessário acessar a propriedade value.

### **Popriedades Computadas:**
  As propriedades são funções que são executadas automaticamente sempre que uma de suas dependências é alterada, como uma variável reativa. Elas são são declaradas usando a função **computed** do VueJS. A sua sintaxe é semelhante ao de um método (função):
  
  `const variavel = computed(() => {
  return AlgumaCoisa})`
  
  A vantagem das propriedades computadas sobre funções comuns é que elas são atualizadas somente quando algumas de suas depedências é atualizadas, diferente das funções que executam sempre que chamadas, o que pode ocorrer sempre que a tela do usuário for renderizada, por exemplo, supondo que exista uma propriedade computada atrelada ao tamanho de um certo array, se outro certo array sofresse alteração e fosse necessário re-renderizar a tela do usuário, se fosse um metódo comum no lugar da propriedade computada, ela seria chamada novamente, sem precisão, causando um impacto negativo na aplicação. 

  ## Aula 05: Renderização:

  É comum em aplicações web se utilizar de listas para diversas funções, geralmente com os dados retirados de um servidor. Existem vários tipos de listas, mas que sempre estão dispostas de duas formas. Ou em Arrays, em que os dados são indexados por números, indices. Ou em Objetos, em que os elementos são indexados por chaves, palavras-chaves.

  ### Renderização dos elementos de uma lista
  Para iterar sobre todos os itens de uma lista, como no javascript, utilizamos um loop, mas neste caso, uma diretiva, **v-for**, sendo sua sintaxe semelhante ao um loop for, `v-for="item in lista_De_Itens":key = "index"`. A propriedade key é usada pelo VueJS para identificar cada item da lista e é obrigatória quando usamos a diretiva v-for. Sem a propriedade key, o VueJS não consegue identificar cada item da lista e não consegue atualizar corretamente a lista quando os dados são alterados.
  É importante ressaltar também que a diretiva pode ser utilizada para renderizar o elemento em qualquer tag HTML adequada, não só em <\li>, mas também em <\p> ou <\div>.
  ### Renderização de um array de objetos
  Diferente de um array simples, no array de objetos, podemos escolher outra chave para utilizarmos com key, pode ser indexado por mais de apenas um número. Considere o seguinte array: 
  ```javascript
     const items = [
       { id: 1, name: 'Item 1' },
    { id: 2, name: 'Item 2' },
    { id: 3, name: 'Item 3' },
  ];
  ```
  Para iterar sobre este array, podemos usar a seguinte diretiva: 
  ```HTML
   <ul>
     <li v-for="item in items" :key="item.id">
       {{ item.name }}
    </li>
  </ul>
  ```
  A grande diferença é que não precisamos usar o índice do item como identificador.
  ### Renderização de objetos 
  Para renderizar um objeto, de forma, completa, precisamos de dois parâmetros, sendo o valor e a chave para acessar o valor, de forma que podemos renderiza-lo completamente. A diferença é que a :key neste caso, pode ser a propria chave do valor dentro do objeto.

  `v-for="(value, key) in items" :key="key"`

  ### Renderização de objetos com objetos aninhados
  
  De forma resumida, podemos ter duas abordagens: 
  - Especificar a chave do valor a ser acessado dentro do array, de forma a usar a sintaxe `item.object.description`
  - Iterar novamente, isto é, usar outra diretiva como v-for, para percorrer o objeto dentro do objeto que está no array que está sendo percorrido, como uma boneca Russa.

  ### Adicionando elementos a uma lista
  Para adicionar elementos ao final de uma lista basta usar a função **push**. Considere o exemplo abaixo: 
  ```javascript
  <script setup>
  import { ref } from 'vue'

  const novaCor = ref('')
  const listaCores = ref(['branco', 'amarelo', 'preto'])
  
  function adicionarCor {
    listaCores.value.push(novaCor.value)
    novaCor.value = ''
  }
</script>
<template>
  <p>
    Adicione sua cor favorita à lista: 
  </p>
  <input type="text" v-model="novaCor">
  <button @click="adicionarCor">Adicionar</button>
  <ul>
    <li v-for="cor in listaCores">{{ cor }}</li>
  </ul>
</template>
```

### Removendo elementos
  Para remover elementos basta usar a função splice, que recebe dois parâmetros, o índice do elementos a ser retirado e a quantidade de elementos a ser retirado a partir daquele índice, 1,2,3,etc.

### Atualizando elementos
  Para atualizar um elemento de uma lista, basta atribuir um novo valor ao elemento.

  ## Aula 06: Componentes
  Componentes instâncias reutilizáveis de VueJS que podem ser criadas e utilizadas em qualquer parte da aplicação. Isto é, são como pedaços de códigos de podem ser reutilizado em diversas partes, simplificando assim a escrita e manutenção do código. Eles permitem dividir a tela do usuário em partes menores de forma a facilitar a utilização e evolução da aplicação.

  No VueJS, em geral, usamos o conceito de SFC (Single File Component) para criar componentes. Um SFC é um arquivo que contém o template, a lógica e o estilo de um componente em um único lugar.

  ### Criação do componente
  Para criar um componente Vue é bastante simples, da mesma forma que criamos um arquivo .HTML, basta decidir o nome do componente e aplicar .vue ao final desse nome. Isto criará um componente do modelo SFC.
  Lembrando que componentes Vue devem sempre ser criadas dentro da pasta source (src), de preferências em outras pastas organizadas conforme sua utilidade. 

  ### Registro e uso do componente
  Para usar um outro componente em alguma aplicação, basta importá-la e usa como uma tag no esqueleto HTML,isso pode ser feito por exemplo na aplicação App.vue, padrão do framework, seguindo a sintaxe: 
  ```HTML
  <script>
    import component from "/src/components/component" 
  </script>
  <template>
    <component/>
  </template>
  <style>
  </style>
  ```

  ### Registro Global de componentes 
  Note que de acordo com a sintaxe e o exemplo anterior, para usar um componente em uma aplicação, é preciso sempre importá-la, de forma que não podemos usar esse componente globalmente. Para fazer o registro de um componente qualquer, permitindo que ele seja usado de forma global em toda a aplicação, basta usar o seguinte código no arquivo **src/main.js**: 
  ``` javascript
  import { createApp } from 'vue';
  import App from './App.vue';
  import componente from './components/componente.vue';

  const app = createApp(App);
  app.component('componente', componente);
  app.mount('#app');
  ```

  ### Propriedades dos componentes 
  Ao criar um componente, é possível passar propriedades para ele. As propriedades são valores que podem ser utilizados pelo componente para alterar seu comportamento ou sua aparência. As propriedades são passadas para o componente como atributos HTML e são acessadas pelo componente como variáveis JavaScript.
  
  A adição de propriedades para um componente é feita pelo método: 
  ``` javascript
  import {defineProps} from 'vue'
  defineProps(["prop"])
   ```
   O método defineProps recebe um array de strings com os nomes das propriedades que o componente deve receber.
   
   #### Outros recursos de propriedades: 
   É possível definir valores específicos para as propriedades que serão passadas para um componente, podendo limitar erros e maus funcionamentos da aplicação, veja o exemplo: 
   ``` HTML
  <script setup>
  import { defineProps } from 'vue';

  defineProps({
    prop: {
      type: String,
      required: true,
    },
    numeroDaApli: {
      type: Number,
      default: '0',
    },
  })
  </script>
   ```
  Acima estamos definindo  os tipos das duas propriedades que devem ser passadas ao usar o componente, a propriedade "prop" e "numeroDaApli", string e number, respectivamente. Além disso, estamos definindo a propriedade `prop` como obrigatório, pois sempre que o componente for usado deve ter esta propriedade passada obrigatoriamente (`required`), por último, o valor da propriedade `numeroDaApli` tem como valor padrão igual à 0 (`default`).

  #### Tipos Permitidos para as propriedades: 
  - String: Texto.
  - Number: Números.
  - Boolean: Verdadeiro/Falso.
  - Array: Arrays.
  - Object: Objetos.
  - Date: Objetos de data.
  - Function: Funções (geralmente usado para callbacks).
  - Symbol: Símbolos.
  - Error: Objetos de erro

  ### Outras formas de envio de valores para as propriedades
  É possível passar valores dinâmicamente para propriedades por meio de varíavel, isto é, que podem mudar conforme o necessidade e ação do usuário, isso é possível com o auxilio da diretiva `v-bind`, veja o exemplo:
  ```HTML
  <script setup>
  import component from './components/component.vue';

  const prop = 'Qualquer coisa';
  const numeroDaApli = 2;
</script>

<template>
  <div>
    <expand-box :prop="prop" :numeroDaApli="numeroDaApli" />
  </div>
</template>
  ```

Além disso, é possível passar um objeto que possua como propriedades internas, os mesmos nomes de que as propriedades do componente, usando também o v-bind.

### Slots 
A tag `<slot>` é usada para passar conteúdo para aplicação de forma diferente das propriedades de forma que possamos passar conteúdo para o componente através de onde estamos utilizando, todo o conteúdo presente dentro das tags do componente, normalmente usada no `App.vue`, serão exibidas dentro da tag slot, não sendo necessária colocar nada nela na aplicação em que ela consta.

Caso seja necessário, podemos definir um valor padrão para o que está dentro slot, caso não seja passado nenhum valor, o que já está dentro da tag slot seja exibida, podendo ser uma outra tag como um `<p>`.

 Quando temos mais de uma tag slot no componente, podemos nomea-las, de forma à controlar melhor o código a ser exibido, para isso, usamos a tag template quando for exibida, veja o exemplo: 

```HTML
<script setup>
  import componente from './src/componentes/componente'
  </script>

<template>
  <componente>
    <template #primeiro_slot>
      Um nome, qualquer coisa
      </template>
      <template #segundo_slot>
        Um sobrenome, um número por exemplo
        </template>
    </componente>
</template>
```

Além disso é possível criar slot condicionais, sendo só exibidos quando um certa condição é verdadeira, por exemplo, quando algum conteúdo é passado para eles.

### Eventos
A manipulação de eventos é uma parte importante da programação de interfaces de usuário. No Vue.js, os componentes filhos podem emitir eventos que são capturados pelos componentes pais. Para isso, é necessário utilizar a diretiva `v-on` no componente pai e o método `$emit` no componente filho. A sintaxe do $emit é: 

`emit('nome-do-evento', dados)`.

