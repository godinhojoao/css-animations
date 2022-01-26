#### Em desenvolvimento !

## Repositório que tem como principal foco o estudo das animações css

- Por conta disso vale ressaltar que qualquer tipo de boas práticas css como, por exemplo: BEM CSS, não serão seguidas.
- Além disso a maioria das páginas não serão responsivas.
- A nomeação e a organização das classes, arquivos, etc... Serão feitas da forma que eu julgar mais ágil para o meu estudo de _Animações Css_. Que é o foco do repositório <3.

## Caso você queira utilizar esse repositório para estudar animações css, é importante que tenha um conhecimento prévio de css:

- Acredito que antes de aprendermos animações é importante sabermos:
  - Criar uma estrutura correta de html
  - Propriedades de alinhamento css, espaçamento, unidades de medida, cores, entre outras coisas básicas.
  - Utilizar a arquitetura BEM CSS.
  - Organizar um projeto de forma a facilitar o entendimento de cada pasta e/ou arquivo.

# - Propriedades muito importantes no css para animações:

## `Transform` -> Uma das mais importantes para dar movimento as suas animações

- Diversas vezes iremos combinar esta propriedade com funções, de forma a causar um efeito visual interessante para o usuário.

### Por exemplo:

- `transform: translate(10px, 0);`: Irá transicionar o elemento selecionado 10px a direita e 0px no eixo x. Vale ressaltar que podemos utilizar valores negativos.
- `transform: rotate(45deg);`: Irá rodar em 45 graus a direita o elemento selecionado.
- `transform: scale(1.5);`: Irá aumentar a escala "tamanho geral" do elemento selecionado.
- `transform: skew(0, 365deg);`: Irá contorcer o elemento em 0 graus no eixo x e 365 graus no eixo y.

## `Transition` -> Define transições agradáveis para as suas animações

- Existem várias "ramificações" dessa propriedade e um shortcut chamado apenas `transition`.

### Por exemplo:

- `transition-delay: 1s;`: Tempo que o efeito aplicado irá demorar para começar.
- `transition-duration: 2s;`: Tempo que o efeito aplicado irá durar do começo ao fim.
- `transition-property: width;`: Define a propriedade na qual a transition irá ser aplicada.
- `transition-timing-function: ;`: Define a curva de aceleração, para que então a velocidade da transição possa variar durante sua duração. ( podemos utilizar cubic bezier, que irei comentar depois )
- `transition: margin-right 4s ease-in-out 1s;` : Um "Shortcut / atalho", para as propriedades antes mencionadas. No exemplo utilizamos nessa ordem: /_ property | duration | timing function | delay _/.

## `Animation` -> Com essa propriedade aplicamos animações criadas por nós mesmos.

- Antes de falar sobre a propriedade animation é imporante falar da `keyframes` rule.

### Keyframes

- Utilizamos a "regra" `keyframes` para criar nossas animações personalizadas, existem algumas formas de utilizar o keyframes. Vou citar as que mais utilizo.

- Utilizando com `from` e `to`, sendo o `from` o estado inicial da animação e `to` o estado final. Vale ressaltar que podemos utilizar apenas um dos dois caso seja necessário.

```css
@keyframes slidein {
  from {
    margin-left: 100%;
    width: 300%;
  }

  to {
    margin-left: 0%;
    width: 100%;
  }
}
```

- Utilizando porcentagens, dessa forma temos mais controle com o que irá ocorrer na animação a cada etapa. Poderíamos utilizar varias porcentagens.

```css
@keyframes slidein {
  0% {
    margin-left: 100%;
    width: 300%;
  }
  100% {
    margin-left: 0%;
    width: 100%;
  }
}
```

- É importante dizer que o `!important` faz com que a declaração seja ignorada.

```css
@keyframes important {
  from {
    margin-top: 50px;
  }
  to {
    margin-top: 100px !important; /* ignored */
  }
}
```

### Agora que já sabemos sobre a regra `keyframes`, vamos conhecer a propriedade `animation`

- Utilizamos a propriedade animation para aplicar as animações personalizadas ao elemento que desejarmos.


```css
  h1 {
    animation-name: slidein; /* nome da animação que criamos previamente */
    animation-duration: 1s; /* duração da animação */
    animation-timing-function: ease-in-out; /* curva de aceleração da animação */
    animation-delay: 3s; /* a animação irá começar após 3 segundos */
    animation-iteration-count: infinite; /* quantas vezes a animação irá ocorrer */
    animation-direction: reverse; /* direção da animação ( nesse caso, invertida ) */
    animation-fill-mode: forwards; /* define em qual etapa o elemento deve parar após a animação ser finalizada ( nesse caso, no último frame da animação ) */
    animation-play-state: paused; /* pausa a animação */

    /* shortcut/atalho para as propriedades já comentadas */
    animation: 3s ease-in 1s 2 reverse both paused slidein;
    /*
      animation-duration: 3s;
      animation-timing-function: ease-in;
      animation-delay: 1s:
      animation-iteration-count: 2;
      animation-direction: reverse;
      animation-fill-mode: both;
      animation-play-state: paused;
      animation-name: slidein;
    */
  }
```