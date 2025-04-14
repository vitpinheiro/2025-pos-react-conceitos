# Notas de aula - React - Conceitos básicos


## Informações gerais
- **Objetivo**: mostrar os conceitos básicos de React
- **Público alvo**: alunos da disciplina de POS (Programação Orientada a Serviços) do curso de Infoweb (Técnico Integrado em Informática para Internet) no CNAT-IFRN (Instituto Federal de Educação, Ciência e Tecnologia do Rio Grande do Norte - Campus Natal-Central)
- **Professor**: [L A Minora](https://github.com/leonardo-minora/)


## Pré-requisitos
1. Conta ativa no Github (todos nossos projetos serão via github)
2. Ter realizado e compreendido a aula/atividade de [criar projeto react](https://github.com/infoweb-pos/2025-pos-react-criar-projeto)



## Sumário

1. Conceitos básicos (introdutórios) do React
2. Prática com os conceitos básicos


### React - Conceitos básicos
by [copilot](https://copilot.microsoft.com/)

#### O que é React?
React é uma biblioteca JavaScript desenvolvida pelo Facebook para criar interfaces de usuário de forma eficiente e declarativa. Ele permite construir componentes reutilizáveis que gerenciam seu próprio estado.

#### Componentes
Componentes são blocos de construção fundamentais em React. Eles podem ser definidos como funções ou classes e retornam elementos React que descrevem o que deve aparecer na tela.

#### JSX
JSX é uma extensão de sintaxe para JavaScript que permite escrever HTML dentro do JavaScript. Ele torna o código mais legível e expressivo.

#### Estado e Props
- **Estado**: O estado é um objeto que representa partes dinâmicas de um componente. Ele pode ser atualizado e React automaticamente re-renderiza o componente quando o estado muda.
- **Props**: Props são argumentos passados para componentes, permitindo que você compartilhe dados entre eles.

#### Hooks
Hooks são funções que permitem usar estado e outros recursos do React em componentes funcionais. O `useState` e `useEffect` são dois dos hooks mais comuns.

#### Ciclo de Vida dos Componentes
Componentes de classe têm métodos de ciclo de vida como `componentDidMount`, `componentDidUpdate`, e `componentWillUnmount`. Em componentes funcionais, você pode usar o hook `useEffect` para lidar com efeitos colaterais.

### Renderização Condicional
React permite renderizar componentes condicionalmente usando operadores ternários ou condicionais simples.

#### Renderização de Listas
Para renderizar listas, você pode usar o método `map` para iterar sobre arrays e retornar elementos React.

#### Eventos
React facilita a manipulação de eventos como cliques, mudanças de formulário, etc., usando manipuladores de eventos.




### Prática com os conceitos básicos

**Passos para praticar**
1. Fork desse repositório para permitir a prática
2. Modificar a linha 8, adicionando nome do aluno e link para o github do aluno.
3. Baixar (`git clone`) para máquina local (lembrar de abrir o vscode na mesma pasta do projeto clonado) ou usar o _codespaces_ para "codar"
4. Rodar a aplicação com `npm run dev`
5. Abrir o navegador e visualizar a aplicação enquanto modifica

**Práticas**
1. Instalar bibliotecas executando o comando `npm i`
2. Escrevendo Markup com JSX
3. Criar e aninhar componentes react
4. Adicionando Estilos
5. 



### 2. Escrevendo Markup com JSX
JSX permite escrever HTML dentro do JavaScript. Aqui está um exemplo simples:

```jsx
const Elemento = <h1>Olá, mundo!</h1>;

```



#### 3. Criar e aninhar componentes
Para criar componentes em Next.js, você pode usar funções ou classes. Abaixo está um exemplo de como criar e aninhar componentes.

Lembrando que o arquivo abaixo é `src/app/page.tsx`.

```jsx
"use client";

function Titulo(props) {
  return <h1>React - conceitos básicos</h1>;
}

const Saudacao = ({ nome }) => {
  return <h2>Olá, {nome}!</h2>;
}

const Home = () => {
  return (
    <div>
			<main>
				<Titulo />
        <Saudacao nome="Professor" />
        <Saudacao nome="Alunos" />
			</main>
    </div>
  );
}

```

Como estamos usando _typescript_, e se o _eslint_ estiver ativo no _vscode_, deverá reclamar de tipagem com a variável `nome`.
Abaixo segue a "correção" declarando o tipo e especificando nos componentes o tipo.

```jsx
// src/app/page.tsx
"use client";

import React, { Component } from 'react';


interface SaudacaoProps {
    nome: string;
  }
  
function Titulo(props) {
  return <h1>React - conceitos básicos</h1>;
}

const Saudacao: React.FC<SaudacaoProps> = ({nome}) => {
  return <h2>Olá, {nome}!</h2>;
}

class SaudacaoComClass extends React.Component<SaudacaoProps> {
  render() {
    const { nome } = this.props;
    return <h2>Olá, {nome}!</h2>;
  }
}

const Home = () => {
	return (
		<div>
			<main>
				<Titulo />
        <Saudacao nome="Minora" />
        <Saudacao nome="Alunos" />
        <SaudacaoComClass nome="professor e alunos" />
			</main>
		</div>
	);
}

export default Home;

```


### 4. Adicionando Estilos
Você pode adicionar estilos usando CSS modules ou styled-jsx. Aqui está um exemplo com CSS modules:

```css
/* src/app/globals.css */
.titulo {
  color: blue;
}

```

```jsx
// src/app/page.tsx
"use client";

const Home = () => {
  return <h1 className="titulo">Olá, mundo!</h1>;
}

export default Home;

```

### 4. Exibindo Dados
Para exibir dados, você pode usar props e estado. Aqui está um exemplo:

```jsx
// src/app/page.tsx
"use client";

const Home = () => {
  const dados = ["React", "Next.js", "JavaScript"];

  return (
    <ul>
      {dados.map((item, index) => (
        <li key={index}>{item}</li>
      ))}
    </ul>
  );
}

export default Home;

```

### 5. Renderização Condicional
Você pode renderizar componentes condicionalmente usando operadores ternários ou condicionais simples:

```jsx
// src/app/page.tsx
"use client";

const Home = () => {
  const estaLogado = true;

  return (
    <div>
      {estaLogado ? <h1>Bem-vindo de volta!</h1> : <h1>Por favor, faça login.</h1>}
    </div>
  );
}

export default Home;

```

### 6. Renderizando Listas
Para renderizar listas, você pode usar o método `map`:

```jsx
// src/app/page.tsx
"use client";

const Home = () => {
  const itens = ["Item 1", "Item 2", "Item 3"];

  return (
    <ul>
      {itens.map((item, index) => (
        <li key={index}>{item}</li>
      ))}
    </ul>
  );
}

export default Home;

```

### 7. Respondendo a Eventos
Para responder a eventos, você pode usar manipuladores de eventos:

```jsx
// src/app/page.tsx
"use client";

import { useState } from 'react';

const Home = () => {
  const [contagem, setContagem] = useState(0);

  return (
    <div>
      <p>Você clicou {contagem} vezes</p>
      <button onClick={() => setContagem(contagem + 1)}>Clique aqui</button>
    </div>
  );
}

export default Home;

```

### 8. Atualizando a Tela
Para atualizar a tela, você pode usar o estado e hooks como `useEffect`:

```jsx
// src/app/page.tsx
"use client";

import { useState, useEffect } from 'react';

const Home = () => {
  const [dados, setDados] = useState([]);

  useEffect(() => {
    fetch('/api/dados')
      .then(response => response.json())
      .then(data => setDados(data));
  }, []);

  return (
    <ul>
      {dados.map((item, index) => (
        <li key={index}>{item}</li>
      ))}
    </ul>
  );
}

export default Home;

```

### 9. Compartilhando Dados Entre Componentes
Para compartilhar dados entre componentes, você pode usar props ou contextos:

```jsx
// src/app/page.tsx
"use client";

import { useState } from 'react';

function Contador() {
  const [contagem, setContagem] = useState(0);

  return (
    <div>
      <p>Você clicou {contagem} vezes</p>
      <button onClick={() => setContagem(contagem + 1)}>Clique aqui</button>
    </div>
  );
}

const Home = () => {
  return (
    <div>
      <Contador />
    </div>
  );
}

export default Home;

```
