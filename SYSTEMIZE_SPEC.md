# Systemize Specification

> The following document defines the architecture for a design system code base, built with Systemize.

## Architectural Layers

Systemize is built to eliminate friction between designers and engineers in producing a scalable design system. To accomplish this, the system is opinionated and there are a few different layers that need their structure maintained in order to not break said system.

### Static Design Tools & Design Tokens

All User Interfaces start with a designer and a static design tool. Over the last few years, the industry standard has become [Figma](https://figma.com) as it is the most collaborative tool available. To closely fit this paradigm, Systemize ships with a Figma file that contains all design tokens and default components already defined. This setup is intended to provide a starting point for building your design system in Figma, and allow for the creation of design tokens. 

Systemize is built to work with [Style Dictionary](https://github.com/amzn/style-dictionary) compatible JSON to achieve an easy transition from Figma to code. There are a number of Figma plugins that allow you to export Style Dictionary compatible JSON from your Figma project. Systemize will then build a stylesheet of CSS custom properties that can be used throughout your source components. 

### Components

Systemize components are built in [Svelte](http://svelte.dev) in order to take advantage of Svelte's compiler and produce a (mostly) platform agnostic design system. All components are written in Typescript and follow this folder structure...

```
|-- lib
    |-- components
        |-- Component Name
            |-- Component.svelte
            |-- component.ts
            |-- component.test.ts

```

To keep Svelte components clean, all type definitions and utility functions should be exported from `component.ts` - this will also allow the overall functionality to be ported to a Vanilla JS setup where the Svelte components cannot be used directly.

### Workshop Environment

Systemize ships with a [Workshop Environment](https://bradfrost.com/blog/post/a-frontend-workshop-environment) for fully documenting your design system and its components. Systemize is built using [SvelteKit](http://kit.svelte.dev) to take advantage of it's routing system which handles the entire Workshop application. 

### Build System, Web Components, & Legacy Support

WIP

