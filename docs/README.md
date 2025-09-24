# TwentyOne Theme - Filament 4 Compatible

## Overview

TwentyOne è un tema moderno focalizzato sui prediction market per applicazioni Laravel con **Filament 4**, **Livewire 3**, **Volt** e **Tailwind CSS**. Fornisce un set completo di componenti UI per engagement e trading.

## Key Features

### 🎯 **Prediction Market Focus**
- UI moderne per scommesse/prediction
- Market cards interattive
- Interfacce ispirate al trading
- Design responsive mobile-first

### 🚀 **Framework Integration**
- **Filament 4.x**
- **Livewire 3.x**
- **Volt 1.x**
- **Tailwind CSS 4 (beta)** via plugin ufficiale Vite
- **Flowbite 3.x**

### 🎨 **Modern Design System**
- Dark/Light mode
- Grid responsive
- Charts e visualizzazioni
- Palette professionale
- Accessibilità

## Architecture

### Directory Structure
```
TwentyOne/
├── resources/
│   ├── css/
│   │   ├── app.css                    # Stili principali
│   │   └── filament/admin/
│   │       ├── theme.css              # Tema Filament (opzionale)
│   │       └── tailwind.config.js     # Config Tailwind per Filament (opzionale)
│   ├── js/
│   │   ├── app.js                     # JavaScript principale
│   │   └── custom.js                  # Interazioni custom
│   └── views/                         # Blade/Livewire/Volt
├── public/                            # Asset compilati da Vite
├── vite.config.js                     # Configurazione Vite (v7)
├── tailwind.config.js                 # Configurazione Tailwind 4 (beta)
├── postcss.config.js                  # Configurazione PostCSS
└── package.json                       # Dipendenze NPM
```

### Build System
- **Vite 7** per la compilazione moderna degli asset
- **PostCSS** con `postcss-import`, `postcss-nesting`, `autoprefixer`
- Gli asset vengono compilati in `./public` e (opzionalmente) copiati in `../../../public_html/themes/TwentyOne`

## Filament 4 Integration

### Theme Configuration

Il tema può integrarsi con Filament 4:

```css
/* resources/css/filament/admin/theme.css */
@import '../../../../../../vendor/filament/filament/resources/css/theme.css';
```

```js
// resources/css/filament/admin/tailwind.config.js
import preset from '../../../../../../vendor/filament/filament/tailwind.config.preset'

export default {
    presets: [preset],
    content: [
        './app/Filament/**/*.php',
        './resources/views/filament/**/*.blade.php',
        './vendor/filament/**/*.blade.php',
    ],
}
```

### Panel Provider Integration

```php
use Filament\Panel;

public function panel(Panel $panel): Panel
{
    return $panel
        ->id('admin')
        ->path('admin')
        ->viteTheme('resources/css/filament/admin/theme.css')
        ->darkMode()
        ->sidebarCollapsibleOnDesktop();
}
```

## Development Workflow

### Prerequisites
- Node.js 18+
- NPM (o altro package manager)
- Laravel 12 con Filament 4

### Installation

1. Posizionati nella cartella del tema:
```bash
cd laravel/Themes/TwentyOne
```

2. Installa le dipendenze:
```bash
npm install
```

3. Sviluppo:
```bash
npm run dev
```

4. Build produzione:
```bash
npm run build
```

5. Copia su public_html (opzionale):
```bash
npm run copy
```

### Build Commands

| Command | Purpose |
|---------|---------|
| `npm run dev` | Dev server con hot reload |
| `npm run build` | Build produzione |
| `npm run watch` | Build in watch mode |
| `npm run copy` | Copia asset in `public_html/themes/TwentyOne` |

## PostCSS Configuration

```js
// postcss.config.js
export default {
  plugins: {
    'postcss-import': {},
    'postcss-nesting': {},
    autoprefixer: {},
  },
}
```

## Tailwind Configuration

```js
// tailwind.config.js
export default {
	content: [
		'./resources/**/*.{html,js,blade.php}',
		'./resources/views/**/*.blade.php',
		'../../Modules/**/Filament/**/*.php',
		'../../Modules/**/resources/views/**/*.blade.php',
		'../../resources/views/filament/**/*.blade.php',
		'../../vendor/filament/**/*.blade.php',
		'../../resources/views/**/*.blade.php',
		'../../storage/framework/views/*.php',
		'../../vendor/laravel/framework/src/Illuminate/Pagination/resources/views/*.blade.php',
		'./node_modules/flowbite/**/*.js',
	],
	theme: {
		fontFamily: {
			sans: ["Figtree", "ui-sans-serif", "system-ui", "sans-serif", "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji"],
		},
		extend: {
			colors: {
				market: { yes: '#10b981', no: '#ef4444', neutral: '#6b7280' },
				probability: { high: '#059669', medium: '#d97706', low: '#dc2626' },
			},
			animation: { 'pulse-slow': 'pulse 3s cubic-bezier(0.4, 0, 0.6, 1) infinite', 'bounce-in': 'bounceIn 0.5s ease-out' },
		},
	},
}
```

## Performance Optimization

- Tree-shaking CSS/JS
- Code splitting
- Immagini ottimizzate (WebP)
- Manifest Vite per versioning

## Browser Support

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

## Deployment

Checklist produzione:
1. `npm run build`
2. `npm run copy`
3. Verifica permessi file
4. Test responsive
5. Accessibilità
6. Performance

## Troubleshooting

- "Assets not loading": ricostruisci e copia
```bash
npm run build && npm run copy
```
- "Vite manifest error":
```bash
npm run build
```

## Collegamenti correlati
- [Analisi completa temi](../../analisi_completa_temi.md)
- [Analisi completa temi (aggiornata)](../../analisi_completa_temi_aggiornata.md)
- [Tema Sixteen - Index](../../Sixteen/docs/index.md)
- [Regole integrazione Vite del tema](./vite-error.md)
- [Regole Filament/Widget](./filament-widget-best-practices.md)

---

Ultimo aggiornamento: 2025-09-24