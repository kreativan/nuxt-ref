https://kreativan.github.io/nuxt-ref/users/dist/

## Build Setup

```bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```


For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).

### UIkit
```
npm install nuxt-vuikit --save
```

Add nuxt-vuikit to modules section of your nuxt.config.js
```
{
  modules: [
    'nuxt-vuikit'
  ],
  vuikit: {
    defaultTheme: true,
    icons: true
  }
}
```

### Git
```
git add .
git commit -m "Initial Commit"
git remote add origin https://github.com/YOUR_USERNAME/NEW_REPO_NAME.git
git push -u origin main
```