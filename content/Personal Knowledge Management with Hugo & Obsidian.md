---
dg-publish: true
title: Personal Knowledge Management with Hugo & Obsidian
date: "{{ .Date }}"
draft: "false"
---
### Prerequisites

- **Obsidian** installed on your machine
- Basic knowledge of **Markdown**
- A **GitHub** account
- Hugo installed on your machine (if not, follow the official installation guide)
- Git installed on your machine

### Step 1: Set up GitHub repository

1. **Create a new repository** on GitHub.
    
    - Go to your [GitHub](https://github.com/) account and create a new repository.
    - Name it `<your-username>.github.io` (replace `<your-username>` with your GitHub username). This is important because GitHub Pages uses this naming convention to host user pages.
    - Set it as **public** and initialize it with a `README.md` file.
2. **Clone the repository** to your local machine.
    
    bash
    
    Copy code
    
    `git clone https://github.com/<your-username>/<your-username>.github.io cd <your-username>.github.io`
    

### Step 2: Install and configure Hugo

1. **Install Hugo** if not already installed.
    
    - You can install Hugo from the terminal. Follow the instructions based on your OS from the Hugo website.
2. **Create a new Hugo site**. Inside your cloned repository:
    
    bash
    
    Copy code
    
    `hugo new site my-digital-garden cd my-digital-garden`
    
3. **Choose a theme**.
    
    - Hugo has a wide selection of themes, but since we are creating a digital garden, you can use a theme like hugo-book or [hugo-theme-digitalgarden](https://github.com/apvarun/digital-garden-hugo).
    - Download a theme and add it to your Hugo site:
        
        bash
        
        Copy code
        
        `git submodule add https://github.com/apvarun/digital-garden-hugo.git themes/digital-garden-hugo`
        
4. **Update Hugo's configuration** (`config.toml`).
    
    - Update your `config.toml` to use the theme and configure the basic site settings.
    - Example:
        
        toml
        
        Copy code
        
        `baseURL = "https://<your-username>.github.io/" languageCode = "en-us" title = "My Digital Garden" theme = "digital-garden-hugo"`
        

### Step 3: Integrating Obsidian with Hugo

1. **Create an Obsidian vault** if you haven’t already, or use your existing vault.
    
    - Open Obsidian and go to your vault.
2. **Set the Hugo content directory as a folder in Obsidian**.
    
    - Inside your Hugo project, go to the `content` directory.
    - Link this directory with Obsidian by adding it as a folder inside your Obsidian vault.
3. **Write notes in Obsidian** using Markdown.
    
    - Each note will become a page in your Hugo-generated site.
    - For each note you want to publish, ensure it’s saved as a `.md` file in the `content` folder.
    - Example front matter for each note (for Hugo):
        
        yaml
        
        Copy code
        
        `--- title: "My Note Title" date: 2024-10-20 ---`
        
4. **Use Obsidian’s bidirectional linking**.
    
    - You can use Obsidian’s link syntax (`[[Note Title]]`) to link notes, which will work well when you generate the site in Hugo.

### Step 4: Build and test the Hugo site locally

1. **Build your site locally**. Inside your Hugo directory, run:
    
    bash
    
    Copy code
    
    `hugo server`
    
    - This will start a local server on `localhost:1313`, allowing you to preview your digital garden.
2. **Make adjustments to the content and theme**.
    
    - As you view the site, make changes to your `config.toml`, themes, or add custom CSS if necessary to match your desired look.

### Step 5: Deploy to GitHub Pages

1. **Build the static files** for GitHub Pages:
    
    bash
    
    Copy code
    
    `hugo`
    
    - This will generate your site in the `public/` directory.
2. **Push the site to GitHub**.
    
    - Move all files from the `public` directory to the root of your GitHub Pages repository.
    - Commit the changes:
        
        bash
        
        Copy code
        
        `git add . git commit -m "Deploy Hugo site" git push origin main`
        
3. **Set up GitHub Pages**.
    
    - In your GitHub repository, go to **Settings** > **Pages**.
    - Select the **main branch** as the source and save.
4. **Visit your site**.
    
    - After GitHub Pages builds your site, visit `<your-username>.github.io`.

### Step 6: Automating with GitHub Actions (optional)

You can automate the process of building and deploying your Hugo site using **GitHub Actions**.

1. Create a `.github/workflows/gh-pages.yml` file in your repository:
    
    yaml
    
    Copy code
    
    `name: Deploy Hugo site  on:   push:     branches:       - main  jobs:   deploy:     runs-on: ubuntu-latest     steps:     - name: Checkout repository       uses: actions/checkout@v2     - name: Set up Hugo       uses: peaceiris/actions-hugo@v2       with:         hugo-version: 'latest'     - name: Build the site       run: hugo     - name: Deploy to GitHub Pages       uses: peaceiris/actions-gh-pages@v3       with:         github_token: ${{ secrets.GITHUB_TOKEN }}         publish_dir: ./public`
    
2. **Commit and push** the workflow file:
    
    bash
    
    Copy code
    
    `git add .github/workflows/gh-pages.yml git commit -m "Add GitHub Actions workflow" git push origin main`
    

Now, every time you push new content to the `main` branch, GitHub Actions will automatically build and deploy your Hugo site.

### Step 7: Keep Adding and Updating Content

Now you can use Obsidian to manage your notes and content. Any notes you write in Obsidian will be reflected in your digital garden on GitHub Pages whenever you commit and push them.