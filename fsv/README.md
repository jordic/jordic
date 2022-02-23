# Javascript modern sense tooling

FullStackValles/feb 2022


## The Javascript Fatigue

- Aquells temps en que es podien programar coses amb un editor i el navegador
- Has configurat mai webpack?
- Babel/webpack/nextjs

## Encara pot ser divertit

### Lit-htm

https://lit.dev/docs/v1/lit-html/introduction/

```javascript
<script type="module">

import {html, render} from 'https://unpkg.com/lit-html?module';

// Define a template
const myTemplate = (name) => html`<p>Hello ${name}</p>`;

// Render the template to the document
render(myTemplate('World'), document.body);

</script>
```

### Preact/htm
https://github.com/developit/htm

- Preact: Una alternativa de 3Kb amb la mateixa API que react.
- A [vinissimus.com](https://www.vinissimus.com/es/) la fem servir a prod. Reducció de 70Kb al bundle.
- Pot fer-se servir també amb JSX.
- No volem tooling, així que la fem servir amb htm

```javascript
<script type="module">
    import { html, Component, render } from 'https://unpkg.com/htm/preact/standalone.module.js';

    class App extends Component {
      addTodo() {
        const { todos = [] } = this.state;
        this.setState({ todos: todos.concat(`Item ${todos.length}`) });
      }
      render({ page }, { todos = [] }) {
        return html`
          <div class="app">
            <${Header} name="ToDo's (${page})" />
            <ul>
              ${todos.map(todo => html`
                <li key=${todo}>${todo}</li>
              `)}
            </ul>
            <button onClick=${() => this.addTodo()}>Add Todo</button>
            <${Footer}>footer content here<//>
          </div>
        `;
      }
    }

    const Header = ({ name }) => html`<h1>${name} List</h1>`

    const Footer = props => html`<footer ...${props} />`

    render(html`<${App} page="All" />`, document.body);
</script>
```

Els esm modules només funcionen amb un servidor http
`npm install http-server -g`

