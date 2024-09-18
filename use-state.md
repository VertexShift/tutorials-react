# Como Usar o useState no React

Neste tutorial, vamos explorar como usar o hook `useState` no React para gerenciar estados dentro de componentes funcionais. O `useState` é um dos hooks mais usados no React e permite que você adicione estados a componentes que anteriormente eram stateless.

## 1. O que é o useState?

O `useState` é um hook que permite que você adicione e manipule estados em componentes funcionais. Ele retorna um array contendo dois elementos:

1. O valor do estado atual.
2. Uma função que permite atualizar esse estado.

### Sintaxe:

```javascript
const [state, setState] = useState(initialValue);
```

- `state`: O valor atual do estado.
- `setState`: A função para atualizar o valor do estado.
- `initialValue`: O valor inicial do estado.

## 2. Exemplo Simples: Contador

Vamos criar um contador simples que aumenta o valor ao clicar em um botão.

### Exemplo de código:

```javascript
import React, { useState } from 'react';

function Counter() {
  // Declarando o estado 'count' com valor inicial de 0
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Você clicou {count} vezes</p>
      <button onClick={() => setCount(count + 1)}>
        Clique aqui
      </button>
    </div>
  );
}

export default Counter;
```

### Explicação:

- `useState(0)`: Inicia o estado `count` com o valor 0.
- `setCount(count + 1)`: Atualiza o estado `count`, incrementando o valor atual em 1.

## 3. Trabalhando com Strings

Além de números, o `useState` pode ser usado para manipular strings. Vamos criar um campo de entrada (input) onde o texto digitado é exibido em tempo real.

### Exemplo de código:

```javascript
import React, { useState } from 'react';

function TextInput() {
  const [text, setText] = useState('');

  return (
    <div>
      <input 
        type="text" 
        value={text} 
        onChange={(e) => setText(e.target.value)} 
        placeholder="Digite algo..." 
      />
      <p>Você digitou: {text}</p>
    </div>
  );
}

export default TextInput;
```

### Explicação:

- `useState('')`: Inicia o estado `text` com uma string vazia.
- `setText(e.target.value)`: Atualiza o estado `text` com o valor digitado no campo de entrada.

## 4. Trabalhando com Objetos

O `useState` também pode ser usado para armazenar objetos. Neste exemplo, vamos criar um formulário simples que armazena o nome e a idade de um usuário.

### Exemplo de código:

```javascript
import React, { useState } from 'react';

function UserForm() {
  const [user, setUser] = useState({ name: '', age: '' });

  const handleInputChange = (e) => {
    const { name, value } = e.target;
    setUser({
      ...user,
      [name]: value,
    });
  };

  return (
    <div>
      <input
        type="text"
        name="name"
        value={user.name}
        onChange={handleInputChange}
        placeholder="Nome"
      />
      <input
        type="text"
        name="age"
        value={user.age}
        onChange={handleInputChange}
        placeholder="Idade"
      />
      <p>Nome: {user.name}</p>
      <p>Idade: {user.age}</p>
    </div>
  );
}

export default UserForm;
```

### Explicação:

- `useState({ name: '', age: '' })`: Inicia o estado `user` com um objeto contendo as propriedades `name` e `age`.
- `setUser({ ...user, [name]: value })`: Atualiza apenas a propriedade que foi modificada, sem sobrescrever o restante do objeto.

## 5. Atualizando Estado com Funções

Às vezes, ao atualizar um estado baseado no valor anterior, é mais seguro usar uma função de atualização. Aqui está um exemplo que incrementa e decrementa o valor de um contador de forma segura.

### Exemplo de código:

```javascript
import React, { useState } from 'react';

function SafeCounter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Contador: {count}</p>
      <button onClick={() => setCount(prevCount => prevCount + 1)}>
        Incrementar
      </button>
      <button onClick={() => setCount(prevCount => prevCount - 1)}>
        Decrementar
      </button>
    </div>
  );
}

export default SafeCounter;
```

### Explicação:

- `setCount(prevCount => prevCount + 1)`: Usa a versão anterior do estado `prevCount` para garantir que o valor seja atualizado corretamente, especialmente em casos onde múltiplas atualizações são feitas rapidamente.

## 6. Conclusão

Neste tutorial, você aprendeu o básico do hook `useState` no React. O `useState` é uma ferramenta poderosa para gerenciar estados dentro de componentes funcionais, sendo essencial para a criação de interfaces interativas. Lembre-se de que o `useState` pode lidar com qualquer tipo de valor, como números, strings, arrays, e objetos.

