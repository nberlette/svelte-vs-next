# SvelteKit 🆚  Next.js

**Objectives**: fast, easy, convention over configuration, & batteries included. Overwhelming choices &lt; providing a clear path forward.

## Comparison of Major Features

**Contenders**: [SvelteKit][sveltekit-url] (by [Svelte][svelte-url]) and [Next.js][next-url] (by [Vercel][vercel-url]).

---

|                            Feature/Category |                              SvelteKit | Next.js                       |  Winner   | More Information                                                                                                                                                                             |
| ------------------------------------------: | -------------------------------------: | :---------------------------- | :-------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|                                UI framework |                   [Svelte][svelte-url] | [React][react-url]                      | SvelteKit | Svelte offers faster, more minimal DOM updates & smaller Kb client size.                                                                                                                     |
|                            Hot reload (dev) |                                     🟢 | 🟢                             |    --     | I.e. Auto reload on file save.                                                                                                                                                               |
|                       O(1) hot reload (dev) |                    [Vite][vite-url] 🟢 | ⛔                             | SvelteKit | I.e. Processes only the changed files. Fast even in big projects.                                                                                                                            |
|                        "Fast refresh" (dev) |                                     🟢 | 🟢                             |    --     | I.e. UI state preserved across reloads.                                                                                                                                                      |
|                       Write modern JS (dev) |                                     🟢 | 🟢                             |    --     | Svelte compiler processes it. Next.js uses Babel for this.                                                                                                                                   |
|                    A11y console hints (dev) |                                     🟢 | ⛔                             | SvelteKit |                                                                                                                                                                                              |
|                              Prettier (dev) |                                     🟢 | 🟢                             |    --     | For `.svelte` or `.jsx` files. For SvelteKit, install `Svelte for VSCode` extension.                                                                                                         |
|                              Bundler (prod) |                   [Rollup][rollup-url] | [Webpack][webpack-url]        |    --     | E.g. Minify assets, etc.                                                                                                                                                                     |
|       Auto code-splitting, per route (prod) |                                     🟢 | 🟢                             |    --     | I.e. Auto code splits JS & CSS per route & bundles appropriately.                                                                                                                            |
| [HTTP2 push][http2push-url] JS/CSS\* (prod) |                                     ⛔ | ⛔                             | _Neither_ | I.e. Set initial page's HTML headers to push JS & CSS. Requires host support (and/or 'link preload' added to HTML head). \*_Chrome deprecated this 12/2020._                                 |
|    Build adapters for host providers (prod) |                                     🟢 | ⛔                             | SvelteKit | SvelteKit provides easy portability. Next.js works best with Vercel.                                                                                                                         |
|                      Kb size: `Hello World` |                         **0.52 Kb** 🟢 | ⚠️  ***204 Kb***               | SvelteKit | \*Mar 19 2021. [sapper-note-url]                                                                                                                                                             |
|                       Kb size: `Real World` |                         **45.3 Kb** 🟢 | ⚠️  ***327 Kb***               | SvelteKit | \*Mar 13, 2021 [svelterealworld-url], [sapper-note-url]                                                                                                                                      |
|      Server Side Rendering (SSR), per route |                                     🟢 | 🟢                             |    --     | I.e. Server-side rendered (at run time).                                                                                                                                                     |
|     Static Site Generation (SSG), per route |                                     🟢 | 🟢                             |    --     | I.e. Static (at build time).                                                                                                                                                                 |
|      Incremental Rendering (SSG), per route |                                     ⛔ | 🟢                             |  Next.js  | I.e. Static 'on demand' in production--first req dynamic then cached.                                                                                                                        |
|             Cache MaxAge Headers, per route |                                     🟢 | 🟡                             | SvelteKit | SvelteKit can set headers for server routes or specify max-age for client routes via load function. Next.js allows it for server routes via [vercel.json][vercel3-url]                       |
|                 File-based routing (Routes) |                                     🟢 | 🟢                             |    --     | For simplicity. Other routing utilities should be included.                                                                                                                                  |
|                         "SPA mode" (Routes) |                                     🟢 | 🟢                             |    --     | SSR for initial page load, then client-side routing for subsequent pages.                                                                                                                    |
|          Pre-fetch JS/CSS on hover (Routes) |                                     🟢 | 🟢  [next/link][nextlink-url]  | SvelteKit | Just add `sveltekit:prefetch` to a regular link. Svelte can prefetch routes (via regex); Next.js requires their `next/link` component; see docs. It's nicer to use regular links.            |
|                          Built-in: Metadata |    [<svelte:head>][sveltehead-url]  🟢 | 🟢  [next/head][nexthead-url]  |    --     | Place within `<svelte:head>...</svelte:head>`                                                                                                                                                |
|                  Built-in: State Management |     [svelte/store][sveltestore-url] 🟢 | 🟡                             | SvelteKit | Ideal is one, easy, built-in way. React has many choices--Zustand is reasonable.                                                                                                             |
|                        Built-in: Animations | [svelte/animate][svelteanimate-url] 🟢 | 🟡                              | SvelteKit | 3rd-party options exist for React, but they're not as easy to use.                                                                                                                           |
|                       Built-in: CSS scoping |                                     🟢 | 🟢                             | SvelteKit | Svelte's is automatic. Next.js' is via CSS modules or CSS in JSX (not as clean).                                                                                                             |
|                      Web vitals reporting\* |                                     🟢 | 🟢                             |  Next.js  | \*Not-so-relevant these days; easily added via analytics snippet/platform provider, eg: [Cloudlfare Site Analytics][cloudflare-url] (zero-config). [Vercel][vercel2-url] (for Next or Nuxt). |
|                  Access Control / User Auth |           ([soon?][svelteauth-url]) ⛔ | 🟢 [NextAuth.js][nextauth-url] |  Next.js  | NextAuth.js is defacto standard for Next.js; easy to use; email, social, &/or one-click link.                                                                                                |
|                             Image component |     [svelte-image][svelteimage-url] 🟢 | 🟢 [next/image][nextimage-url] |    --     | Preferably optimized image generation with caching.                                                                                                                                          |
|                             Form Components |                  [Felte][felte-url] 🟢 | 🟢 [Formik][formik-url]        |    --     | Felte offers a nearly-native HTML5 form experience. Or [Sveltik][sveltik-url] is a port of Formik for React. Can use Yup for validation.                                                     |
|      SWR-like (Stale While Reload) fetching |    [svelte-query][svelte-query-url] 🟢 | 🟢 [SWR][swr-url]              |    --     | SWR is by Vercel. Easy fetch/isLoading/errors/caching.                                                                                                                                       |
|     [Tailwind CSS][tailwind-url] compatible |                                     🟢 | 🟢                             |    --     | Easy via [svelte-add-tailwindcss][svelte-add-tailwind-url]. Next.js requires more steps, but [RFC][next-rfc-url] for `npx init tailwind`                                                     |
|       [Headless UI][headless-url] available |                                     ⛔ | 🟡  WIP                        |  Next.js  | 🚧  Un-styled UI components (dropdown, slider, toggle, etc) from Tailwind creators.                                                                                                              |
|                               Documentation |                                     👍 | 👍                             |    --     | Both are excellently documented.                                                                                                                                                                                            |

