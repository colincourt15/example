
# Host a Static Website on a Forge

## Statement of Purpose


This document provides directed instructions to Marvin McLaren for preparing a resume with Markdown while building a static web host. The created process adheres to technical writing principles defined in Andrew Etter's Modern Technical Writing book.

 
Etter says, the technical documentation methodology of today should support lightweight efficiency. According to his principles users should employ distributed version control systems, lightweight markup languages and static site generators together with forges. The mentioned tools enable collaborative workflows which simplifies documentation flows while both enhancing accessibility through portable systems that require low maintenance efforts in the long term. Following the guidance allows technical writers and developers to create professional documentation systems that require minimal operational costs.

## Prerequisites

Before you begin, ensure you have the following installed:

### Install 'make' on Windows

-   Visit [Stack Overflow guide](https://stackoverflow.com/questions/32127524/how-to-install-and-use-make-in-windows)
    
-   Follow the instructions to download and install
    
-   Verify the installation by running:
    
    ```
    make --version
    ```
    

### Install Python

-   Visit [Python's official page](https://www.python.org/)
    
-   Download and install Python following the provided instructions
    
-   Ensure that Python is added to your system’s PATH
    
-   Verify the installation by running:
    
    ```
    python --version
    ```
    

### Install a Static Site Generator (Pelican)

-   Open **Command Prompt (CMD)** (not PowerShell)
    
-   Enter the command:
    
    ```
    python -m pip install "pelican[markdown]"
    ```
    
-   Verify the installation by running:
    
    ```
    pelican --version
    ```
    

### Install `ghp-import` for Deployment

-   Open **CMD** and run:
    
    ```
    python -m pip install ghp-import
    ```
    
-   This tool helps deploy static websites to GitHub Pages
    

### Install a Version Control System (Git)

-   Visit [Git's download page](https://git-scm.com/downloads/win)
    
-   Follow the installation instructions
    
-   Verify installation by running:
    
    ```
    git --version
    ```
    

### Create a Forge Account (GitHub)

-   Visit [GitHub](https://github.com/)
    
-   Create an account
    

## Instructions

### Step 1: Set Up a Repository on GitHub

1.  Open [GitHub](https://github.com/)
    
2.  Click **New** to create a repository
    
3.  Choose a repository name (e.g., `example`)
    
4.  Click **Create Repository**
    
5.  Copy the repository URL for future use
    
6.  Add a README file during setup to help document your project
    

**Etter’s Principle:** A distributed version control system should be utilized for efficient tracking of changes.  Multiple people can edit documentation through Git version control systems which maintain extensive logs of the documentation changes made by all collaborators.  Such version control preserves data integrity while making it possible for multiple users to co-edit easily and provides an option to revert changes if required.

### Step 2: Create a Directory for the Website

1.  Open **CMD** and navigate to your desired directory
    
2.  Run the command:
    
    ```
    pelican-quickstart
    ```
    
3.  Follow the prompts, setting the URL prefix to `https://yourgithubusername.github.io/example`
    
4.  Choose the default settings unless otherwise required
    

**Etter’s Principle:** Static site generators make websites simpler and eliminate the need for CMS database systems.  The fast website load times and minimal security risks together with simple maintenance features make static sites stand out.

### Step 3: Add Content

1.  Navigate to the `example/content` directory
    
2.  Create a resume file:
    
    ```
    echo "Title: Resume\nDate: 2025-02-14 12:00\nCategory: Resume" > resume.md
    ```
    
3.  Create a directory for additional pages:
    
    ```
    mkdir pages
    ```
    
4.  Create a cover letter:
    
    ```
    echo "Title: Cover Letter" > pages/coverletter.md
    ```
    

**Etter’s Principle:** Written documentation should exist as plain text because it promotes ease of collaboration plus portability between systems.  All text editors can easily access plain text files which enables universal readability because they use no proprietary format.

### Step 4: Test the Site Locally

1.  Generate the site:
    
    ```
    pelican content
    ```
    
2.  Start a local server:
    
    ```
    pelican --listen
    ```
    
3.  Open the provided link in a browser to view the site
    
4.  Ensure all content is formatted correctly and links function as expected
    

**Etter’s Principle:** Always test documentation before publishing. Local site preview enables users to find formatting mistakes along with broken links and absent files before going live.

### Step 5: Push to GitHub

1.  Initialize Git:
    
    ```
    git init
    ```
    
2.  Add and commit files:
    
    ```
    git add .
    git commit -m "Initial commit"
    ```
    
3.  Link the repository:
    
    ```
    git remote add origin https://github.com/yourusername/example.git
    ```
    
4.  Push the changes:
    
    ```
    git push -u origin main
    ```
    

**Etter’s Principle:** The act of maintaining documentation within a forge allows instant availability to all team members and ensures visibility alongside protection against accidental data loss.

### Step 6: Configure GitHub Pages

1.  Generate the final build:
    
    ```
    pelican content -s publishconf.py
    ```
    
2.  Deploy the site:
    
    ```
    ghp-import output -b gh-pages
    ```
    
3.  Push to GitHub:
    
    ```
    git push origin gh-pages
    ```
    
4.  Go to **GitHub Repository > Settings > Pages** and ensure the branch is set to `gh-pages`
    
5.  Wait a few minutes and visit `https://yourgithubusername.github.io/example` to see your site live
    

## Additional Resources

-   [Markdown Tutorial](https://www.markdownguide.org/basic-syntax/)
    
-   [Pelican Documentation](https://opensource.com/article/19/1/getting-started-pelican)
    
-   [GitHub Repositories Guide](https://docs.github.com/en/repositories/creating-and-managing-repositories/quickstart-for-repositories)
    
-   [Git Initialization](https://github.com/git-guides/git-init)
    
-   [GitHub Pages Documentation](https://pages.github.com/)
    

## FAQ


**Q:** Why use Markdown instead of Word?

**A:** Markdown functions as an easy-to-read lightweight text format which operates smoothly with Git version control frameworks.  Since it prevents proprietary formatting problems Markdown proves suitable for collaborative work and technical documentation and long-term document support.  The benefit of markdown as a markup language lies in its ability to enable fast document editing along with change tracking features that automatically operate with static site generators to strengthen modern documentation methods.

**Q:** Why isn’t my site loading on GitHub?

**A:** There are several possible reasons your site may not be loading:

1.  **Incorrect** `SITEURL`  – Ensure that your `SITEURL` is set correctly in `publishconf.py`. It should match your GitHub Pages URL (e.g., `https://yourgithubusername.github.io/example`).
    
2.  **Pending Changes Not Pushed** – Check if you have uncommitted or unpushed changes by running:
    
    ```
    git status
    ```
    
    If there are changes, commit and push them using:
    
    ```
    git add .
    git commit -m "Updated site files"
    git push origin gh-pages
    ```
    
3.  **GitHub Pages Not Enabled** – Verify that GitHub Pages is enabled for your repository:
    
    -   Go to **Settings** in your repository.
        
    -   Scroll to **GitHub Pages** and ensure the correct branch (`gh-pages`) is selected.
        
4.  **Caching Issues** – Sometimes, browsers cache old versions of your site. Try clearing your cache or opening the site in an incognito/private browsing window.
    
5.  **Deployment Delay** – GitHub Pages may take a few minutes to update. Wait a bit and refresh your page.
    
If the issue persists, review your repository's **Actions** tab for any build errors or check the **GitHub Pages documentation** for troubleshooting tips.

## Credits

**Peer Reviewers:** Karson Perche, Krupal Patel

**Acknowledgments:** Thanks to Andrew Etter for insights from _Modern Technical Writing_ and William S. Pfeiffer for instruction guidelines.

 