# Tailwind CSS JIT Mode SSR Bug

This repository demonstrates a common bug encountered when using Tailwind CSS's JIT mode with server-side rendering (SSR) frameworks like Next.js or Nuxt.js.

## The Problem

In JIT mode, Tailwind only generates CSS for the classes actually used in your components. During SSR, only the classes used on the server are generated.  If your client-side rendering uses different classes, those styles will be missing, resulting in styling issues in the browser after the initial render.

## Setup

1. Clone the repository.
2. Run `npm install`.
3. Run `npm run dev` to start the development server (assumes Next.js or similar).

## Bug Reproduction

Observe the initial rendering and note that the styling is incomplete.  The client-side classes are not applied until after the initial render is complete and the client-side code kicks in.

## Solution

The solution is to ensure that all classes used on the client-side are also used, or at least accounted for, on the server-side. Refer to the `bugSolution.js` for a possible fix that accounts for this issue, even if the client-side class isn't directly rendered in all cases on the server-side.

This might involve carefully reviewing your component structure and conditionally rendering classes, using CSS Modules for better separation of concerns, or leveraging techniques specific to your SSR framework. See `bugSolution.js` for one approach. 