# YellowShuttl Landing Page

A stunning, revolutionary landing page for YellowShuttl - the next-generation fleet management and live tracking platform for educational institutions.

Built with **Svelte 5**, featuring modern animations, scroll-triggered effects, and an unconventional design that breaks all the rules.

## About YellowShuttl

YellowShuttl is a comprehensive fleet management solution designed specifically for educational institutes. It offers real-time tracking, ride statistics, fuel consumption data, and driver performance metrics - all at a fraction of traditional costs by leveraging smartphone technology.

## Features of This Landing Page

- **Hero Section**: Animated gradient background with mouse-parallax effect, floating logo, and animated text
- **Problem Statement**: Glassmorphic cards showcasing challenges in educational transport
- **Solution Showcase**: Feature art display with hover animations
- **Features Grid**: 4 interactive cards with app screenshots and smooth hover effects
- **Impact Section**: Rotating icon animations highlighting environmental, safety, and operational benefits
- **App Showcase**: Gallery of beautiful app screenshots
- **CTA Section**: Animated gradient background with links to Blink42.com
- **Responsive Design**: Fully responsive across all devices

## Technical Highlights

- **Svelte 5 Runes**: Using `$state`, `$derived` for reactive state management
- **Intersection Observer API**: For scroll-triggered animations
- **Pure CSS Animations**: No external animation libraries needed
- **Mouse Parallax**: Interactive hero background that follows cursor movement
- **Smooth Scroll Effects**: All sections animate on scroll
- **Modern Design**: Dark theme with vibrant gradients and glassmorphism

## Developing

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```sh
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

To create a production version of your app:

```sh
npm run build
```

You can preview the production build with `npm run preview`.

> To deploy your app, you may need to install an [adapter](https://svelte.dev/docs/kit/adapters) for your target environment.
