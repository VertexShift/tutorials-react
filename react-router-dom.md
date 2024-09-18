# Como Usar o React Router DOM

Neste tutorial, vamos aprender como configurar e usar o `react-router-dom` para adicionar navegação ao seu aplicativo React. O `react-router-dom` permite que você gerencie rotas, crie links entre páginas e faça o controle de navegação de forma simples.

## 1. Instalação do React Router DOM

Primeiro, instale o pacote `react-router-dom`:

```bash
npm install react-router-dom
```

## 2. Configuração do React Router DOM

Agora que o pacote foi instalado, vamos configurar as rotas no nosso projeto. O `react-router-dom` fornece vários componentes para navegação, mas os principais que usaremos são:

- `BrowserRouter`: Componente que envolve sua aplicação e habilita o uso de rotas.
- `Routes` e `Route`: Define as rotas e seus componentes correspondentes.


### 3. Criando os Componentes

Crie os componentes `home.tsx`, `about.tsx` e `contact.tsx` em uma pasta chamada `pages/`. Cada componente será bem simples para fins de demonstração:

```javascript
// home.tsx
export function Home() {
  return (
    <div>
      <h1>Página Inicial</h1>
    </div>
  );
}
```

```javascript
// about.tsx
export function About() {
  return (
    <div>
      <h1>Sobre Nós</h1>
    </div>
  );
}
```

```javascript
// contact.tsx
export function Contact() {
  return (
    <div>
      <h1>Contato</h1>
    </div>
  );
}
```

### 4. Configurando as Rotas no App.tsx

No arquivo `App.tsx`, importe os componentes necessários do `react-router-dom` e defina as rotas:

```javascript
import { BrowserRouter, Routes, Route } from 'react-router-dom';
import Home from './pages/Home';
import About from './pages/About';
import Contact from './pages/Contact';

function App() {
  return (
    <BrowserRouter>
      <div>
        <h1>Meu Aplicativo</h1>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/about" element={<About />} />
          <Route path="/contact" element={<Contact />} />
        </Routes>
      </div>
    </BrowserRouter>
  );
}

export default App;
```

### 5. Navegação Entre Páginas

Para permitir que os usuários naveguem entre as páginas, podemos usar o componente `Link` do `react-router-dom`. Adicione os links ao `App.tsx`:

```javascript
import { BrowserRouter, Routes, Route, Link } from 'react-router-dom';
import Home from './pages/Home';
import About from './pages/About';
import Contact from './pages/Contact';

function App() {
  return (
    <BrowserRouter>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">Sobre</Link>
            </li>
            <li>
              <Link to="/contact">Contato</Link>
            </li>
          </ul>
        </nav>

        <h1>Meu Aplicativo</h1>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/about" element={<About />} />
          <Route path="/contact" element={<Contact />} />
        </Routes>
      </div>
    </BrowserRouter>
  );
}

export default App;
```

Agora, ao clicar nos links, a navegação entre as páginas será realizada sem a necessidade de recarregar a página.

### 6. Configurando Rota 404 (Página Não Encontrada)

Para lidar com rotas que não existem, você pode adicionar uma rota "coringa" que exibe uma página de erro 404:

```javascript
function NotFound() {
  return (
    <div>
      <h1>404 - Página Não Encontrada</h1>
    </div>
  );
}

function App() {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">Sobre</Link>
            </li>
            <li>
              <Link to="/contact">Contato</Link>
            </li>
          </ul>
        </nav>

        <h1>Meu Aplicativo</h1>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/about" element={<About />} />
          <Route path="/contact" element={<Contact />} />
          <Route path="*" element={<NotFound />} />
          // Qualquer url acessada que não esteja parametrizada em algum `path` nas rotas, será então mostrada a página `NotFound`.
        </Routes>
      </div>
    </Router>
  );
}

export default App;
```

### 7. Conclusão

Agora, você tem uma aplicação React funcional com navegação usando o `react-router-dom`. Você pode adicionar mais rotas e personalizar conforme necessário para o seu projeto. Esta configuração básica cobre a maioria dos casos de uso comuns de navegação em aplicativos React.
