# Notas de aula - React - Conceitos básicos

## Informações gerais
- **Objetivo**: mostrar os conceitos básicos de React
- **Público alvo**: alunos da disciplina de POS (Programação Orientada a Serviços) do curso de Infoweb (Técnico Integrado em Informática para Internet) no CNAT-IFRN (Instituto Federal de Educação, Ciência e Tecnologia do Rio Grande do Norte - Campus Natal-Central)
- **Professor**: [L A Minora](https://github.com/leonardo-minora/)
- **Aluno**: FIXME


## Pré-requisitos
1. Conta ativa no Github (todos nossos projetos serão via github)
2. Ter realizado e compreendido a aula/atividade de [criar projeto react](https://github.com/infoweb-pos/2025-pos-react-criar-projeto)



## Sumário

1. Conceitos básicos (introdutórios) do React
2. Prática com os conceitos básicos


### 1. React - Conceitos básicos
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




### 2. Prática com os conceitos básicos

**Passos para praticar**
1. _Fork_ desse repositório para permitir a prática
2. Modificar a linha 7, colocando o nome do aluno e o link para o github também do aluno.
3. Baixar (`git clone`) para máquina local (lembrar de abrir o vscode na mesma pasta do projeto clonado) ou usar o _codespaces_ para "codar"
4. Lembrar de instalar as bibliotecas com `npm i`
5. Rodar a aplicação com `npm run dev`
6. Abrir o navegador e visualizar a aplicação enquanto modifica

**Práticas**
1. Escrevendo Markup com JSX
2. Criar e aninhar componentes react
3. Adicionando Estilos
4. 

**Observação** as práticas serão modificando os arquivos `src/app/page.tsx` e `src/app/globals.css`.

### Prática 1. Escrevendo Markup com JSX
JSX é a sintaxe baseada na linguagem de marcação HTML para descrever um componente, ou parte dele, em React.
JSX é mais rigoroso que os navegadores são com arquivos HTML, como abrir e fechar marcações na sequência correta, uso de propriedades, entre outras coisas.
O JSX para descrever um componente deve:
- ter somente 1 marcação pai, que pode conter vários filhos, netos, etc.
- quando for usar mais de 1 linha, sempre envolver a marcação pai com parenteses.
- caso não tenha uma marcação pai de fato, pode usar a marcação vazia `<> ... </>`.

```jsx
// src/app/page.tsx
"use client";

const Titulo = () => <h1>React - Conceitos básicos</h1>;

const SubTitulo = () => (<h2>Lista de tarefas</h2>);

const Cabecalho = () => (
  <>
    <Titulo />
    <SubTitulo />
  </>
);

const Home = () => {
  return <Cabecalho />;
}

export default Home;

```



#### 2. Criar e aninhar componentes
Para criar componentes em React, você pode usar funções ou classes.
Abaixo está um exemplo de como criar e aninhar componentes.

Lembrando que o arquivo abaixo é `src/app/page.tsx`.

```jsx
// src/app/page.tsx
"use client";

import React from "react";

const Titulo = () => <h1>React - Conceitos básicos</h1>;

const SubTitulo = () => <h2>Lista de tarefas</h2>;

function Cabecalho() {
	return (
		<>
			<Titulo />
			<SubTitulo />
		</>
	);
}

class Tarefa extends React.Component {
	render(): React.ReactNode {
		return (
			<div>
				<h3>Codar e codar durante 2025</h3>
				<p>Pendente</p>
			</div>
		);
	}
}
const Home = () => {
	return (
		<>
			<Cabecalho />
			<Tarefa />
		</>
	);
};

export default Home;

```



### 4. Adicionando Estilos
Você pode adicionar estilos usando CSS modules ou styled-jsx, ou ainda usando Styled Components.
Abaixo está um exemplo com CSS adicionado classe `titulo` ao código padrão (linhas 1-26) dos projetos React com NextJS.

Lembrando que iremos usar o `tailwind` em sala de aula e como tal o exemplo do código React será usando o framework.

```css
/* src/app/globals.css */
@import "tailwindcss";

:root {
	--background: #ffffff;
	--foreground: #171717;
}

@theme inline {
	--color-background: var(--background);
	--color-foreground: var(--foreground);
	--font-sans: var(--font-geist-sans);
	--font-mono: var(--font-geist-mono);
}

@media (prefers-color-scheme: dark) {
	:root {
		--background: #0a0a0a;
		--foreground: #ededed;
	}
}

body {
	background: var(--background);
	color: var(--foreground);
	font-family: Arial, Helvetica, sans-serif;
}

.titulo {
	color: blue;
}

```

```jsx
// src/app/page.tsx
"use client";

import React from "react";

const Titulo = () => <h1 className="text-2xl font-bold mb-1">React - Conceitos básicos</h1>;

const SubTitulo = () => <h2 className="text-4xl font-bold mb-6">Lista de tarefas</h2>;

function Cabecalho() {
	return (
		<div className="text-center">
			<Titulo />
			<SubTitulo />
		</div>
	);
}

class Tarefa extends React.Component {
	render(): React.ReactNode {
		return (
			<div className="p-3 mb-3 rounded-lg shadow-md bg-gray-400">
				<h3 className="text-xl font-bold">Codar e codar durante 2025</h3>
				<p className="text-sm">Pendente</p>
			</div>
		);
	}
}

const Home = () => {
	return (
		<div className="container mx-auto p-4">
			<Cabecalho />
			<Tarefa />
		</div>
	);
};

export default Home;

```

### 4. Exibindo Dados
Para exibir dados, você pode usar `props` e estado.
Abaixo está um exemplo usando valores em `props`.

```jsx
// src/app/page.tsx
"use client";

import React from "react";

const Titulo = () => (
	<h1 className="text-2xl font-bold mb-1">React - Conceitos básicos</h1>
);

const SubTitulo = () => (
	<h2 className="text-4xl font-bold mb-6">Lista de tarefas</h2>
);

function Cabecalho() {
	return (
		<div className="text-center">
			<Titulo />
			<SubTitulo />
		</div>
	);
}

class Tarefa extends React.Component {
	render(): React.ReactNode {
		return (
			<div className="p-3 mb-3 rounded-lg shadow-md bg-gray-400">
				<h3 className="text-xl font-bold">{this.props.titulo}</h3>
				<p className="text-sm">Pendente</p>
			</div>
		);
	}
}

const Home = () => {
	const tarefas = [
		{ id: 1, title: "delectus aut autem", completed: false },
		{ id: 2, title: "quis ut nam facilis et officia qui", completed: true },
		{ id: 3, title: "fugiat veniam minus", completed: false },
	];

	return (
		<div className="container mx-auto p-4">
			<Cabecalho />
			<Tarefa titulo={tarefas[0].title} />
			<Tarefa titulo={tarefas[1].title} />
		</div>
	);
};

export default Home;

```

Talvez apareça um sublinhado vermelho nos códigos `<Tarefa titulo=... />` porque o editor de código não consegue inferir o tipo, sim _typescript_ é tipado.

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
