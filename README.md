# Svelte & Firebase & Tailwindcss

[Website](https://svelte-firebase-k0kz0zs3x-ogty.vercel.app/)

 - [Svelte](https://svelte.dev/)
 - [Sveltekit](https://kit.svelte.dev/)
 - [Firebase](https://firebase.google.com/?hl=ja)
 - [Tailwindcss](https://tailwindcss.com/)
 - [Vercel](https://vercel.com/)

---

### Svelte設定

```bash
$ npx degit sveltejs/template <app-name>
$ cd <app-name>
$ npm i
$ npm i svelte-routing sveltestrap
$ npm i firebase
$ npm i -D tailwindcss@latest postcss@latest autoprefixer@latest
$ npx tailwindcss init
```

---

### Tailwindcss設定

**`tailwind.config.js`**

```js
const production = !process.env.ROLLUP_WATCH;

module.exports = {
  content: [
    './src/**/*.svelte',
    './src/**/*.html',
  ],
  enabled: production,
  theme: {
    extend: {},
  },
  plugins: [],
}
```

```bash
$ npm i svelte-preprocess
```

**`rollup.config.js`**

```js
import sveltePreprocess from 'svelte-preprocess';

export default {
  plugins: [
    svelte({
      preprocess: sveltePreprocess({
        sourceMap: !production,
        postcss: {
          plugins: [
            require('tailwindcss'),
            require('autoprefixer'),
          ],
        },
      }),

      ...
};
```

***

### Firebase設定

1. プロジェクト作成
2. プロジェクトの設定 → SDK の設定と構成 → 構成を選択し → オブジェクトをコピー
3. `App.svelte`内の`firebaseConfig`に貼り付け
4. AuthenticationからGoogleプロバイダーを追加

##### TODO: どうやら`public/index.html`に配置するらしい...でも適応されない...

***

### Routing設定

**`App.svelte`**

```svelte
<script>
    import { Router, Link, Route } from "svelte-routing";
    import Home from "./pages/Home.svelte";
    import About from "./pages/About.svelte";
</script>
  
<Router>
    <nav>
        <Link to="">home</Link>
        <Link to="about">about</Link>
    </nav>
    <main>
        <Route path="" component={Home} />
        <Route path="about">
        <About />
        </Route>
    </main>
</Router>

<style global lang="postcss">
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
</style>
```

***

### Vercelデプロイ

[Deploy Svelte with Vercel](https://vercel.com/guides/deploying-svelte-with-vercel)  

Firebase → プロジェクト → Authentication → Sign-in method → 承認済みドメインにVercelのドメインを追加してください。

***

### Firebaseデプロイ

```bash
$ firebase init hosting
 # setting
$ firebase deploy --only hosting
```

##### Hostingの選択にはスペースキーを使います。

デプロイ取り消し

```bash
$ firebase hosting:disable
```
