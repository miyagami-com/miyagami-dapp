# Miyagami Dapp
Decentralized chatting app

## Table of Contents

* [Overview](#overview)
* [Development](#development)
    * [Technology stack](#technology-stack)
    * [Microservices](#microservices)
* [Getting started](#getting-started)

## Overview

The Miyagami dapp consists of a simple front-end made with Svelte, and a decentralized database based on GUN.


## Development

### Technology stack

After careful consideration the project will be built on a decentralized stack.

* A front-end application built using the open source [Svelte](https://svelte.dev/) project.
* A decentralized database using [GUN](https://gun.eco/).


### Microservices

The following services will be used in this project.

* Authentication will be provided by [SEA](https://gun.eco/docs/SEA).
* UI components will be made with [Tailwind CSS](https://tailwindui.com/).
* [Vercel](https://vercel.com/) will be used for deploying the front-end.


## Getting started

This step by step guide will familiarize you with how to get started with the project right away.

### 1. NodeJS

>We will be using the LTS version of [NodeJS](https://nodejs.org/en/). To switch node versions use a node version manager.
The nvm [n](https://github.com/tj/n) is recommended.

```
node -v

sudo npm install -g n 
sudo n 14.15.4  # Current LTS
```

### 2. Front-end

>[Svelte](https://svelte.dev/) is a radical new approach to building user interfaces. Whereas traditional frameworks like React and Vue do the bulk of their work in the browser, Svelte shifts that work into a compile step that happens when you build your app.

```
npm install
npm run dev
```

Check out the [Live Version](https://miyagami-dapp.vercel.app/)
