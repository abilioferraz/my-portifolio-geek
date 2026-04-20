# Design System & Components

## 🎨 Color Palette

### Core Colors

- **Primary**: `#7af7df` (Cyan) - CTAs e highlights
- **Primary Strong**: `#5bddc9` - Hover states
- **Secondary**: `#ffca63` (Yellow) - Tags e labels
- **Accent**: `#7ea3ff` (Blue) - Status e informações
- **Danger**: `#ff8d83` (Red) - Alerts e errors

### Background

- **Main BG**: `#060b17` - Background principal
- **Surface**: `rgba(14, 24, 48, 0.78)` - Cards e containers
- **Surface Strong**: `#121f3c` - Elementos elevados

### Text

- **Primary**: `#f3f7ff` - Texto principal
- **Muted**: `#97a6c6` - Texto secundário

---

## 📐 Typography

### Font Stack

```css
/* Headlines */
'Chakra Petch', sans-serif

/* Body text */
'Space Grotesk', sans-serif
```

### Sizes (Responsive)

- **H1**: `clamp(2.8rem, 9vw, 5.8rem)`
- **H2**: `clamp(2rem, 6vw, 3.4rem)`
- **H3**: `1.35rem`
- **Body**: `clamp(1rem, 2.4vw, 1.15rem)`
- **Small**: `0.9rem - 0.95rem`

### Font Weights

- Regular: 400
- Medium: 500
- Semi-bold: 600
- Bold: 700

---

## 🎯 Spacing Scale

```css
--radius-sm: 12px /* Botões, inputs */ --radius-md: 20px /* Cards */
  --radius-lg: 28px /* Containers */ --radius-xl: 36px /* Panels */;
```

### Margins & Padding

- xs: 0.5rem
- sm: 0.75rem - 1rem
- md: 1.25rem - 1.5rem
- lg: 2rem - 2.5rem
- xl: 3rem - 4rem

---

## 🧩 Componentes

### Button

```html
<!-- Primary Button -->
<a class="button button--primary" href="#link"> Ação Principal </a>

<!-- Secondary Button -->
<a class="button button--secondary" href="#link"> Ação Secundária </a>

<!-- Ghost Button -->
<a class="button button--ghost" href="#link"> Link Discreto </a>
```

**Estados:**

- Default: background gradiente
- Hover: transform translateY(-2px), shadow aumentada
- Focus: outline focus-visible

### Card

```html
<article class="project-card" data-reveal>
  <div class="project-card__top">
    <span class="project-card__status">Web Application</span>
    <h3>Título do Projeto</h3>
  </div>
  <p>Descrição do projeto...</p>
  <div class="project-card__footer">
    <ul class="tag-list">
      <li>React</li>
      <li>TypeScript</li>
    </ul>
    <a class="project-link" href="#">Ver repositório</a>
  </div>
</article>
```

**Variações:**

- `.project-card` - Projetos
- `.stack-card` - Stack técnico
- `.quest-card` - Objetivos
- `.value-card` - Diferenciais
- `.contact-card` - Contato

### Tag/Badge

```html
<!-- Status Tag -->
<span class="project-card__status">Status aqui</span>

<!-- Simple Tag -->
<ul class="tag-list">
  <li>Tag 1</li>
  <li>Tag 2</li>
</ul>
```

### Menu Mobile

```html
<button
  class="menu-toggle"
  data-menu-toggle
  aria-expanded="false"
  aria-label="Abrir menu principal"
>
  <span class="menu-toggle__bars" aria-hidden="true">
    <span></span>
    <span></span>
    <span></span>
  </span>
</button>
```

**Comportamento:**

- Abre/fecha ao clicar no botão
- Fecha ao selecionar um link (em mobile)
- Fecha ao pressionar Escape
- Automaticamente oculto em desktop (640px+)

### Timeline

```html
<div class="timeline">
  <article class="timeline__item" data-reveal>
    <span class="timeline__meta">2022-2023</span>
    <h3>Título</h3>
    <p>Descrição da fase...</p>
  </article>
</div>
```

---

## ♿ Acessibilidade

### ARIA Labels

```html
<!-- Menu toggle button -->
<button aria-expanded="false" aria-controls="site-menu">Menu</button>

<!-- Icon without text -->
<span class="icon" aria-hidden="true">→</span>

<!-- Non-visual descriptions -->
<a aria-label="Abrir repositório do projeto XYZ"> Ver código </a>
```

### Keyboard Navigation

| Key      | Behavior                             |
| -------- | ------------------------------------ |
| `Tab`    | Navigate entre elementos interativos |
| `Enter`  | Ativar links e buttons               |
| `Escape` | Fechar menu mobile                   |
| `Space`  | Ativar buttons                       |

### Focus Management

```css
:focus-visible {
  outline: 3px solid rgba(122, 247, 223, 0.75);
  outline-offset: 4px;
}
```

### Color Contrast

Mínimo WCAG AA:

- Normal text: 4.5:1
- Large text (18pt+): 3:1
- Graphical elements: 3:1

---

## 🎬 Animations

### Reveal Animation (Scroll)

```html
<section data-reveal>Conteúdo que anima ao entrar na viewport</section>
```

**Propriedades:**

- Fade in: 0 → 1 opacity
- Slide up: 18px translateY → 0
- Duration: 420ms
- Timing: ease

### Hover Effects

Cards têm:

- `transform: translateY(-4px)` on hover
- `border-color` mais forte
- `box-shadow` aumentada

---

## 📱 Responsive Behavior

### Mobile (< 640px)

- Menu hamburger ativo
- Grids em 1 coluna
- Tipografia menor
- Spacing reduzido

### Tablet (640px - 860px)

- Menu horizontal
- Grids em 2 colunas
- Tipografia escalada
- Spacing normal

### Desktop (860px+)

- Layout completo com sidebars
- Grids em 3+ colunas
- Tipografia máxima
- Timeline alternada (duas colunas)

---

## 🔄 Data Config Pattern

Conteúdo é renderizado via `portfolioConfig` em `script.js`:

```javascript
const portfolioConfig = {
  profile: {
    /* ... */
  },
  timeline: [
    /* ... */
  ],
  projects: [
    /* ... */
  ],
  stack: [
    /* ... */
  ],
  quests: [
    /* ... */
  ],
  valueProps: [
    /* ... */
  ],
  contacts: [
    /* ... */
  ],
  metrics: [
    /* ... */
  ],
  actions: {
    /* ... */
  },
};
```

**Vantagens:**

- Fácil manutenção de conteúdo
- Separação de dados e apresentação
- Reutilização de componentes
- Pronto para integração com API/CMS

---

## 🚀 Performance Tips

1. **Lazy Load Images**

   ```html
   <img loading="lazy" src="..." alt="..." />
   ```

2. **Use CSS Variables**

   ```css
   color: var(--text-muted);
   ```

3. **Optimize Fonts**
   - Usar `display=swap` no Google Fonts
   - Preconnect com `<link rel="preconnect">`

4. **Minify em Produção**
   - HTML, CSS e JS compactados
   - Remover console.logs

5. **Preload Critical Resources**
   ```html
   <link rel="preload" href="..." as="..." />
   ```

---

Para dúvidas sobre implementação, consulte os arquivos source ou abra uma issue.
