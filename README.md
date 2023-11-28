# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

Best option @ option 1

Option 1. works in both private and public repository
create a vercel app then connect it to your github project works like magic click here https://vercel.com/signup 

//The below step has been added to your code just go to github account click actions to deploy project

//follow steps


Option 2. works in public repository unless you upgrade github account
Steps to setup CI/CD using github pages 

1.Setup a Github page 
sign up link https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home

2.Host Code in GitHub

follow installation steps

In the newly created project move to vite.config.js file in the root folder

add the line below inside defineConfig function 

base: '/workoutapp/',

Go back to the vite website at deploy Static site

click here then copy paste yml code https://vitejs.dev/guide/static-deploy.html#github-pages

@your github click actions

click link set up a workflow yourself

paste yml code in main.yml

the code

# Simple workflow for deploying static content to GitHub Pages
name: Deploy static content to Pages

on:
  # Runs on pushes targeting the default branch
  push:
    branches: ['main']

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# Sets the GITHUB_TOKEN permissions to allow deployment to GitHub Pages
permissions:
  contents: read
  pages: write
  id-token: write

# Allow one concurrent deployment
concurrency:
  group: 'pages'
  cancel-in-progress: true

jobs:
  # Single deploy job since we're just deploying
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Set up Node
        uses: actions/setup-node@v3
        with:
          node-version: 18
          cache: 'npm'
      - name: Install dependencies
        run: npm install
      - name: Build
        run: npm run build
      - name: Setup Pages
        uses: actions/configure-pages@v3
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v2
        with:
          # Upload dist repository
          path: './dist'
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v2

The code will run and deploy website on public url limited to github

connection to cpanel click here -> https://youtu.be/W70fWpcHMzc