---

### Legend

* ⚠️  = Important Info / Warning
* 🟢  = Feature Available
* 🟡  = 3rd-party / partially available
* ⛔  = Feature Unavailable
* 🚧  = Work in Progress or RFC  

---  

## Conclusion and Thoughts

Both of these frameworks bring a lot to the table, each in their own respective flavors. I'd say that rather than one being an out-and-out winner over the other, they're more along the lines of cordial competitors in similar fields. At the end of the day, the choice (as always) boils down to your development preferences, and project-specific requirements.  

In the React scene, Next.js and the development experience that [Vercel][vercel-url] provides are essentially unrivalled. They really are best-in-class, no doubt about that. But as we edge closer to the 10-year mark of React's existence, I must say that [Svelte][svelte-url] (and SvelteKit) are a refreshing change of pace. With it's built-in features (lookin' at you CSS animations) and familiar syntax, it just seems to pick up right where Vanilla JS fell short... without forcing us to learn a whole new style of coding.  

I've been experimenting with both Svelte and Next.js **a lot** recently, and today I still have a lot of trouble picking one over the other 😬  

---

> MIT 2021 © [Nicholas Berlette](https://github.com/nberlette). Forked from [jasongitmail's original](https://github.com/jasongitmail/svelte-vs-next).

[react-url]: https://reactjs.org/
[svelte-url]: https://svelte.dev
[svelteauth-url]: https://github.com/sveltejs/kit/tree/master/examples/realworld.svelte.dev/src/routes/auth
[svelteimage-url]: https://svelte-image.matyunya.now.sh/
[sveltehead-url]: https://svelte.dev/docs#svelte_head
[svelte-query-url]: https://github.com/SvelteStack/svelte-query
[sveltekit-url]: https://kit.svelte.dev/
[felte-url]: https://felte.dev/
[sveltik-url]: https://github.com/nathancahill/sveltik
[svelte-realworld-url]: <https://realworld.svelte.dev/>
[sapper-note-url]: <https://svelte.dev/blog/sapper-towards-the-ideal-web-app-framework>
[sveltestore-url]: https://svelte.dev/docs#svelte_store
[svelteanimate-url]: https://svelte.dev/docs#svelte_animate
[svelte-add-tailwind-url]: https://github.com/svelte-add/tailwindcss
[next-url]: https://nextjs.org/
[nextauth-url]: https://next-auth.js.org/
[nextimage-url]: https://nextjs.org/docs/api-reference/next/image
[nextlink-url]: https://nextjs.org/docs/api-reference/next/link
[nexthead-url]: https://nextjs.org/docs/api-reference/next/head
[next-rfc-url]: https://github.com/vercel/next.js/discussions/20030
[vercel-url]: https://vercel.com/
[vercel2-url]: https://vercel.com/docs/analytics
[vercel3-url]: https://vercel.com/docs/configuration#project/headers
[swr-url]: https://swr.vercel.app
[vite-url]: https://vitejs.dev/
[formik-url]: https://formik.org/
[http2push-url]: https://brianli.com/cloudflare-workers-sites-http2-server-push/
[tailwind-url]: https://tailwindcss.com/
[headless-url]: https://headlessui.dev/
[webpack-url]: https://webpack.js.org/
[rollup-url]: https://rollupjs.org/
[preact]: https://preactjs.org/
[cloudflare-url]: https://cloudflare.com/
